# Data model

> [Home](../README.md) › [Metadata](README.md) › Data model

Status: schema only, being written (2026-11-19). The descriptions come once the schema is validated by the Product Owner.

- `internal_id`: the UUID set by the software; every FK holds one.
- `id`: the public identifier, written by the user. What the software ships (quantities, families, units) has a `name` instead: the user never writes it.
- A choice of the software (`kind`, `direction`, `measure`...) is written in the JSON as an English word (`"input"`, `"difference"`), never as a number, so that a file reads by itself (Product Owner, 2026-11-19). The key of an enum item stays a whole number: it goes to the model (decisions 0012, 0016).
- A box without `internal_id` is a part of its owner (a nested object in the JSON), never pointed to.
- `has`: one nested object; `holds`: an ordered list inside its owner.
- Field order in each box: `internal_id`, then the links (FK), then the kind, then `id` or the name, then the values, then the texts.

## The schema

```mermaid
erDiagram
    TYPE {
        uuid internal_id PK
        uuid parent FK
        text id
    }
    APPEARANCE {
        uuid icon FK
        uuid colour FK
    }
    DOCUMENTATION {
        markdown description
    }
    LINK {
        uuid internal_id PK
        link_kind kind "path or url"
        text target
        text description
    }
    SIGNAL {
        uuid internal_id PK
        direction direction "input or output"
        text id
    }
    VALUE_TYPE {
        uuid enum FK
        uuid quantity FK
        value_kind kind "integer, real, boolean or enum"
        measure measure "value or difference"
    }
    COMMAND {
        uuid internal_id PK
        command_kind kind "set a signal, trigger or override"
        text id
    }
    COMMAND_TARGET {
        uuid signal FK
        typed_value value
    }
    FLAG {
        uuid internal_id PK
        text id
        text description
    }
    PRESET {
        uuid internal_id PK
        text name
    }
    PRESET_VALUE {
        uuid signal FK
        typed_value default_value
    }
    DISPLAY {
        uuid unit FK
        integer decimals
    }
    FACEPLATE_ELEMENT {
        uuid internal_id PK
        element_kind kind "signal, command, title, description or group"
    }
    SIGNAL_FIELD {
        uuid signal FK
        access access "read, write or override"
        input_kind input
        text name_shown
    }
    BOUND {
        uuid signal FK
        real value
    }
    COMMAND_BUTTON {
        uuid command FK
        text button_text
    }
    TEXT_CONTENT {
        uuid identifier FK
        uuid signal FK
        text text
    }
    ENUM {
        uuid internal_id PK
        enum_kind kind "global or template"
        text id
        text description
    }
    ENUM_ITEM {
        uuid internal_id PK
        integer key
        text display_text
        text description
    }
    IDENTIFIER {
        uuid internal_id PK
        text id
        text display_name
        text description
    }
    QUANTITY {
        uuid internal_id PK
        uuid default_unit FK
        text name
        boolean offers_difference
        integer default_decimals
    }
    FAMILY {
        uuid internal_id PK
        text name
    }
    UNIT {
        uuid internal_id PK
        text name
        text symbol
    }
    CONVERSION {
        expression from_default "this unit from x, in the default unit"
        expression to_default "the default unit from x, in this unit"
    }
    ICON {
        uuid internal_id PK
        svg drawing
        text description
    }
    PALETTE {
        uuid internal_id PK
        text name
    }
    COLOUR {
        uuid internal_id PK
        rgb value
        text description "shown on hover"
    }
    TYPE |o--o{ TYPE : "parent of"
    TYPE ||--|| APPEARANCE : has
    TYPE ||--|| DOCUMENTATION : has
    DOCUMENTATION ||--o{ LINK : holds
    TYPE ||--o{ SIGNAL : holds
    TYPE ||--o{ COMMAND : holds
    TYPE ||--o{ FLAG : holds
    TYPE ||--o{ PRESET : holds
    APPEARANCE }o--o| ICON : shows
    APPEARANCE }o--o| COLOUR : shows
    PALETTE ||--|{ COLOUR : holds
    SIGNAL ||--|| VALUE_TYPE : has
    VALUE_TYPE }o--o| ENUM : "points to"
    VALUE_TYPE }o--o| QUANTITY : measures
    ENUM ||--o{ ENUM_ITEM : holds
    COMMAND ||--o| COMMAND_TARGET : has
    COMMAND_TARGET }o--|| SIGNAL : targets
    COMMAND_TARGET }o--o| ENUM_ITEM : sends
    PRESET ||--|{ PRESET_VALUE : holds
    PRESET_VALUE }o--|| SIGNAL : "value of"
    PRESET_VALUE ||--|| DISPLAY : has
    DISPLAY }o--o| UNIT : "shown in"
    PRESET_VALUE }o--o| ENUM_ITEM : "default item"
    PRESET ||--o{ FACEPLATE_ELEMENT : holds
    FACEPLATE_ELEMENT |o--o{ FACEPLATE_ELEMENT : "a group holds"
    FACEPLATE_ELEMENT ||--o| SIGNAL_FIELD : has
    FACEPLATE_ELEMENT ||--o| COMMAND_BUTTON : has
    FACEPLATE_ELEMENT ||--o| TEXT_CONTENT : has
    SIGNAL_FIELD }o--|| SIGNAL : shows
    SIGNAL_FIELD ||--o| BOUND : min
    SIGNAL_FIELD ||--o| BOUND : max
    BOUND }o--o| SIGNAL : "taken from"
    COMMAND_BUTTON }o--|| COMMAND : "button of"
    TEXT_CONTENT }o--o| IDENTIFIER : "text from"
    TEXT_CONTENT }o--o| SIGNAL : "text from"
    QUANTITY ||--|{ FAMILY : holds
    FAMILY ||--|{ UNIT : holds
    QUANTITY }o--|| UNIT : "default unit"
    UNIT ||--o| CONVERSION : "of a value"
    UNIT ||--o| CONVERSION : "of a difference"
```

