# Designation

> [Home](../../README.md) › [Metadata](../README.md) › [Entities](README.md) › Designation

| Version | Date | Status | Change |
| --- | --- | --- | --- |
| 1 | 2026-11-22 | Draft | Creation of the file |

| Tag | Value |
| --- | --- |
| File | `designations.json` |

A designation is what identifies the equipment a placed symbol stands for, such as its tag or its location. Metadata defines it once, by its `id` (`tag`, `location`); its text is written on each placed symbol, in the synoptic: `P-101` for the tag of a pump, `Hall B` for where it stands. A title or a paragraph of a faceplate can show it. Designations belong to no type and are all kept in one file.

## The entity

```mermaid
erDiagram
    DESIGNATION {
        uuid internal_id PK
        text id
        boolean required
        text description
    }
```

| Field | Required | Default | What it is |
| --- | --- | --- | --- |
| `internal_id` | ✓ |  | The unique identifier inside the software, set by it. It never leaves the software. |
| `id` | ✓ |  | The key the user gives. The software shows it and writes it in the configuration files it makes; `internal_id` never appears there. |
| `required` | ✓ | `false` | Whether its text must be filled on every placed symbol. |
| `description` |  |  | What the designation is, in plain text for people. |

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "designation.schema.json",
  "title": "Synoptic Studio designation",
  "type": "object",
  "required": ["internal_id", "id", "required", "description"],
  "additionalProperties": false,
  "properties": {
    "internal_id": {
      "description": "Primary key, unique; surrogate key, never exported. UUID version 7 (RFC 9562), lower case, set by the software.",
      "type": "string",
      "pattern": "^[0-9a-f]{8}-[0-9a-f]{4}-7[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$",
      "readOnly": true
    },
    "id": {
      "description": "The key the user gives, never a UUID; written in the configuration files in place of internal_id.",
      "type": "string",
      "minLength": 1
    },
    "required": {
      "description": "Whether its text must be filled on every placed symbol.",
      "type": "boolean",
      "default": false
    },
    "description": {
      "description": "What the designation is, plain text for people.",
      "type": ["string", "null"],
      "minLength": 1
    }
  }
}
```

## The file

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "designations.schema.json",
  "title": "Synoptic Studio designations file",
  "type": "object",
  "required": ["format_version", "designations"],
  "additionalProperties": false,
  "properties": {
    "format_version": {
      "description": "Version of the file format.",
      "const": 1
    },
    "designations": {
      "description": "Every designation, in the order chosen by the user.",
      "type": "array",
      "items": { "$ref": "designation.schema.json" }
    }
  }
}
```
