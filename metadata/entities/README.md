# entities

> [Home](../../README.md) › [Metadata](../README.md) › Entities

The entities of Metadata, one file each, written whole. An entity is a kind of thing Metadata keeps, with its own identity: a box of the [Data model](../data-model.md). Its file says what the entity is, shows its box, the JSON Schema of the entity and the JSON Schema of the file that holds it. Each file describes the structure every thing of that kind follows, never one thing in particular. Started on 2026-11-21 at the Product Owner's request, under the name `objects/`; renamed `entities/` the same day at their request.

## How an entity file is written

Settled with the Product Owner on 2026-11-21, on the file [Designation](01-designation.md) (then named Identifier), whose plan was validated that day as the model of every entity file (its text is not validated yet):

- **Every entity file follows [Designation](01-designation.md) exactly**: the same sections, the same tables, the same two schemas, nothing added.
- **Short texts**: the introduction in a few sentences, each `What it is` in one or two; never what a column or a schema already says (a `✓` in `Required`, a `minLength`).
- **The Product Owner validates each entity file, one by one**, its structure and its text ("je te valide la structuration de toutes les entités à chaque fois").
- **The same sections, in the same order**: the title and its breadcrumb; the table of versions; the table of tags; a short introduction that says what the entity is; **The entity** (the schema, the table of its fields, then the JSON Schema of the entity); **The file** (its JSON Schema only, no text, no example); **Open questions**, only when one is left. No status sentence, no **Where it is used** (the pages that use an entity link to it; the whole picture is the [Data model](../data-model.md)), no **Product Owner context**.
- **The table of versions** has four columns: `Version`, `Date`, `Status`, `Change`. Each line is one version of the file, and its `Status` is that version's own: `Draft`, then `Validated` on the same line once the Product Owner validates it. These two statuses only: no "in review" step while only the Product Owner and the assistant work on the specs.
  - **Never two lines while one is `Draft`**: as long as the last version is `Draft`, every change stays in that version; no line is added.
  - **Version 1 says only "Creation of the file"**, nothing else: the changes made while it is `Draft` are never listed. Validating never adds a line.
  - Only a change made after a validation adds a line: the next version, `Draft`, whose `Change` cell lists every change made since the last validation, until it is validated in turn.
  - The `Status` column of [What it contains](#what-it-contains) repeats the status of each file's last version, changed in the same session.
- **The table of tags** has two columns, `Tag` and `Value`: `File`, with the file's name, when the entity has a file of its own.
- **Two JSON Schemas**: the entity's (`$id`: its name, then `.schema.json`, as `designation.schema.json`) and the file's (`$id`: the file's name with `.schema.json`, as `designations.schema.json`), whose list refers to the entity's by its `$id` and never repeats its fields.
- **The JSON Schema says every rule it can**: a text never empty (`minLength: 1`), a default (`default`), a field set by the software (`readOnly`). What it cannot say (a primary key, a uniqueness) goes in the field's `description`.
- **The schema shows only the structure**: for each field its type, its name and its key (`PK`, `FK`), nothing else. Mermaid draws only these columns and a comment, and accepts only `PK`, `FK` and `UK` as keys, so the constraints go in the table below.
- **The table has four columns**: `Field`, `Required` (`✓` when required, a `PK` included; empty otherwise), `Default` (the bare value, such as `false`, empty when there is none), `What it is`: what the field is for the user and what must be respected about it, in one or two sentences, never what everyone knows already (what a primary key does) nor a rule that belongs to another page (what a faceplate shows).
- **In the [Data model](../data-model.md), only the title of the entity's box is coloured**, by a rule in the `themeCSS` line at the top of the diagram (`[id*='entity-NAME-'] .outer-path path`), never by a `style` line, which colours every other row.
- **What holds for every file is never written on an entity** (the `format_version` key, the names of the lists, the order of the keys): it is in [Files](../files.md).
- **The body says only what must be respected**: no history of the discussion, no "no display name", no quote, no "chosen by", no order of size, no reason already given by a field's description.
- No sentence that only counts the fields ("three fields, nothing else"): the schema already shows them.
- **Figma follows later**: a change made while the text is validated is not redrawn in Figma at once; the screens are gone over once the text is validated (Product Owner, 2026-11-21: "le but de là, c'est de valider le texte, et ensuite on repassera sur Figma").

## What it contains

| File | What it holds | Status |
| --- | --- | --- |
| [Designation](01-designation.md) | What identifies the equipment of a placed symbol (its tag, its location): defined once, its text written on each placed symbol; all in one file. | Draft |
