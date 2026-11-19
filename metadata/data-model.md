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
        uuid enum FK "enum only"
        value_kind kind "integer, real, boolean or enum"
    }
    MEASUREMENT {
        uuid quantity FK
        measure measure "value or difference"
    }
    COMMAND {
        uuid internal_id PK
        command_kind kind "set a signal, trigger or override"
        text id
    }
    COMMAND_TARGET {
        uuid signal FK
        typed_value value "a number, a boolean, or the internal_id of an enum item"
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
        typed_value default_value "a number, a boolean, or the internal_id of an enum item"
    }
    DISPLAY {
        uuid unit FK "only when the signal has a quantity"
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
        uuid signal FK "signal only"
        bound_source source "typed or signal"
        real value "typed only"
    }
    COMMAND_BUTTON {
        uuid command FK
        text button_text
    }
    TEXT_CONTENT {
        uuid identifier FK "identifier only"
        uuid signal FK "signal only"
        text_source source "fixed, identifier or signal"
        text text "fixed only"
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
        boolean offers_difference "a signal of it may hold a difference"
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
        expression to_default "x in this unit gives the default unit"
        expression from_default "x in the default unit gives this unit"
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
    VALUE_TYPE ||--o| MEASUREMENT : "has, integer or real only"
    MEASUREMENT }o--|| QUANTITY : measures
    ENUM ||--o{ ENUM_ITEM : holds
    COMMAND ||--o| COMMAND_TARGET : has
    COMMAND_TARGET }o--|| SIGNAL : targets
    COMMAND_TARGET }o--o| ENUM_ITEM : sends
    PRESET ||--|{ PRESET_VALUE : holds
    PRESET_VALUE }o--|| SIGNAL : "value of"
    PRESET_VALUE ||--o| DISPLAY : "has, integer or real only"
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
    FAMILY ||--|{ UNIT : "holds, sorted by size"
    QUANTITY }o--|| UNIT : "default unit"
    UNIT ||--o| CONVERSION : has
