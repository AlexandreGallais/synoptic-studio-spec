# Files

> [Home](../README.md) › [Metadata](README.md) › Files

| Version | Date | Status | Change |
| --- | --- | --- | --- |
| 1 | 2026-11-22 | Draft | Creation of the file |

The rules every file of Metadata follows. An [entity file](entities/README.md) gives only the JSON Schemas of its entity and of its own file; what holds for every file is written here, never on an entity.

## Each file

- **`"format_version"` is the first key**: the version of the file format, not of Metadata (decision 0053), so that a later Synoptic Studio can still read an older file. It belongs to the file, not to an entity, so it is never in the schema of the [Data model](data-model.md).
- **One schema per version of the file format**: the schema of a file fixes its `format_version` to one value (`"const": 1`). A new version of the format gets a schema of its own, and the software reads `format_version` first to choose the schema that checks the file.
- **The rules of each file are given in JSON Schema (draft 2020-12)**. The software checks each object against it and lists where the errors are; a file with errors is still read and written.
- **A text is never an empty string**: empty is `null`.

## The two keys of an entity

- **`internal_id` is always a UUID version 7**, set by the software. It is the surrogate key: every link (FK) holds one, and it never leaves the software.
- **`id` is never a UUID**: the key the user writes, shown on screen, sent to the model and written in the configuration files.
- **When a file is exported to a standard**, each key goes to its match there, never the other way round:

| Synoptic Studio | AutomationML | OPC UA | FMI |
| --- | --- | --- | --- |
| `internal_id` | `ID` | `NodeId` | — |
| `id` | `Name` | `BrowseName` | `name` |

## From the schema to JSON

- A field keeps its name in the schema.
- A part (`has`) is a nested object named after its box, in lower case; two parts of the same box are named by their role (`min`, `max`).
- A list (`holds`) is an array named after the box it holds, in lower case and in the plural (`designations`, `signals`, `enum_items`); the same list has the same name everywhere.
- A field or a part that does not exist in this case (its `when` is false) is left out; one that exists but is empty is `null`.
- A choice of several words is joined by underscores (`"set_signal"`).

## The order of the keys

- **The keys of each object always follow the field order of its schema**, then its parts and its lists.
- A file whose order is not respected is still read; when the software saves it, it writes it again in the order of the schema.

## The name of a file

- An entity with a file of its own gives the file's name in its tag `File`.
- **One file for the whole list**: the name of its list, then `.json` (`designations.json`). That name is reserved for that entity: no other file may take it.
- **One file per thing** (a palette): its `internal_id`, then the entity's name, then `.json` (`<internal_id>.palette.json`), so that renaming it breaks nothing. The file holds `format_version`, then the thing as one object named after its entity in lower case (`"palette": { … }`).
- Where the files are placed is settled by the software architecture, not here.

## Shared types

To come: one global JSON Schema will hold the types every entity shares, and the entity schemas will refer to it instead of repeating them. The first one is the UUID: every UUID of Synoptic Studio is a UUID version 7 (RFC 9562), which starts with the time of its creation (see [Rules of the schema](data-model-notes.md#rules-of-the-schema)).

## Open questions

- JSON files rather than a database: a leaning of the Product Owner, not settled.
- The catalogue of quantities: one file with one `format_version` at its top, or one file per quantity.
- The examples of a type and of a global enum in the [Data model](data-model.md) put their fields beside `format_version`, not in one object named after the entity as a palette does: to make even when those entities are written.
- The other open questions on files stay in the [whole draft](draft.md#files).
