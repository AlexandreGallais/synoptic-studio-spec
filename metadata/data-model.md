# Data model

> [Home](../README.md) › [Metadata](README.md) › Data model

Status: the schema and its JSON, being validated with the Product Owner. The rules, the reading notes and the open questions are in [Data model: notes](data-model-notes.md).

Colour of a box's title: orange, the entity has its own page in [Entities](entities/README.md), whose last version is not validated yet; green, the last version of its page is validated by the Product Owner; no colour, not written yet.

## The schema

```mermaid
---
config:
  themeCSS: "[id*='entity-DESIGNATION-'] .outer-path path, [id*='entity-PALETTE-'] .outer-path path, [id*='entity-COLOR-'] .outer-path path, [id*='entity-ENUM-'] .outer-path path, [id*='entity-ENUM_ITEM-'] .outer-path path, [id*='entity-ICON-'] .outer-path path, [id*='entity-ICON_SET-'] .outer-path path, [id*='entity-FLAG-'] .outer-path path, [id*='entity-LINK-'] .outer-path path, [id*='entity-DOCUMENTATION-'] .outer-path path, [id*='entity-QUANTITY-'] .outer-path path, [id*='entity-UNIT_SYSTEM-'] .outer-path path, [id*='entity-UNIT-'] .outer-path path, [id*='entity-CONVERSION-'] .outer-path path, [id*='entity-SIGNAL-'] .outer-path path, [id*='entity-VALUE_TYPE-'] .outer-path path, [id*='entity-COMMAND-'] .outer-path path, [id*='entity-COMMAND_TARGET-'] .outer-path path, [id*='entity-APPEARANCE-'] .outer-path path, [id*='entity-PRESET_VALUE-'] .outer-path path, [id*='entity-DISPLAY_FORMAT-'] .outer-path path, [id*='entity-BOOLEAN_TEXTS-'] .outer-path path, [id*='entity-BOUND-'] .outer-path path, [id*='entity-RANGE-'] .outer-path path, [id*='entity-SIGNAL_FIELD-'] .outer-path path, [id*='entity-COMMAND_BUTTON-'] .outer-path path, [id*='entity-TEXT_CONTENT-'] .outer-path path, [id*='entity-FACEPLATE_ELEMENT-'] .outer-path path, [id*='entity-PRESET-'] .outer-path path, [id*='entity-TYPE-'] .outer-path path { fill: #f8b26a !important; }"
---
erDiagram
    TYPE {
        uuid internal_id PK
        text id
        uuid parent FK
    }
    APPEARANCE {
        svg icon_drawing
        rgba color_value
    }
    DOCUMENTATION {
        markdown description
    }
    LINK {
        uuid internal_id PK
        link_kind kind
        text address
        text description
    }
    SIGNAL {
        uuid internal_id PK
        direction direction
        text id
        text description
    }
    VALUE_TYPE {
        value_type_kind kind
        uuid enum FK
        uuid quantity FK
        boolean relative_quantity
    }
    COMMAND {
        uuid internal_id PK
        command_kind kind
        text id
        text description
    }
    COMMAND_TARGET {
        uuid signal FK
        signal_value value
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
        signal_value start_value
    }
    DISPLAY_FORMAT {
        uuid unit FK
        integer decimals
    }
    BOOLEAN_TEXTS {
        text true_text
        text false_text
    }
    FACEPLATE_ELEMENT {
        uuid internal_id PK
        faceplate_element_kind kind
    }
    SIGNAL_FIELD {
        uuid signal FK
        access access
        input_kind input_kind
        text display_name
    }
    BOUND {
        bound_source source
        uuid signal FK
        real typed_value
    }
    COMMAND_BUTTON {
        uuid command FK
        text display_name
    }
    TEXT_CONTENT {
        text_content_source source
        uuid designation FK
        text typed_text
    }
    ENUM {
        uuid internal_id PK
        enum_kind kind
        text id
        text description
    }
    ENUM_ITEM {
        uuid internal_id PK
        integer key
        text display_name
        text description
    }
    DESIGNATION {
        uuid internal_id PK
        text id
        boolean required
        text description
    }
    QUANTITY {
        uuid internal_id PK
        text name
        uuid default_unit FK
        boolean offers_relative_quantity
    }
    UNIT_SYSTEM {
        uuid internal_id PK
        text name
    }
    UNIT {
        uuid internal_id PK
        text name
        text symbol
    }
    CONVERSION {
        expression to_default
        expression from_default
    }
    ICON_SET {
        uuid internal_id PK
        text name
    }
    ICON {
        uuid internal_id PK
        text name
        svg drawing
    }
    PALETTE {
        uuid internal_id PK
        text name
    }
    COLOR {
        uuid internal_id PK
        text name
        rgba value
    }
    TYPE |o--o{ TYPE : "parent"
    TYPE ||--|| APPEARANCE : "has"
    TYPE ||--|| DOCUMENTATION : "has"
    DOCUMENTATION ||--o{ LINK : "holds"
    TYPE ||--o{ SIGNAL : "holds"
    TYPE ||--o{ COMMAND : "holds"
    TYPE ||--o{ FLAG : "holds"
    TYPE ||--o{ PRESET : "holds"
    ICON_SET ||--|{ ICON : "holds"
    PALETTE ||--|{ COLOR : "holds"
    SIGNAL ||--|| VALUE_TYPE : "has"
    VALUE_TYPE }o--o| ENUM : "enum"
    VALUE_TYPE }o--o| QUANTITY : "quantity"
    ENUM ||--o{ ENUM_ITEM : "holds"
    COMMAND ||--o| COMMAND_TARGET : "has, when kind is set_input_signal or override_output_signal"
    COMMAND_TARGET }o--|| SIGNAL : "signal"
    COMMAND_TARGET }o--o| ENUM_ITEM : "value"
    PRESET ||--o{ PRESET_VALUE : "holds, one per signal of the type"
    PRESET_VALUE }o--|| SIGNAL : "signal"
    PRESET_VALUE }o--o| ENUM_ITEM : "start_value"
    PRESET_VALUE ||--o| DISPLAY_FORMAT : "has, when the signal is an integer or a real"
    DISPLAY_FORMAT }o--|| UNIT : "unit"
    PRESET_VALUE ||--o| BOOLEAN_TEXTS : "has, when the signal is a boolean"
    PRESET ||--o{ FACEPLATE_ELEMENT : "holds"
    FACEPLATE_ELEMENT |o--o{ FACEPLATE_ELEMENT : "holds, when kind is group"
    FACEPLATE_ELEMENT ||--o| SIGNAL_FIELD : "has, when kind is signal"
    FACEPLATE_ELEMENT ||--o| COMMAND_BUTTON : "has, when kind is command"
    FACEPLATE_ELEMENT ||--o| TEXT_CONTENT : "has, when kind is title or paragraph"
    SIGNAL_FIELD }o--|| SIGNAL : "signal"
    SIGNAL_FIELD ||--o| RANGE : "has, when input_kind is number_field"
    RANGE ||--o| BOUND : "has, as min"
    RANGE ||--o| BOUND : "has, as max"
    BOUND }o--o| SIGNAL : "signal"
    COMMAND_BUTTON }o--|| COMMAND : "command"
    TEXT_CONTENT }o--o| DESIGNATION : "designation"
    QUANTITY ||--|{ UNIT_SYSTEM : "holds"
    UNIT_SYSTEM ||--|{ UNIT : "holds, sorted by size"
    QUANTITY }o--|| UNIT : "default_unit"
    UNIT ||--o| CONVERSION : "has, except the default unit"
```

