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

- **`internal_id`, set by the software, and `id`, written by the user**: their rules, their uniqueness and their match in the standards are in [Identity and renaming](identity-and-renaming.md#the-two-keys).

## From the schema to JSON

- A field keeps its name in the schema.
- A part (`has`) is a nested object named after its box, in lower case; two parts of the same box are named by their role (`min`, `max`).
- A list (`holds`) is an array named after the box it holds, in lower case and in the plural (`designations`, `signals`, `enum_items`); the same list has the same name everywhere.
- A field or a part that does not exist in this case (its `when` is false) is left out; one that exists but is empty is `null`.
- A choice of several words is joined by underscores (`"set_input_signal"`).

## The order of the keys

- **The keys of each object always follow the field order of its schema**, then its parts and its lists.
- A file whose order is not respected is still read; when the software saves it, it writes it again in the order of the schema.

## The name of a file

- An entity with a file of its own gives the file's name in its tag `File`.
- **A file's name means something to a person**, never an `internal_id`: the files are read and shared by people.
- **One file for the whole list**: the name of its list, then `.json` (`designations.json`). That name is reserved for that entity: no other file may take it.
- **One file per thing** (a palette, a type): the file name of its `name`, or of its `id` when it has one, then the entity's name, then `.json` (`pompes-bleues.palette.json`, `centrifugal-pump.type.json`). Renaming the thing renames its file.
- **The file name of a `name` or an `id`, in kebab-case**: in lower case, without accents, each run of characters other than a letter or a digit becoming one hyphen `-`, without a hyphen at either end ("Pompes bleues" gives `pompes-bleues`). The same on Windows, macOS and Linux. The hyphen, not the underscore: it is the usual separator in file names and web addresses, and keeps file names apart from the snake_case keys inside the files.
- **Two things of the same entity never give the same file name**: a `name` or an `id` whose file name is taken, or that gives an empty one, is refused (`centrifugal_pump` and `centrifugal-pump` both give `centrifugal-pump`).

## The two configuration folders

- **The configuration files, such as the palettes and the icon sets, are kept in two folders**: the software's and the user's. The software reads both, and offers what it finds in both.
- **The software's folder** holds what Synoptic Studio ships. The user may change its files by hand; a file they break is read like any file with errors.
- **The user's folder** holds what the user adds; they do with it what they want.
- **The same file name in both folders: the user's file is offered**, the software's is not (decision 0071). The user replaces a file of the software without touching the software's folder.
- **The built-in enums are the exception, matched by `internal_id`**: their `enums.json` is inside the program, not in the software's folder, and cannot be changed. The software reads it with the user's `enums.json`, and an enum of the user with the `internal_id` of a built-in enum overrides it whole (see [Overriding a built-in enum](draft.md#overriding-a-built-in-enum), decision 0095).
- Where the two folders are on each system, and where the other files are placed, is settled by the software architecture, not here.

## What a file holds

- **`format_version`, then one key**, named after what the file holds, in lower case: the list in the plural for a whole list (`"designations": [ … ]`, `"enums": [ … ]`), the entity in the singular for one thing (`"palette": { … }`, `"type": { … }`).
- The fields of an entity are never beside `format_version`: the entity's schema stays closed, and the file's schema only adds the key that holds it.

## Shared types

To come: one global JSON Schema will hold the types every entity shares, and the entity schemas will refer to it instead of repeating them. The first one is the UUID: every UUID of Synoptic Studio is a UUID version 7 (RFC 9562), which starts with the time of its creation (see [Rules of the schema](data-model-notes.md#rules-of-the-schema)).

## Open questions

- JSON files rather than a database: a leaning, not settled.
- Which files are configuration files, in the two folders, beside the palettes and the icon sets: the catalogue of quantities, others? Left for later.
- The same `internal_id` under two different file names, in the software's folder and in the user's: which one is offered?
- **The format of the `id`s, an idea not settled**: a settings page where the user chooses the format each kind of `id` must follow, as a regular expression kept in the settings configuration file; the software tells when an `id` typed does not follow it, and the user writes their own expressions in that file. Open: whether a format is set by default or none (today no rule says how an ID is written); a message only, or the `id` refused; one format per entity or shared ones. See [Data model notes](data-model-notes.md#noted-on-2026-11-22-format-of-the-ids-idea).
- The other open questions on files stay in the [whole draft](draft.md#files).
