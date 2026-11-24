# Type

> [Home](../../README.md) › [Metadata](../README.md) › [Entities](README.md) › Type

| Version | Date | Status | Change |
| --- | --- | --- | --- |
| 1 | 2026-11-22 | Draft | Creation of the file |
| 2 | 2026-11-24 | Draft | No more presets: the type holds its signal settings, its faceplate elements and their order |

| Tag | Value |
| --- | --- |
| File | `<id>.type.json` |

A type is what a symbol represents, at one level of detail: a pump, a centrifugal pump. Types form a tree: a type has one parent or none, set when it is created and never changed, and inherits everything of its parents: signals, commands, flags, documentation, signal settings and faceplate (see [Inheritance of types](../inheritance.md)). There are no presets: to show a type another way, a sub-type is made. A type holds its [appearance](12-appearance.md), its [documentation](14-documentation.md), its own [signals](16-signal.md), [commands](18-command.md) and [flags](19-flag.md), the [signal settings](22-signal-setting.md) of its signals, and its own [faceplate elements](28-faceplate-element.md). Its `id` is the contract with the model: renaming it breaks the models that use it, never the software, whose links go through the `internal_id`. One file per type. A type whose parent's file is missing or unreadable is still shown, flagged in error with the missing parent named; its file is left as it is. A type that has sub-types cannot be deleted: its sub-types are deleted first.

## The entity

```mermaid
erDiagram
    %% link TYPE 30-type.md
    %% link APPEARANCE 12-appearance.md
    %% link DOCUMENTATION 14-documentation.md
    %% link SIGNAL 16-signal.md
    %% link COMMAND 18-command.md
    %% link FLAG 19-flag.md
    %% link SIGNAL_SETTING 22-signal-setting.md
    %% link FACEPLATE_ELEMENT 28-faceplate-element.md
    TYPE {
        uuid internal_id PK
        text id
        uuid parent FK
        uuid_list faceplate_order
    }
    TYPE |o--o{ TYPE : "parent"
    TYPE ||--|| APPEARANCE : "has"
    TYPE ||--|| DOCUMENTATION : "has"
    TYPE ||--o{ SIGNAL : "holds"
    TYPE ||--o{ COMMAND : "holds"
    TYPE ||--o{ FLAG : "holds"
    TYPE ||--o{ SIGNAL_SETTING : "holds, one per own signal, and one per inherited signal it changes"
    TYPE ||--o{ FACEPLATE_ELEMENT : "holds"
```

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "type.schema.json",
  "title": "Synoptic Studio type",
  "type": "object",
  "required": ["internal_id", "id", "parent", "appearance", "documentation", "signals", "commands", "flags", "signal_settings", "faceplate_elements", "faceplate_order"],
  "additionalProperties": false,
  "properties": {
    "internal_id": {
      "description": "Primary key.",
      "type": "string",
      "pattern": "^[0-9a-f]{8}-[0-9a-f]{4}-7[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$",
      "readOnly": true
    },
    "id": {
      "description": "The name of the type for the model, readable and exact; unique in the whole type tree.",
      "type": "string",
      "minLength": 1,
      "examples": ["centrifugal_pump"]
    },
    "parent": {
      "description": "Foreign key to the type it is created under, set at creation and never changed. Null: a type at the root of the tree.",
      "type": ["string", "null"],
      "pattern": "^[0-9a-f]{8}-[0-9a-f]{4}-7[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$"
    },
    "appearance": {
      "description": "The icon and the color the type shows.",
      "$ref": "appearance.schema.json"
    },
    "documentation": {
      "description": "What explains the type to people.",
      "$ref": "documentation.schema.json"
    },
    "signals": {
      "description": "The type's own signals, in the order of its table of signals; those it inherits are not repeated.",
      "type": "array",
      "items": { "$ref": "signal.schema.json" }
    },
    "commands": {
      "description": "The type's own commands, in the order of its table of commands; those it inherits are not repeated.",
      "type": "array",
      "items": { "$ref": "command.schema.json" }
    },
    "flags": {
      "description": "The type's own flags, in the order of its table of flags; those it inherits are not repeated.",
      "type": "array",
      "items": { "$ref": "flag.schema.json" }
    },
    "signal_settings": {
      "description": "How each signal starts and is shown: one per own signal, and one per inherited signal whose setting the type changes; an inherited signal it leaves alone shows its parent's.",
      "type": "array",
      "items": { "$ref": "signal-setting.schema.json" }
    },
    "faceplate_elements": {
      "description": "The type's own faceplate elements; those of its parents are not repeated: they are shown read only, and only their place changes.",
      "type": "array",
      "items": { "$ref": "faceplate-element.schema.json" }
    },
    "faceplate_order": {
      "description": "The internal_id of every element at the top of the faceplate, inherited and own, in the order it shows them. Empty: the elements of the parents, from the root down, then the own ones. An element missing from it is shown at the end; an internal_id that no longer exists is ignored.",
      "type": "array",
      "items": {
        "type": "string",
        "pattern": "^[0-9a-f]{8}-[0-9a-f]{4}-7[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$"
      },
      "uniqueItems": true
    }
  }
}
```

## The file

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "type-file.schema.json",
  "title": "Synoptic Studio type file",
  "type": "object",
  "required": ["format_version", "type"],
  "additionalProperties": false,
  "properties": {
    "format_version": {
      "const": 1
    },
    "type": {
      "description": "The type the file holds.",
      "$ref": "type.schema.json"
    }
  }
}
```

## Open questions

- May an own element of the faceplate go between two elements of a parent, as `faceplate_order` allows, or only after them?
- Inside a group of a parent, may a sub-type move or add elements?
