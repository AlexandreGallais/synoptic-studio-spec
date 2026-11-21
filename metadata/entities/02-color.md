# Color

> [Home](../../README.md) › [Metadata](../README.md) › [Entities](README.md) › Color

| Version | Date | Status | Change |
| --- | --- | --- | --- |
| 1 | 2026-11-22 | Draft | Creation of the file |

A color is one color of a [Palette](03-palette.md), picked for the appearance of a type. It exists only inside its palette, never on its own, and is kept in the palette's file. A type points to it by its `internal_id`, never by its value: changing the value in the palette changes every type that uses it.

## The entity

```mermaid
erDiagram
    COLOR {
        uuid internal_id PK
        text name
        rgb value
    }
```

| Field | Required | Default | What it is |
| --- | --- | --- | --- |
| `internal_id` | ✓ |  | The unique identifier inside the software, set by it. It never leaves the software. |
| `name` | ✓ |  | The label shown on hover, to tell the colors apart. |
| `value` | ✓ |  | The color itself, as a hexadecimal code (`#1f77b4`). |

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "color.schema.json",
  "title": "Synoptic Studio color",
  "type": "object",
  "required": ["internal_id", "name", "value"],
  "additionalProperties": false,
  "properties": {
    "internal_id": {
      "description": "Primary key, unique; surrogate key, never exported. UUID version 7 (RFC 9562), lower case, set by the software.",
      "type": "string",
      "pattern": "^[0-9a-f]{8}-[0-9a-f]{4}-7[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$",
      "readOnly": true
    },
    "name": {
      "description": "The label shown on hover.",
      "type": "string",
      "minLength": 1
    },
    "value": {
      "description": "The color, as a hexadecimal sRGB code, lower case, without transparency.",
      "type": "string",
      "pattern": "^#[0-9a-f]{6}$"
    }
  }
}
```

## Open questions

- Is the `name` of a color unique in its palette?
