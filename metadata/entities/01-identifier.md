# Identifier

> [Home](../../README.md) › [Metadata](../README.md) › [Entities](README.md) › Identifier

Status: draft, written on 2026-11-21 at the Product Owner's request, from the page Identifiers of the [whole draft](../draft.md#identifiers) (decision 0048) and the [Data model](../data-model.md). The head (status and introduction) and the order of the sections are validated by the Product Owner on 2026-11-21; the rest is being read. "Identifier" is still a working name.

An identifier is a named key that each placed symbol fills with its own text, in the synoptic: the tag of a pump, for example `P-101`. Metadata only makes the key, never the text. Identifiers are global: they belong to no type, every type can use them, and they are all kept in one file.

## The entity

```mermaid
erDiagram
    IDENTIFIER {
        uuid internal_id PK "required, generated"
        text id "required, no default"
        boolean required "required, default false"
        text description "optional, no default"
    }
```

| Field | What it is | Rule |
| --- | --- | --- |
| `internal_id` | The UUID set by the software, version 7 (see [Rules of the schema](../data-model-notes.md#rules-of-the-schema)) | Generated when the identifier is created. Never changes, never leaves the application. A faceplate points to the identifier through it, so a changed `id` breaks nothing. |
| `id` | The key | Written by the user. The public identifier, as for every entity of Metadata. It is also what people read: the identifier has no display name. |
| `required` | Whether its text must be filled | `true`: every placed symbol must have its text (a control ID, the tag of the equipment). `false`: the text may stay empty (a location, given for context). `false` for a new identifier (Product Owner, 2026-11-21). |
| `description` | What the identifier is | Plain text, for people. Empty: `null`. |

- **Required or not** (Product Owner, 2026-11-21: "j'ai complètement besoin de dire si c'est required ou non [...] des identifiants qui vont forcément être requis, comme un ID [...] un ID qui est la localisation de la chose [...] qui ne serait pas obligatoire").
  - **On every placed symbol**, whether or not its faceplate shows the identifier (Product Owner, questionnaire of 2026-11-21: "Sur tous les symboles placés"): required means each piece of equipment has its control ID.
  - **An empty required text warns, never blocks** (same questionnaire: "Avertir sans bloquer"): the field is marked, the placed symbol is listed in the faults as a warning, and the synoptic is saved anyway, so that the work can be finished later.
- **Field order: what the identifier is, what it asks for, then what explains it** (assistant's choice, left to it by the Product Owner, who wants "un ordre le plus logique possible"): `internal_id`, `id`, `required`, `description`. It is also the order of every box of the schema, where the text that explains comes last.
- **A few identifiers per project**: usually three, four at most (Product Owner, 2026-11-21: "Normalement, ils sont censés en avoir trois. Je pense qu'on aura trois, quatre grands max"). An order of size for the screens, not a limit set by the software.
- **No display name** (Product Owner, 2026-11-21: "on va dégager display name [...] on voit que l'ID [...] Par contre, faut laisser la description"): the `id` is shown everywhere the identifier is picked or filled. Removing it breaks nothing in a first version.
- The title or description of a faceplate that points to an identifier is a `TEXT_CONTENT` of the preset (see [Data model](../data-model.md)); it belongs to the faceplate, so it is not drawn on this page (assistant's choice, left to it by the Product Owner).
- No value of its own: the text in front of the key is filled on each placed symbol, in the synoptic (part 3).
- The order of the list is the order chosen by the user on the page Identifiers, with the handles.

## The file

All the identifiers are kept in one file, since they are global and their order is the order on the screen. Its name and its place are a proposal: `identifiers.json`, at the root of the Metadata folder, beside `types/` and `enums/`.

- `"format"` first, the version of the file format, as in every file (see [Files](../draft.md#files)).
- Then `identifiers`, the ordered list, named after the box in the plural.
- Each identifier keeps the field order of the schema: `internal_id`, `id`, `required`, `description`.

### Example

Two made-up identifiers. The internal IDs are made up too; `…800` is the one the title of the [type example](../data-model.md#a-type) points to.

```json
{
  "format": 1,
  "identifiers": [
    {
      "internal_id": "01a1f800-0000-7000-8000-000000000800",
      "id": "tag",
      "required": true,
      "description": "The tag of the equipment, as on the plant drawings."
    },
    {
      "internal_id": "01a1f800-0000-7000-8000-000000000801",
      "id": "location",
      "required": false,
      "description": null
    }
  ]
}
```

### JSON Schema

The rules of the file, in JSON Schema (draft 2020-12), so that a file can be checked by a program. It says only what the specification settles: nothing on how an `id` is written, nor on its uniqueness, both still open.

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Synoptic Studio identifiers file",
  "type": "object",
  "required": ["format", "identifiers"],
  "additionalProperties": false,
  "properties": {
    "format": {
      "description": "Version of the file format.",
      "const": 1
    },
    "identifiers": {
      "description": "Every identifier, in the order chosen by the user.",
      "type": "array",
      "items": { "$ref": "#/$defs/identifier" }
    }
  },
  "$defs": {
    "identifier": {
      "type": "object",
      "required": ["internal_id", "id", "required", "description"],
      "additionalProperties": false,
      "properties": {
        "internal_id": {
          "description": "UUID version 7 (RFC 9562) set by the software, lower case, never changes.",
          "type": "string",
          "pattern": "^[0-9a-f]{8}-[0-9a-f]{4}-7[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$"
        },
        "id": {
          "description": "The key, written by the user.",
          "type": "string"
        },
        "required": {
          "description": "true: its text must be filled on every placed symbol; empty, a warning, never a block.",
          "type": "boolean"
        },
        "description": {
          "description": "What the identifier is, plain text; null when empty.",
          "type": ["string", "null"]
        }
      }
    }
  }
}
```

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Identifier (`id`, `description`), its order | Page Identifiers of Metadata | `TEXT_CONTENT` of a title or description element of a faceplate | No | Its text, filled on each placed symbol |
| `required` | Page Identifiers of Metadata | The panel of a placed symbol, which asks for the text; the faults | No | Every placed symbol asks for the text; left empty, a warning, never a block |
| File `identifiers.json` | The software, at each change on the page Identifiers | Read when Metadata opens | No | No |

## Open questions

- The name of the concept and of the page (still "Identifiers").
- The words `id` and `internal_id`: research T5.
- The name and the place of the file (`identifiers.json` at the root of Metadata: proposal).
- Must an `id` be unique on the page? May it be empty?
- Are the configuration files of a synoptic made while a required text is empty (proposal: yes, with the warning, since nothing blocks)?
- The other open questions of the page stay in the [whole draft](../draft.md#open-questions-8).