```

## Changed on 2026-11-19

Asked by the Product Owner on 2026-11-19, while reading the schema; the three points the assistant proposed were settled by the Product Owner the same day, in the questionnaire. Decision 0049 (accepted, 2026-11-19) records them: it changes decision 0003 (reference family, closed forms) and specifies decision 0020 (a difference).

- **The default unit** replaces `model_unit` (Product Owner: "c'est plutôt la unit par défaut"): the unit of the quantity that every conversion is written against, as the Units page already calls it. Its own conversion is empty: it is the unit itself.
- **No reference family any more**: every unit converts to the default unit and back, never to another family. It answers the question of 2026-11-17 the way the assistant proposed then; the families only group the units for reading.
- **A conversion is the real formula** (Product Owner: "que la conversion on puisse mettre le calcul réel"), not only a factor: two expressions in `x`, one from the default unit, one back to it, because a free formula cannot be turned round by the software. Confirmed by the Product Owner on 2026-11-19 ("Oui, formules libres"). It replaces the rule of 2026-11-11 (decision 0003) by which a conversion was one of four closed forms, a pair of free expressions being the last resort. The four forms of the research (proportional, affine, inverse, logarithmic) are now just formulas like any other. The catalogue is written by contributors, so its tests check that each pair goes there and back.
- **A quantity has a `name`, not an `id`** (Product Owner: "c'est pas vraiment ce que j'appellerai un ID, c'est plutôt un nom"): mass, volume, flow are shipped by the software, never typed by the user.
- **A difference is no longer a quantity of its own** (assistant's proposal, chosen by the Product Owner on 2026-11-19: "une lecture de la grandeur"; no table of its own): the signal says whether its value is the quantity or a difference of it (`measure`, as decision 0020 already says), and the units of a quantity whose conversion changes (`offers_difference`, temperature, gauge pressure...) carry a second conversion, for a difference (computed by the software since the evening, see below). It removes the quantity that points to another quantity (`difference_of`, `kind`), which read badly. It is what FMI does with its flag `relativeQuantity` (research T2, section 3.8).
- **`integer` stays a value kind** beside `real`, `boolean` and `enum` (Product Owner, 2026-11-19: "Garder integer"), as decisions 0003 and 0043 already say: the model receives an exact whole number, and the input refuses decimals. FMI and SSP keep integers apart from reals (research T2, section 3.1).

## Read again on 2026-11-19 (afternoon)

The Product Owner read the quantity part again and found it right (`measure`: "ça, c'est vraiment bien"; families: metric or imperial "c'est juste ça"; units: name and symbol).

- **The units of a family are sorted by the software, never by hand** (Product Owner: "Oui, go faire ça. C'est plus simple comme ça"): smallest first, by the size of one step in the default unit, `to_default(1) − to_default(0)`; equal sizes by name. The catalogue writes them in any order. A quantity whose formulas give no finite step (an inverse such as l/100 km, a logarithm such as dB) keeps the order the catalogue writes.
- **The two expressions of a conversion are named by where `x` goes**: `to_default` takes `x` in this unit and gives the default unit; `from_default` takes `x` in the default unit and gives this unit. The labels of the schema said it the wrong way round.
- **What a difference is, said for the Product Owner** (the assistant's explanation, not a new rule): a value is a point on the scale ("it is 20 °C"), a difference is a gap between two points ("it rose by 20 °C"). Most conversions only multiply (litres to decalitres, kilograms to pounds): a value and a difference then convert the same way, so a quantity like volume needs nothing more. A conversion that also shifts the zero (°C to °F: `x × 9/5 + 32`; gauge to absolute pressure) converts them differently: 20 °C is 68 °F, but a rise of 20 °C is a rise of 36 °F, because the `+ 32` cancels out in a gap. `offers_difference` marks these quantities, as decision 0020 says.
- **`default_decimals` is for the screen, never for the model**: the model always gets the full value; the decimals only round what is shown. Removed the same day (see below).

## Settled on 2026-11-19 (evening)

The Product Owner answered the two questions of the afternoon in the questionnaire. Decision 0050 (accepted, 2026-11-19) records them: it changes decisions 0049 (a second conversion for a difference) and 0020 (default decimals in the catalogue).

- **A difference is converted by the software, never written in the catalogue** (Product Owner: "si tout peut être calculé, « logiquement », ben go"; with no exception, else everything by hand): the difference of `x` in the default unit is `to_default(x) − to_default(0)`, and back `from_default(x) − from_default(0)`. A unit has one conversion only; the conversion "of a difference" is gone.
  - Why there is no exception: this computation is exact for every conversion that multiplies then shifts (°C, °F, K, gauge or absolute pressure), and these are the only quantities that offer a difference. A conversion that only multiplies needs no difference at all. A conversion that is not a straight line (an inverse such as l/100 km, a logarithm such as dB) has no difference that converts on its own, and such a quantity never offers one.
  - Hence one rule of the catalogue, checked by its tests: a quantity with `offers_difference` has only conversions that multiply then shift (`to_default(x) − to_default(0)` proportional to `x`).
- **No `default_decimals` on the quantity** (Product Owner: "les décimales à montrer, c'est vraiment selon les presets [...] il faut l'enlever de l'objet quantité"): the decimals shown are set in the presets only, which start from one default number of decimals, the same everywhere. The assistant agrees: the right number of decimals depends on the unit shown, not on the quantity (2 decimals show 10 g in kilograms, but 0.01 g in grams), so a default per quantity would be wrong as soon as a preset shows another unit.

## Read again on 2026-11-19 (enums)

The Product Owner read the enums and found them right (enum: kind, `id`, description, "faut pas plus"; item: key, display text, description, and its place in the list). The Product Owner then asked why `VALUE_TYPE` holds `measure` beside `enum`, when a signal does not always have a quantity. The question was right: `measure` only means something when there is a quantity, and the box did not say it. The fix is a rule for the whole schema, not only for this box (assistant's proposal, asked by the Product Owner: "corriger tous les endroits où il y aura des problèmes comme ça").

- **Fields that only exist together go in a part of their own.** The quantity and `measure` move to `MEASUREMENT`, which a value type has for an integer or a real only. The enum stays a single field of `VALUE_TYPE`: it has nothing else that goes with it, so it needs no part.
- **A part that only exists for some signals says so on its link.** `DISPLAY` (unit and decimals) is there for an integer or a real only, never for a boolean or an enum; its unit only when the signal has a quantity.
- **A choice between alternatives says which one it is**, as `VALUE_TYPE.kind` does, instead of leaving the reader to guess from the field that is filled. `BOUND` gets `source` (typed or signal), `TEXT_CONTENT` gets `source` (fixed, identifier or signal); each other field says when it is filled.
- **A typed value says what it holds**: a number, a boolean, or the internal ID of an enum item (decision 0047), in `COMMAND_TARGET` and `PRESET_VALUE`.
- The screen of an enum showed "Name": it is the `id`, as the Product Owner said ("ça devrait être ID"), in `screens/metadata.md`, MD-09.3.

## Not in the schema yet

- The texts filled on each placed symbol: with the synoptic.
- The versions of Metadata.

## Open

- The default unit is also the model unit while the model unit stays in the catalogue (decision 0024 leans that way). If it moves to a configuration of the project, the default unit stays the unit the formulas are written against, and the model unit becomes a field of its own.
- The symbol of a unit for a difference: the same (`°C`) or marked (`Δ°C`)?
- The default number of decimals of a preset: 2 or 3 (Product Owner, 2026-11-19: "qui serait de 2 ou de 3"), and whether it is fixed by the software or set for the project.
- The syntax of the expressions (operators, π, powers, logarithms): chosen with the architecture, evaluated without `eval`.
- The name of the short text that names a colour or an icon: `description` for now.
- The names of the nested parts (`APPEARANCE`, `VALUE_TYPE`, `MEASUREMENT`, `COMMAND_TARGET`, `DISPLAY`, `SIGNAL_FIELD`, `BOUND`, `COMMAND_BUTTON`, `TEXT_CONTENT`, `CONVERSION`) and of `FACEPLATE_ELEMENT`: working names.
