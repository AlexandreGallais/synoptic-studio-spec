# metadata

> [Home](../README.md) › Metadata

The first part of Synoptic Studio: the data and documentation a symbol can be attached to. It is the model side (what an object is, what goes in and out of it), not the front side (how it looks).

The documentation of Metadata is written in one file per theme. The first theme is the data model, its schema first.

## What it contains

| File | What it holds |
| --- | --- |
| [Data model](data-model.md) | The whole schema of Metadata, the table of its entities with the file each one is kept in, and the types of the fields. |
| [Files](files.md) | The rules every file of Metadata follows: the `format_version` key, how the schema becomes JSON, the order of the keys, the names of the files and what each file holds. |
| [Formulas](formulas.md) | How the two formulas of a conversion are written and computed: what a formula holds, priorities, refused forms, grammar, precision, computing without `eval`, out of domain, checks of the catalogue. From research T6 (decisions 0076, 0077). |
| [Inheritance of types](inheritance.md) | What a sub-type takes from its parents, what it may change, the order of the inherited lines, and what happens when a parent changes or is missing. |
| [Deleting and its consequences](deleting.md) | What can be deleted in Metadata, how, and what happens to what points to the deleted thing, in Metadata, in the signal settings, the faceplates and the symbols. |
| [Identity and renaming](identity-and-renaming.md) | How each thing is known: `internal_id` and `id`, the key of each entity and where it is unique, what a rename changes in the software and breaks outside it. |
| [Checks and errors](checks-and-errors.md) | What the software checks in Metadata, when, and what each check gives: a change refused, a thing flagged in error, a mark in place of a value, or nothing. |
| [Units on screen](units-on-screen.md) | In which unit a number is kept, shown, typed and sent to the model: default, display and model unit, a value or a difference, the decimals, the rounding, the Units page. |
| [Documentation plan](documentation-plan.md) | The kinds of documents of Metadata (data model, entities, topics, catalogues, screens, journeys...), those written and those missing. |
| [Entities](entities/README.md) | One file per entity (a box of the schema), written whole: its box and the JSON Schema of its file. Every box of the data model has one since 2026-11-22. |
| [Data model: notes](data-model-notes.md) | Everything written around the schema from 2026-11-19 to 2026-11-21: the rules of the names, the faceplate box by box, the writing rules of the entity files, notes for the development, the reading notes by date and the open questions. |
| [Whole draft](draft.md) | Every page written up to 2026-11-18, gathered in one file, content unchanged: types, icons, documentation, signals, units, enums, commands, presets (removed since, 2026-11-24), editing without versions, flags, identifiers, the first data model, who changes what, open questions. The source of the final pages, until each theme replaces its part. |

## See also

- [Glossary](../overview/glossary.md): each word of the specification, Metadata's first, its one meaning and the words not to use for it.

- [Storage](../storage/README.md): how the files that types generate are saved.
- [Screens of Metadata](../screens/metadata.md): every screen of this part, with its buttons, fields and lists, and what is missing.