## Changed on 2026-11-19

Asked by the Product Owner on 2026-11-19, while reading the schema; the three points the assistant proposed were settled by the Product Owner the same day, in the questionnaire. Decision 0049 (accepted, 2026-11-19) records them: it changes decision 0003 (reference family, closed forms) and specifies decision 0020 (a difference).

- **The default unit** replaces `model_unit` (Product Owner: "c'est plutôt la unit par défaut"): the unit of the quantity that every conversion is written against, as the Units page already calls it. Its own conversion is empty: it is the unit itself.
- **No reference family any more**: every unit converts to the default unit and back, never to another family. It answers the question of 2026-11-17 the way the assistant proposed then; the families only group the units for reading.
- **A conversion is the real formula** (Product Owner: "que la conversion on puisse mettre le calcul réel"), not only a factor: two expressions in `x`, one from the default unit, one back to it, because a free formula cannot be turned round by the software. Confirmed by the Product Owner on 2026-11-19 ("Oui, formules libres"). It replaces the rule of 2026-11-11 (decision 0003) by which a conversion was one of four closed forms, a pair of free expressions being the last resort. The four forms of the research (proportional, affine, inverse, logarithmic) are now just formulas like any other. The catalogue is written by contributors, so its tests check that each pair goes there and back.
- **A quantity has a `name`, not an `id`** (Product Owner: "c'est pas vraiment ce que j'appellerai un ID, c'est plutôt un nom"): mass, volume, flow are shipped by the software, never typed by the user.
- **A difference is no longer a quantity of its own** (assistant's proposal, chosen by the Product Owner on 2026-11-19: "une lecture de la grandeur"; no table of its own): the signal says whether its value is the quantity or a difference of it (`measure`, as decision 0020 already says), and the units of a quantity whose conversion changes (`offers_difference`, temperature, gauge pressure...) carry a second conversion, for a difference. It removes the quantity that points to another quantity (`difference_of`, `kind`), which read badly. It is what FMI does with its flag `relativeQuantity` (research T2, section 3.8).
- **`integer` stays a value kind** beside `real`, `boolean` and `enum` (Product Owner, 2026-11-19: "Garder integer"), as decisions 0003 and 0043 already say: the model receives an exact whole number, and the input refuses decimals. FMI and SSP keep integers apart from reals (research T2, section 3.1).

## Not in the schema yet

- The texts filled on each placed symbol: with the synoptic.
- The versions of Metadata.

## Open

- The default unit is also the model unit while the model unit stays in the catalogue (decision 0024 leans that way). If it moves to a configuration of the project, the default unit stays the unit the formulas are written against, and the model unit becomes a field of its own.
- The symbol of a unit for a difference: the same (`°C`) or marked (`Δ°C`)?
- The syntax of the expressions (operators, π, powers, logarithms): chosen with the architecture, evaluated without `eval`.
- The name of the short text that names a colour or an icon: `description` for now.
- The names of the nested parts (`APPEARANCE`, `VALUE_TYPE`, `COMMAND_TARGET`, `DISPLAY`, `SIGNAL_FIELD`, `BOUND`, `COMMAND_BUTTON`, `TEXT_CONTENT`, `CONVERSION`) and of `FACEPLATE_ELEMENT`: working names.
