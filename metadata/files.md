# Files

> [Home](../README.md) › [Metadata](README.md) › Files

Status: draft, written on 2026-11-21 at the Product Owner's request, from the [Data model: notes](data-model-notes.md#how-the-schema-becomes-json) and the [whole draft](draft.md#files); not validated yet.

The rules every file of Metadata follows. An [entity file](entities/README.md) gives only the JSON Schema of its own file; what holds for every file is written here, never on an entity.

## Each file

- **`"format"` is the first key**: the version of the file format, not of Metadata (decision 0053), so that a later Synoptic Studio can still read an older file. It belongs to the file, not to an entity, so it is never in the schema of the [Data model](data-model.md).
- **The rules of each file are given in JSON Schema (draft 2020-12)**, so that a file can be checked by a program. A JSON Schema says only what the specification settles.

## From the schema to JSON

- A field keeps its name in the schema.
- A part (`has`) is a nested object named after its box, in lower case; two parts of the same box are named by their role (`min`, `max`).
- A list (`holds`) is an array named after the box it holds, in lower case and in the plural (`identifiers`, `signals`, `enum_items`); the same list has the same name everywhere.
- A field or a part that does not exist in this case (its `when` is false) is left out; one that exists but is empty is `null`.
- A choice of several words is joined by underscores (`"set_signal"`).

## The order of the keys

- **The keys of each object always follow the field order of its schema**, then its parts and its lists.
- A file whose order is not respected is still read; when the software saves it, it writes it again in the order of the schema.

## The files of Metadata

| File | What it holds | Status |
| --- | --- | --- |
| `types/<internal ID>.json` | One type, its signals, commands, flags and presets | One file per type: settled. Named by internal ID: proposal. |
| `enums/<internal ID>.json` | One global enum and its items | Proposal |
| `identifiers.json`, at the root of Metadata | All the [identifiers](entities/01-identifier.md) | Proposal |

## Open questions

- JSON files rather than a database: a leaning of the Product Owner, not settled.
- The names and places of the files: proposals above.
- The catalogue of quantities: one file with one `format` at its top, or one file per quantity.
- The other open questions on files stay in the [whole draft](draft.md#files).
