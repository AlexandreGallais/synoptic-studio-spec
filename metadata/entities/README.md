# entities

> [Home](../../README.md) › [Metadata](../README.md) › Entities

The entities of Metadata, one file each, written whole. An entity is a kind of thing Metadata keeps, with its own identity: a box of the [Data model](../data-model.md). Its file says what the entity is, shows its box, the JSON Schema of the entity and the JSON Schema of the file that holds it. Each file describes the structure every thing of that kind follows, never one thing in particular. Started on 2026-11-21 at the Product Owner's request, under the name `objects/`; renamed `entities/` the same day at their request.

## How an entity file is written

Settled with the Product Owner on 2026-11-21, on the file [Identifier](01-identifier.md):

- **The Product Owner validates each entity file, one by one**, its structure and its text ("je te valide la structuration de toutes les entités à chaque fois").
- **The same sections, in the same order**: the title and its breadcrumb; the table of versions; the table of tags; a short introduction that says what the entity is; **The entity** (the schema, the table of its fields, then the JSON Schema of the entity); **The file** (its JSON Schema only, no text, no example); **Open questions**, only when one is left (the names wait for the research on the terms). No status sentence, no **Where it is used** (the pages that use an entity link to it; the whole picture is the [Data model](../data-model.md)), no **Product Owner context**.
- **The table of versions** has four columns: `Version`, `Date`, `Status`, `Change`. The first line is version 1, `Draft`, "Creation of the file"; each later change adds a line. The status stays `Draft` until the Product Owner validates the file.
- **The table of tags** has two columns, `Tag` and `Value`: `File`, with the file's name, when the entity has a file of its own.
- **Two JSON Schemas**: the entity's (`$id`: its name, then `.schema.json`, as `identifier.schema.json`) and the file's (`$id`: the file's name with `.schema.json`, as `identifiers.schema.json`), whose list refers to the entity's by its `$id` and never repeats its fields.
- **The JSON Schema says every rule it can**: a text never empty (`minLength: 1`), a default (`default`), a field set by the software (`readOnly`). What it cannot say (a primary key, a uniqueness) goes in the field's `description`.
- **The schema shows only the structure**: for each field its type, its name and its key (`PK`, `FK`), nothing else. Mermaid draws only these columns and a comment, and accepts only `PK`, `FK` and `UK` as keys, so the constraints go in the table below.
- **The table has four columns**: `Field`, `Required` (`✓` when required, a `PK` included; empty otherwise), `Default` (the bare value, such as `false`, empty when there is none), `What it is`: what the field is for the user and what must be respected about it, in one or two sentences, never what everyone knows already (what a primary key does) nor a rule that belongs to another page (what a faceplate shows).
- **In the [Data model](../data-model.md), only the title of the entity's box is coloured**, by a rule in the `themeCSS` line at the top of the diagram (`[id*='entity-NAME-'] .outer-path path`), never by a `style` line, which colours every other row.
- **What holds for every file is never written on an entity** (the `format` key, the names of the lists, the order of the keys): it is in [Files](../files.md).
- **The body says only what must be respected**: no history of the discussion, no "no display name", no quote, no "chosen by", no order of size, no reason already given by a field's description.
- No sentence that only counts the fields ("three fields, nothing else"): the schema already shows them.
- **Figma follows later**: a change made while the text is validated is not redrawn in Figma at once; the screens are gone over once the text is validated (Product Owner, 2026-11-21: "le but de là, c'est de valider le texte, et ensuite on repassera sur Figma").

## What it contains

| File | What it holds |
| --- | --- |
| [Identifier](01-identifier.md) | A named key that each placed symbol fills with its own text; global, all in one file. |