## The schema as JSON

### A type

```json
{
  "format_version": 1,
  "type": {
    "internal_id": "01a1f800-0000-7000-8000-000000000001",
    "id": "centrifugal_pump",
    "parent": "01a1f800-0000-7000-8000-000000000000",
    "appearance": {
      "icon_drawing": "<svg xmlns=\"http://www.w3.org/2000/svg\" viewBox=\"0 0 24 24\"><circle cx=\"12\" cy=\"12\" r=\"9\"/></svg>",
      "color_value": null
    },
    "documentation": {
      "description": "A **centrifugal** pump, driven by a variable speed motor.",
      "links": [
        {
          "internal_id": "01a1f800-0000-7000-8000-000000000010",
          "kind": "url",
          "address": "https://example.com/datasheets/centrifugal-pump",
          "description": "Datasheet"
        }
      ]
    },
    "signals": [
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000020",
        "direction": "input",
        "id": "speed_setpoint",
        "description": "Speed asked of the motor.",
        "value_type": {
          "kind": "real",
          "quantity": "01a1f800-0000-7000-8000-000000000900",
          "relative_quantity": false
        }
      },
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000021",
        "direction": "input",
        "id": "speed_max",
        "description": "Highest speed the operator may ask for.",
        "value_type": {
          "kind": "real",
          "quantity": "01a1f800-0000-7000-8000-000000000900",
          "relative_quantity": false
        }
      },
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000022",
        "direction": "output",
        "id": "speed",
        "description": "Speed of the motor, computed by the model.",
        "value_type": {
          "kind": "real",
          "quantity": "01a1f800-0000-7000-8000-000000000900",
          "relative_quantity": false
        }
      },
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000023",
        "direction": "output",
        "id": "running",
        "description": "True while the pump turns.",
        "value_type": {
          "kind": "boolean"
        }
      },
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000024",
        "direction": "input",
        "id": "mode",
        "description": "How the pump is driven.",
        "value_type": {
          "kind": "enum",
          "enum": "01a1f800-0000-7000-8000-000000000500"
        }
      },
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000025",
        "direction": "output",
        "id": "bearing_temperature_rise",
        "description": "How much the bearing is warmer than the room.",
        "value_type": {
          "kind": "real",
          "quantity": "01a1f800-0000-7000-8000-000000000910",
          "relative_quantity": true
        }
      }
    ],
    "commands": [
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000030",
        "kind": "trigger",
        "id": "start",
        "description": "Tells that the start of the pump was asked."
      },
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000031",
        "kind": "set_input_signal",
        "id": "switch_to_auto",
        "description": "Puts the pump in automatic mode.",
        "command_target": {
          "signal": "01a1f800-0000-7000-8000-000000000024",
          "value": "01a1f800-0000-7000-8000-000000000502"
        }
      },
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000032",
        "kind": "override_output_signal",
        "id": "force_speed",
        "description": "Replaces the speed computed by the model, for a test.",
        "command_target": {
          "signal": "01a1f800-0000-7000-8000-000000000022",
          "value": 151.8436
        }
      }
    ],
    "flags": [
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000040",
        "id": "under_maintenance",
        "description": "The pump is out of service for maintenance."
      }
    ],
    "presets": [
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000050",
        "name": "Standard",
        "preset_values": [
          {
            "signal": "01a1f800-0000-7000-8000-000000000020",
            "start_value": 0,
            "display_format": {
              "unit": "01a1f800-0000-7000-8000-000000000902",
              "decimals": 0
            }
          },
          {
            "signal": "01a1f800-0000-7000-8000-000000000021",
            "start_value": 157.0796,
            "display_format": {
              "unit": "01a1f800-0000-7000-8000-000000000902",
              "decimals": 0
            }
          },
          {
            "signal": "01a1f800-0000-7000-8000-000000000022",
            "start_value": 0,
            "display_format": {
              "unit": "01a1f800-0000-7000-8000-000000000902",
              "decimals": 1
            }
          },
          {
            "signal": "01a1f800-0000-7000-8000-000000000023",
            "start_value": false,
            "boolean_texts": {
              "true_text": "Running",
              "false_text": "Stopped"
            }
          },
          {
            "signal": "01a1f800-0000-7000-8000-000000000024",
            "start_value": "01a1f800-0000-7000-8000-000000000501"
          },
          {
            "signal": "01a1f800-0000-7000-8000-000000000025",
            "start_value": 0,
            "display_format": {
              "unit": "01a1f800-0000-7000-8000-000000000912",
              "decimals": 1
            }
          }
        ],
        "faceplate_elements": [
          {
            "internal_id": "01a1f800-0000-7000-8000-000000000060",
            "kind": "title",
            "text_content": {
              "source": "designation",
              "designation": "01a1f800-0000-7000-8000-000000000800"
            }
          },
          {
            "internal_id": "01a1f800-0000-7000-8000-000000000061",
            "kind": "paragraph",
            "text_content": {
              "source": "typed",
              "typed_text": "Feed pump of the main loop."
            }
          },
          {
            "internal_id": "01a1f800-0000-7000-8000-000000000062",
            "kind": "group",
            "faceplate_elements": [
              {
                "internal_id": "01a1f800-0000-7000-8000-000000000063",
                "kind": "signal",
                "signal_field": {
                  "signal": "01a1f800-0000-7000-8000-000000000020",
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
                      "signal": "01a1f800-0000-7000-8000-000000000021"
                    }
                  }
                }
              },
              {
                "internal_id": "01a1f800-0000-7000-8000-000000000064",
                "kind": "signal",
                "signal_field": {
                  "signal": "01a1f800-0000-7000-8000-000000000022",
                  "access": "read",
                  "display_name": null
                }
              },
              {
                "internal_id": "01a1f800-0000-7000-8000-000000000065",
                "kind": "signal",
                "signal_field": {
                  "signal": "01a1f800-0000-7000-8000-000000000023",
                  "access": "read",
                  "display_name": "State"
                }
              }
            ]
          },
          {
            "internal_id": "01a1f800-0000-7000-8000-000000000066",
            "kind": "signal",
            "signal_field": {
              "signal": "01a1f800-0000-7000-8000-000000000024",
              "access": "write",
              "input_kind": "radio_horizontal",
              "display_name": "Mode"
            }
          },
          {
            "internal_id": "01a1f800-0000-7000-8000-000000000067",
            "kind": "command",
            "command_button": {
              "command": "01a1f800-0000-7000-8000-000000000030",
              "display_name": "Start"
            }
          }
        ]
      }
    ]
  }
}
```

