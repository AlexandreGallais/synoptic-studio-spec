# Data model

> [Home](../README.md) › [Metadata](README.md) › Data model

Status: schema only, being written (2026-11-19). The descriptions come once the schema is validated by the Product Owner.

- `internal_id`: the UUID set by the software; every FK holds one.
- `id`: the public identifier, written by the user.
- `holds`: an ordered list inside its owner.

## The schema

```mermaid
erDiagram
    TYPE {
        uuid internal_id PK
        text id
        uuid parent FK
        uuid icon FK
        uuid colour FK
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
        uuid enum FK
        uuid quantity FK
    }
    COMMAND {
        uuid internal_id PK
        command_kind kind "set a signal, trigger or override"
        text id
        uuid target FK
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
        uuid display_unit FK
        integer decimals
        typed_value default_value
    }
    ELEMENT {
        uuid internal_id PK
        element_kind kind "signal, command, title, description or group"
        uuid signal FK
        text name_shown
        access access "read, write or override"
        input_kind input
        real min
        uuid min_signal FK
        real max
        uuid max_signal FK
        uuid command FK
        text button_text
        text text
        uuid text_identifier FK
        uuid text_signal FK
    }
    ENUM {
        uuid internal_id PK
        text id
        enum_kind kind "global or template"
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
        text id
        quantity_kind kind "quantity or difference"
        uuid difference_of FK
        uuid model_unit FK
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
        conversion conversion
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

- The texts filled on each placed symbol: with the synoptic.
- The versions of Metadata.
- How a unit converts (against a reference family or a base unit).

## Open

- The name of the short text that names a colour or an icon: `description` for now.
