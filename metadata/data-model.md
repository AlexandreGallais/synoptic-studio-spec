# Data model

> [Home](../README.md) › [Metadata](README.md) › Data model

Status: schema only, being written (2026-11-19). The descriptions come once the schema is validated by the Product Owner.

- `internal_id`: the UUID set by the software; every FK holds one.
- `id`: the public identifier, written by the user.
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
        uuid difference_of FK
        uuid model_unit FK
        quantity_kind kind "quantity or difference"
        text id
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
    QUANTITY |o--o| QUANTITY : "difference of"
    QUANTITY }o--|| UNIT : "model unit"
```

## Not in the schema yet

- The texts filled on each placed symbol: with the synoptic.
- The versions of Metadata.
- How a unit converts (against a reference family or a base unit).

## Open

- The name of the short text that names a colour or an icon: `description` for now.
- The names of the nested parts (`APPEARANCE`, `VALUE_TYPE`, `COMMAND_TARGET`, `DISPLAY`, `SIGNAL_FIELD`, `BOUND`, `COMMAND_BUTTON`, `TEXT_CONTENT`) and of `FACEPLATE_ELEMENT`: working names.