### The enums

```json
{
  "format_version": 1,
  "enums": [
    {
      "internal_id": "01a1f800-0000-7000-8000-000000000500",
      "kind": "global",
      "id": "operating_mode",
      "description": "How a piece of equipment is driven.",
      "enum_items": [
        {
          "internal_id": "01a1f800-0000-7000-8000-000000000501",
          "key": 0,
          "display_name": "Manual",
          "description": "Driven by the operator."
        },
        {
          "internal_id": "01a1f800-0000-7000-8000-000000000502",
          "key": 1,
          "display_name": "Auto",
          "description": "Driven by the control loop."
        }
      ]
    },
    {
      "internal_id": "01a1f800-0000-7000-8000-000000000510",
      "kind": "template",
      "id": "switch_positions",
      "description": "The positions of a switch.",
      "enum_items": []
    }
  ]
}
```

### A quantity

```json
{
  "format_version": 1,
  "quantity": {
    "internal_id": "01a1f800-0000-7000-8000-000000000910",
    "name": "temperature",
    "default_unit": "01a1f800-0000-7000-8000-000000000911",
    "offers_relative_quantity": true,
    "unit_systems": [
      {
        "internal_id": "01a1f800-0000-7000-8000-000000000915",
        "name": "metric",
        "units": [
          {
            "internal_id": "01a1f800-0000-7000-8000-000000000911",
            "name": "kelvin",
            "symbol": "K"
          },
          {
            "internal_id": "01a1f800-0000-7000-8000-000000000912",
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
        "internal_id": "01a1f800-0000-7000-8000-000000000916",
        "name": "imperial",
        "units": [
          {
            "internal_id": "01a1f800-0000-7000-8000-000000000913",
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
}
```
