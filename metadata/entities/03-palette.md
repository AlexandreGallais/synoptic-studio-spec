# Palette

> [Home](../../README.md) › [Metadata](../README.md) › [Entities](README.md) › Palette

| Version | Date | Status | Change |
| --- | --- | --- | --- |
| 1 | 2026-11-22 | Draft | Creation of the file |

| Tag | Value |
| --- | --- |
| File | `<internal_id>.palette.json` |

A palette is a named, ordered set of [colors](02-color.md): the only place where colors are kept, and the only colors a type can pick. Each palette has a file of its own, so that a palette is added or removed with its file.

## The entity

```mermaid
erDiagram
    PALETTE {
        uuid internal_id PK
        text name
    }
    PALETTE ||--|{ COLOR : "holds"
```

| Field | Required | Default | What it is |
| --- | --- | --- | --- |
| `internal_id` | ✓ |  | The unique identifier inside the software, set by it. It never leaves the software. |
| `name` | ✓ |  | The label people read to tell the palettes apart. |
| `colors` | ✓ |  | Its [colors](02-color.md), in the order chosen by the user. |

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "palette.schema.json",
  "title": "Synoptic Studio palette",
  "type": "object",
  "required": ["internal_id", "name", "colors"],
  "additionalProperties": false,
  "properties": {
    "internal_id": {
      "description": "Primary key, unique; surrogate key, never exported. UUID version 7 (RFC 9562), lower case, set by the software.",
      "type": "string",
      "pattern": "^[0-9a-f]{8}-[0-9a-f]{4}-7[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$",
      "readOnly": true
    },
    "name": {
      "description": "The label people read to tell the palettes apart.",
      "type": "string",
      "minLength": 1
    },
    "colors": {
      "description": "Every color of the palette, in the order chosen by the user.",
      "type": "array",
      "minItems": 1,
      "items": { "$ref": "color.schema.json" }
    }
  }
}
```

## The file

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "palette-file.schema.json",
  "title": "Synoptic Studio palette file",
  "type": "object",
  "required": ["format_version", "palette"],
  "additionalProperties": false,
  "properties": {
    "format_version": {
      "description": "Version of the file format.",
      "const": 1
    },
    "palette": {
      "description": "The palette the file holds, with its colors.",
      "$ref": "palette.schema.json"
    }
  }
}
```

## Open questions

- Is the `name` of a palette unique?
- A type whose color belonged to a palette that was removed: does it follow its parent's color, as when its color is empty?
- Which palettes ship with the software, and whether the user can add their own: defined with the design system.
