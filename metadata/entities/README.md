# entities

> [Home](../../README.md) › [Metadata](../README.md) › Entities

The entities of Metadata, one file each, written whole. An entity is a kind of thing Metadata keeps, with its own identity: a box of the [Data model](../data-model.md). Its file says what the entity is, shows its box, its JSON and the JSON Schema of the file that holds it. Each file describes the structure every thing of that kind follows, never one thing in particular. Started on 2026-11-21 at the Product Owner's request, under the name `objects/`; renamed `entities/` the same day at their request.

## How an entity file is written

Settled with the Product Owner on 2026-11-21, on the file [Identifier](01-identifier.md):

- **The Product Owner validates each entity file, one by one**, its structure and its text ("je te valide la structuration de toutes les entités à chaque fois").
- **The same sections, in the same order**: the title and its breadcrumb; the status; a short introduction that says what the entity is; **The entity** (the schema, then the table of its fields); the rules; **The file** (its example, its JSON Schema); **Where it is used**; **Open questions**.
- **The schema shows only the structure**: for each field its type, its name, its key (`PK`, `FK`), and in its comment whether it is required or optional and its default value (`required, default false`, `required, generated`, `optional, no default`). What a field means goes in the table below it, never in the schema (Product Owner: "vu qu'il y a un tableau juste en dessous, c'est à rien").
- No sentence that only counts the fields ("three fields, nothing else"): the schema already shows them.
- **Figma follows later**: a change made while the text is validated is not redrawn in Figma at once; the screens are gone over once the text is validated (Product Owner, 2026-11-21: "le but de là, c'est de valider le texte, et ensuite on repassera sur Figma").

## What it contains

| File | What it holds |
| --- | --- |
| [Identifier](01-identifier.md) | A named key that each placed symbol fills with its own text; global, all in one file. |
