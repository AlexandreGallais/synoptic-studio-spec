# Data model

> [Home](../README.md) › [Metadata](README.md) › Data model

Status: final page, being written (2026-11-19). The schema only, to be validated by the Product Owner before the rest of the page. Written from the [whole draft](draft.md); the presets part is drawn from the [Presets](draft.md#presets-and-their-faceplate) page, never described as data before.

## How to read the schema

- Every object has an `internal_id` (PK): a UUID set by the software, that never changes and never leaves the application.
- A field marked FK holds the `internal_id` of the object it points to, never its `id` nor a copy.
- `id` is the public identifier, written by the user and sent to the model and the configuration files.
- A "holds" line is a nested, ordered list: the order of the list is the order on the screen.
- `null` in a comment says what an empty field means.
- `quantity`, `family`, `unit`, `icon`, `palette` and `colour` ship with the software: the user only points to them.

## The schema

```mermaid
erDiagram
    TYPE {
        uuid internal_id PK
        text id "unique in the whole tree"
        uuid parent FK "null: a root type"
        uuid icon FK "null: follows the parent"
        uuid colour FK "null: follows the parent"
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
        value_type type "integer, real, boolean or enum"
        uuid enum FK "enum signals only"
        uuid quantity FK "a quantity or a difference; optional"
    }
    COMMAND {
        uuid internal_id PK
        command_kind kind "set a signal, trigger or override an output"
        text id
        uuid target FK "null: a trigger"
        typed_value value "number, boolean or enum item; null: a trigger"
    }
    FLAG {
        uuid internal_id PK
        text id
        text description "optional"
    }
    PRESET {
        uuid internal_id PK
        text name
    }
    PRESET_VALUE {
        uuid signal FK "one line per signal, own and inherited"
        uuid display_unit FK "null: the model unit"
        integer decimals "null: the default of the quantity"
        typed_value default_value "number, boolean or enum item"
    }
    ELEMENT {
        uuid internal_id PK
        element_kind kind "signal, command, title, description or group"
        uuid signal FK "signal element"
        text name_shown "signal element; null: its id"
        access access "signal element: read, write or override"
        input_kind input "signal element: number field, radio, select..."
        real min "number field: typed"
        uuid min_signal FK "number field: or taken from a signal"
        real max "number field: typed"
        uuid max_signal FK "number field: or taken from a signal"
        uuid command FK "command element"
        text button_text "command element"
        text text "title or description: a fixed text"
        uuid text_identifier FK "title or description: or an identifier"
        uuid text_signal FK "title or description: or a signal"
    }
    ENUM {
        uuid internal_id PK
        text id
        enum_kind kind "global or template"
        text description
    }
    ENUM_ITEM {
        uuid internal_id PK
        integer key "unique in the enum, sent to the model"
        text display_text
        text description "optional"
    }
    IDENTIFIER {
        uuid internal_id PK
        text id
        text display_name
        text description "optional"
    }
    QUANTITY {
        uuid internal_id PK
        text id
        quantity_kind kind "quantity or difference"
        uuid difference_of FK "difference only"
        uuid model_unit FK
        integer default_decimals
    }
    FAMILY {
        uuid internal_id PK
        text name "Metric, Imperial..."
    }
    UNIT {
        uuid internal_id PK
        text name
        text symbol
        conversion conversion "going and back"
    }
    ICON {
        uuid internal_id PK
        svg drawing
    }
    PALETTE {
        uuid internal_id PK
    }
    COLOUR {
        uuid internal_id PK
        rgb value
    }
    TYPE |o--o{ TYPE : "parent of"
    TYPE ||--o{ LINK : holds
    TYPE ||--o{ SIGNAL : holds
    TYPE ||--o{ COMMAND : holds
    TYPE ||--o{ FLAG : holds
    TYPE ||--o{ PRESET : holds
    TYPE }o--o| ICON : shows
    TYPE }o--o| COLOUR : shows
    PALETTE ||--|{ COLOUR : holds
    SIGNAL }o--o| ENUM : "points to"
    SIGNAL }o--o| QUANTITY : measures
    ENUM ||--o{ ENUM_ITEM : holds
    COMMAND }o--o| SIGNAL : targets
    COMMAND }o--o| ENUM_ITEM : sends
    PRESET ||--|{ PRESET_VALUE : holds
    PRESET_VALUE }o--|| SIGNAL : "value of"
    PRESET_VALUE }o--o| UNIT : "shown in"
    PRESET_VALUE }o--o| ENUM_ITEM : "default item"
    PRESET ||--o{ ELEMENT : holds
    ELEMENT |o--o{ ELEMENT : "a group holds"
    ELEMENT }o--o| SIGNAL : shows
    ELEMENT }o--o| COMMAND : "button of"
    ELEMENT }o--o| IDENTIFIER : "text from"
    QUANTITY ||--|{ FAMILY : holds
    FAMILY ||--|{ UNIT : holds
    QUANTITY |o--o| QUANTITY : "difference of"
    QUANTITY }o--|| UNIT : "model unit"
```

## Not in the schema yet

- The texts filled on each placed symbol (identifiers, items of a template enum, flags on or off): with the synoptic, part 3.
- The versions of Metadata: their questions are open (see [Versions](draft.md#versions-of-metadata)).
- The conversion of a unit: against a reference family or a base unit, still open (see [Units](draft.md#quantities-families-and-conversions)).
