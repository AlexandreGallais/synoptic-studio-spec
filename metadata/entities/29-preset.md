# Preset

> [Home](../../README.md) › [Metadata](../README.md) › [Entities](README.md) › Preset

| Version | Date | Status | Change |
| --- | --- | --- | --- |
| 1 | 2026-11-22 | Draft | Creation of the file |

A preset holds the defaults a symbol and a synoptic start from: how each signal of the type starts and is shown, its [preset values](22-preset-value.md), and the faceplate it builds, its [faceplate elements](28-faceplate-element.md). A type needs at least one preset to be chosen in a symbol or a synoptic. A preset exists only inside its [type](30-type.md), in the type's list of presets.

## The entity

```mermaid
erDiagram
    PRESET {
        uuid internal_id PK
        text name
    }
    PRESET ||--o{ PRESET_VALUE : "holds, one per signal of the type"
    PRESET ||--o{ FACEPLATE_ELEMENT : "holds"
```

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "preset.schema.json",
  "title": "Synoptic Studio preset",
  "type": "object",
  "required": ["internal_id", "name", "preset_values", "faceplate_elements"],
  "additionalProperties": false,
  "properties": {
    "internal_id": {
      "description": "Primary key.",
      "type": "string",
      "pattern": "^[0-9a-f]{8}-[0-9a-f]{4}-7[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$",
      "readOnly": true
    },
    "name": {
      "description": "Tells two presets of a type apart, for people; never sent to the model.",
      "type": "string",
      "minLength": 1,
      "examples": ["Standard"]
    },
    "preset_values": {
      "description": "Exactly one per signal of the type, own and inherited.",
      "type": "array",
      "items": { "$ref": "preset-value.schema.json" }
    },
    "faceplate_elements": {
      "description": "The elements of the faceplate, in the order it shows them.",
      "type": "array",
      "items": { "$ref": "faceplate-element.schema.json" }
    }
  }
}
```

## Open questions

- Is the `name` of a preset unique among the presets of its type?
- A signal added to the type, or to one of its parents: does the software add its preset value to every preset of the type and of its sub-types, with the start value and the display format a new preset value starts with? And a signal removed: is its preset value removed, with the faceplate elements that show it?
