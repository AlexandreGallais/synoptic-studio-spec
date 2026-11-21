# Data model

> [Home](../README.md) › [Metadata](README.md) › Data model

Status: the schema and its JSON, being validated with the Product Owner. The rules, the reading notes and the open questions are in [Data model: notes](data-model-notes.md).

Colours of the boxes: orange, the object has its own page in [Objects](objects/README.md), not validated yet; green, its page is validated by the Product Owner; no colour, not written yet.

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
        text description
    }
    VALUE_TYPE {
        value_type_kind kind "integer, real, boolean or enum"
        uuid enum FK "when kind is enum"
        uuid quantity FK "when kind is integer or real"
        boolean relative_quantity "when kind is integer or real: true when the value is a difference"
    }
    COMMAND {
        uuid internal_id PK
        command_kind kind "set_signal, trigger or override"
        text id
        text description
    }
    COMMAND_TARGET {
        uuid signal FK "an input for set_signal, an output for override"
        signal_value value "a number in the default unit, a boolean, or the internal_id of an item of the signal's enum"
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
        signal_value default_value "a number in the default unit, a boolean, or the internal_id of an item of the signal's enum"
    }
    DISPLAY_FORMAT {
        uuid unit FK "the display unit: a unit of the signal's quantity"
        integer decimals
    }
    BOOLEAN_TEXTS {
        text true_text "shown when the value is true"
        text false_text "shown when the value is false"
    }
    FACEPLATE_ELEMENT {
        uuid internal_id PK
        faceplate_element_kind kind "signal, command, title, description or group"
    }
    SIGNAL_FIELD {
        uuid signal FK
        access access "read; write for an input; override for an output"
        input_kind input_kind "when access is write or override: number_field for a number; radio_one_line, radio_several_lines or select for an enum; switch for a boolean"
        text display_name "empty: the signal's id is shown"
    }
    BOUND {
        bound_source source "typed or signal"
        uuid signal FK "when source is signal: an input of the same quantity, its value is the bound"
        real typed_value "when source is typed, in the default unit of the quantity of the signal shown"
    }
    COMMAND_BUTTON {
        uuid command FK
        text display_name "empty: the command's id is shown"
    }
    TEXT_CONTENT {
        text_content_source source "typed or identifier"
        uuid identifier FK "when source is identifier: its text on each placed symbol"
        text typed_text "when source is typed"
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
        text display_name "empty: the key is shown"
        text description
    }
    IDENTIFIER {
        uuid internal_id PK
        text id
        text display_name "empty: the id is shown"
        text description
    }
    QUANTITY {
        uuid internal_id PK
        uuid default_unit FK "one of its units"
        text name
        boolean offers_relative_quantity "a signal of it may have relative_quantity true"
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
        text name "shown on hover"
        svg drawing
    }
    PALETTE {
        uuid internal_id PK
        text name
    }
    COLOUR {
        uuid internal_id PK
        text name "shown on hover"
        rgb value
    }
    TYPE |o--o{ TYPE : "parent"
    TYPE ||--|| APPEARANCE : "has"
    TYPE ||--|| DOCUMENTATION : "has"
    DOCUMENTATION ||--o{ LINK : "holds"
    TYPE ||--o{ SIGNAL : "holds"
    TYPE ||--o{ COMMAND : "holds"
    TYPE ||--o{ FLAG : "holds"
    TYPE ||--o{ PRESET : "holds"
    APPEARANCE }o--o| ICON : "icon"
    APPEARANCE }o--o| COLOUR : "colour"
    PALETTE ||--|{ COLOUR : "holds"
    SIGNAL ||--|| VALUE_TYPE : "has"
    VALUE_TYPE }o--o| ENUM : "enum, when kind is enum"
    VALUE_TYPE }o--o| QUANTITY : "quantity, when kind is integer or real"
    ENUM ||--o{ ENUM_ITEM : "holds"
    COMMAND ||--o| COMMAND_TARGET : "has, when kind is set_signal or override"
    COMMAND_TARGET }o--|| SIGNAL : "signal"
    COMMAND_TARGET }o--o| ENUM_ITEM : "value, when the signal is an enum"
    PRESET ||--o{ PRESET_VALUE : "holds, one per signal of the type"
    PRESET_VALUE }o--|| SIGNAL : "signal"
    PRESET_VALUE }o--o| ENUM_ITEM : "default_value, when the signal is an enum"
    PRESET_VALUE ||--o| DISPLAY_FORMAT : "has, when the signal is an integer or a real"
    DISPLAY_FORMAT }o--|| UNIT : "unit"
    PRESET_VALUE ||--o| BOOLEAN_TEXTS : "has, when the signal is a boolean"
    PRESET ||--o{ FACEPLATE_ELEMENT : "holds"
    FACEPLATE_ELEMENT |o--o{ FACEPLATE_ELEMENT : "holds, when kind is group"
    FACEPLATE_ELEMENT ||--o| SIGNAL_FIELD : "has, when kind is signal"
    FACEPLATE_ELEMENT ||--o| COMMAND_BUTTON : "has, when kind is command"
    FACEPLATE_ELEMENT ||--o| TEXT_CONTENT : "has, when kind is title or description"
    SIGNAL_FIELD }o--|| SIGNAL : "signal"
    SIGNAL_FIELD ||--o| RANGE : "has, when input_kind is number_field"
    RANGE ||--o| BOUND : "has, as min"
    RANGE ||--o| BOUND : "has, as max"
    BOUND }o--o| SIGNAL : "signal, when source is signal: an input of the same quantity"
    COMMAND_BUTTON }o--|| COMMAND : "command"
    TEXT_CONTENT }o--o| IDENTIFIER : "identifier, when source is identifier"
    QUANTITY ||--|{ FAMILY : "holds"
    FAMILY ||--|{ UNIT : "holds, sorted by size"
    QUANTITY }o--|| UNIT : "default_unit"
    UNIT ||--o| CONVERSION : "has, except the default unit"
    style IDENTIFIER fill:#f8b26a,stroke:#c66a00
```

## The schema as JSON

### A type

```json
{
  "format": 1,
  "internal_id": "6f1c2a90-0000-4000-8000-000000000001",
  "parent": "6f1c2a90-0000-4000-8000-000000000000",
  "id": "centrifugal_pump",
  "appearance": {
    "icon": "6f1c2a90-0000-4000-8000-000000000700",
    "colour": null
  },
  "documentation": {
    "description": "A **centrifugal** pump, driven by a variable speed motor.",
    "links": [
      {
        "internal_id": "6f1c2a90-0000-4000-8000-000000000010",
        "kind": "url",
        "target": "https://example.com/datasheets/centrifugal-pump",
        "description": "Datasheet"
      }
    ]
  },
  "signals": [
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000020",
      "direction": "input",
      "id": "speed_setpoint",
      "description": "Speed asked of the motor.",
      "value_type": {
        "kind": "real",
        "quantity": "6f1c2a90-0000-4000-8000-000000000900",
        "relative_quantity": false
      }
    },
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000021",
      "direction": "input",
      "id": "speed_max",
      "description": "Highest speed the operator may ask for.",
      "value_type": {
        "kind": "real",
        "quantity": "6f1c2a90-0000-4000-8000-000000000900",
        "relative_quantity": false
      }
    },
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000022",
      "direction": "output",
      "id": "speed",
      "description": "Speed of the motor, computed by the model.",
      "value_type": {
        "kind": "real",
        "quantity": "6f1c2a90-0000-4000-8000-000000000900",
        "relative_quantity": false
      }
    },
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000023",
      "direction": "output",
      "id": "running",
      "description": "True while the pump turns.",
      "value_type": {
        "kind": "boolean"
      }
    },
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000024",
      "direction": "input",
      "id": "mode",
      "description": "How the pump is driven.",
      "value_type": {
        "kind": "enum",
        "enum": "6f1c2a90-0000-4000-8000-000000000500"
      }
    },
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000025",
      "direction": "output",
      "id": "bearing_temperature_rise",
      "description": "How much the bearing is warmer than the room.",
      "value_type": {
        "kind": "real",
        "quantity": "6f1c2a90-0000-4000-8000-000000000910",
        "relative_quantity": true
      }
    }
  ],
  "commands": [
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000030",
      "kind": "trigger",
      "id": "start",
      "description": "Asks the model to start the pump."
    },
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000031",
      "kind": "set_signal",
      "id": "switch_to_auto",
      "description": "Puts the pump in automatic mode.",
      "command_target": {
        "signal": "6f1c2a90-0000-4000-8000-000000000024",
        "value": "6f1c2a90-0000-4000-8000-000000000502"
      }
    },
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000032",
      "kind": "override",
      "id": "force_speed",
      "description": "Replaces the speed computed by the model, for a test.",
      "command_target": {
        "signal": "6f1c2a90-0000-4000-8000-000000000022",
        "value": 151.8436
      }
    }
  ],
  "flags": [
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000040",
      "id": "under_maintenance",
      "description": "The pump is out of service for maintenance."
    }
  ],
  "presets": [
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000050",
      "name": "Standard",
      "preset_values": [
        {
          "signal": "6f1c2a90-0000-4000-8000-000000000020",
          "default_value": 0,
          "display_format": {
            "unit": "6f1c2a90-0000-4000-8000-000000000902",
            "decimals": 0
          }
        },
        {
          "signal": "6f1c2a90-0000-4000-8000-000000000021",
          "default_value": 157.0796,
          "display_format": {
            "unit": "6f1c2a90-0000-4000-8000-000000000902",
            "decimals": 0
          }
        },
        {
          "signal": "6f1c2a90-0000-4000-8000-000000000022",
          "default_value": 0,
          "display_format": {
            "unit": "6f1c2a90-0000-4000-8000-000000000902",
            "decimals": 1
          }
        },
        {
          "signal": "6f1c2a90-0000-4000-8000-000000000023",
          "default_value": false,
          "boolean_texts": {
            "true_text": "Running",
            "false_text": "Stopped"
          }
        },
        {
          "signal": "6f1c2a90-0000-4000-8000-000000000024",
          "default_value": "6f1c2a90-0000-4000-8000-000000000501"
        },
        {
          "signal": "6f1c2a90-0000-4000-8000-000000000025",
          "default_value": 0,
          "display_format": {
            "unit": "6f1c2a90-0000-4000-8000-000000000912",
            "decimals": 1
          }
        }
      ],
      "faceplate_elements": [
        {
          "internal_id": "6f1c2a90-0000-4000-8000-000000000060",
          "kind": "title",
          "text_content": {
            "source": "identifier",
            "identifier": "6f1c2a90-0000-4000-8000-000000000800"
          }
        },
        {
          "internal_id": "6f1c2a90-0000-4000-8000-000000000061",
          "kind": "description",
          "text_content": {
            "source": "typed",
            "typed_text": "Feed pump of the main loop."
          }
        },
        {
          "internal_id": "6f1c2a90-0000-4000-8000-000000000062",
          "kind": "group",
          "faceplate_elements": [
            {
              "internal_id": "6f1c2a90-0000-4000-8000-000000000063",
              "kind": "signal",
              "signal_field": {
                "signal": "6f1c2a90-0000-4000-8000-000000000020",
                "access": "write",
                "input_kind": "number_field",
                "display_name": "Speed setpoint",
                "range": {
                  "min": {
                    "source": "typed",
                    "typed_value": 0
                  },
                  "max": {
                    "source": "signal",
                    "signal": "6f1c2a90-0000-4000-8000-000000000021"
                  }
                }
              }
            },
            {
              "internal_id": "6f1c2a90-0000-4000-8000-000000000064",
              "kind": "signal",
              "signal_field": {
                "signal": "6f1c2a90-0000-4000-8000-000000000022",
                "access": "read",
                "display_name": null
              }
            },
            {
              "internal_id": "6f1c2a90-0000-4000-8000-000000000065",
              "kind": "signal",
              "signal_field": {
                "signal": "6f1c2a90-0000-4000-8000-000000000023",
                "access": "read",
                "display_name": "State"
              }
            }
          ]
        },
        {
          "internal_id": "6f1c2a90-0000-4000-8000-000000000066",
          "kind": "signal",
          "signal_field": {
            "signal": "6f1c2a90-0000-4000-8000-000000000024",
            "access": "write",
            "input_kind": "radio_one_line",
            "display_name": "Mode"
          }
        },
        {
          "internal_id": "6f1c2a90-0000-4000-8000-000000000067",
          "kind": "command",
          "command_button": {
            "command": "6f1c2a90-0000-4000-8000-000000000030",
            "display_name": "Start"
          }
        }
      ]
    }
  ]
}
```

### A global enum

```json
{
  "format": 1,
  "internal_id": "6f1c2a90-0000-4000-8000-000000000500",
  "kind": "global",
  "id": "operating_mode",
  "description": "How a piece of equipment is driven.",
  "enum_items": [
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000501",
      "key": 0,
      "display_name": "Manual",
      "description": "Driven by the operator."
    },
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000502",
      "key": 1,
      "display_name": "Auto",
      "description": "Driven by the control loop."
    }
  ]
}
```

### A quantity of the catalogue

```json
{
  "internal_id": "6f1c2a90-0000-4000-8000-000000000910",
  "default_unit": "6f1c2a90-0000-4000-8000-000000000911",
  "name": "temperature",
  "offers_relative_quantity": true,
  "families": [
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000915",
      "name": "metric",
      "units": [
        {
          "internal_id": "6f1c2a90-0000-4000-8000-000000000911",
          "name": "kelvin",
          "symbol": "K"
        },
        {
          "internal_id": "6f1c2a90-0000-4000-8000-000000000912",
          "name": "degree Celsius",
          "symbol": "°C",
          "conversion": {
            "to_default": "x + 273.15",
            "from_default": "x - 273.15"
          }
        }
      ]
    },
    {
      "internal_id": "6f1c2a90-0000-4000-8000-000000000916",
      "name": "imperial",
      "units": [
        {
          "internal_id": "6f1c2a90-0000-4000-8000-000000000913",
          "name": "degree Fahrenheit",
          "symbol": "°F",
          "conversion": {
            "to_default": "(x + 459.67) * 5 / 9",
            "from_default": "x * 9 / 5 - 459.67"
          }
        }
      ]
    }
  ]
}
```
