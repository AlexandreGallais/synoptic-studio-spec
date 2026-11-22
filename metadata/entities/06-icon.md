# Icon

> [Home](../../README.md) › [Metadata](../README.md) › [Entities](README.md) › Icon

| Version | Date | Status | Change |
| --- | --- | --- | --- |
| 1 | 2026-11-22 | Draft | Creation of the file |

An icon is one drawing of an [Icon set](07-icon-set.md), picked for the appearance of a type. It exists only inside its icon set's file.

## The entity

```mermaid
erDiagram
    ICON {
        uuid internal_id PK
        text name
        svg drawing
    }
```

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "icon.schema.json",
  "title": "Synoptic Studio icon",
  "type": "object",
  "required": ["internal_id", "name", "drawing"],
  "additionalProperties": false,
  "properties": {
    "internal_id": {
      "description": "Primary key.",
      "type": "string",
      "pattern": "^[0-9a-f]{8}-[0-9a-f]{4}-7[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$",
      "readOnly": true
    },
    "name": {
      "description": "What the icon shows, read on hover and searched in the list; unique in its icon set.",
      "type": "string",
      "minLength": 1,
      "examples": ["centrifugal-pump"]
    },
    "drawing": {
      "description": "The whole SVG of the icon, from <svg> to </svg>.",
      "type": "string",
      "minLength": 1
    }
  }
}
```

## Open questions

- What the SVG of an icon may hold: its size and `viewBox`, and how the color of the type is put on the drawing (a type shows its icon in its color).
