# entities

> [Home](../../README.md) › [Metadata](../README.md) › Entities

The entities of Metadata, one file each, written whole. An entity is a kind of thing Metadata keeps, with its own identity: a box of the [Data model](../data-model.md). Its file says what the entity is, shows its box, the JSON Schema of the entity and the JSON Schema of the file that holds it. Each file describes the structure every thing of that kind follows, never one thing in particular. Started on 2026-11-21 at the Product Owner's request, under the name `objects/`; renamed `entities/` the same day at their request.

## How an entity file is written

Settled with the Product Owner on 2026-11-21, on the file [Designation](01-designation.md) (then named Identifier), whose plan was validated that day as the model of every entity file (its text is not validated yet):

- **Every entity file follows [Designation](01-designation.md) exactly**: the same sections, the same tables, the same two schemas, nothing added.
- **Short texts**: the introduction in a few sentences, each field's `description` in one or two; never what the JSON Schema already says by a keyword (`required`, `minLength`, `default`).
- **The Product Owner validates each entity file, one by one**, its structure and its text ("je te valide la structuration de toutes les entités à chaque fois").
- **The same sections, in the same order**: the title and its breadcrumb; the table of versions; the table of tags; a short introduction that says what the entity is; **The entity** (the schema, then the JSON Schema of the entity; no table of the fields, which would repeat the JSON Schema); **The file** (its JSON Schema only, no text, no example); **Open questions**, only when one is left. No status sentence, no **Where it is used** (the pages that use an entity link to it; the whole picture is the [Data model](../data-model.md)), no **Product Owner context**.
- **The table of versions** has four columns: `Version`, `Date`, `Status`, `Change`. Each line is one version of the file, and its `Status` is that version's own: `Draft`, then `Validated` on the same line once the Product Owner validates it. These two statuses only: no "in review" step while only the Product Owner and the assistant work on the specs.
  - **Never two lines while one is `Draft`**: as long as the last version is `Draft`, every change stays in that version; no line is added.
  - **Version 1 says only "Creation of the file"**, nothing else: the changes made while it is `Draft` are never listed. Validating never adds a line.
  - Only a change made after a validation adds a line: the next version, `Draft`, whose `Change` cell lists every change made since the last validation, until it is validated in turn.
  - The `Status` column of [What it contains](#what-it-contains) repeats the status of each file's last version, changed in the same session.
- **The table of tags** has two columns, `Tag` and `Value`: `File`, with the file's name, when the entity has a file of its own.
- **A part is numbered just before the entity that has or holds it** (Product Owner, 2026-11-22): Enum item before Enum, Value type before Signal, Command target before Command.
- **An entity kept inside another one's file** (a [Color](02-color.md), in its [Palette](03-palette.md)) has no table of tags and no section **The file**: its introduction says where it is kept, and the file is described on the entity that has it.
- **Two JSON Schemas**: the entity's (`$id`: its name, then `.schema.json`, as `designation.schema.json`) and the file's, which refers to the entity's by its `$id` and never repeats its fields. The file's `$id` is the file's name with `.schema.json` (`designations.schema.json`) when the file holds the whole list; the entity's name with `-file.schema.json` (`palette-file.schema.json`) when there is one file per thing.
- **The JSON Schema says every rule it can**: a text never empty (`minLength: 1`), a default (`default`), a field set by the software (`readOnly`). What it cannot say (a primary key, a uniqueness) goes in the field's `description`.
- **The schema shows only the structure**: for each field its type, its name and its key (`PK`, `FK`), nothing else. Mermaid accepts only `PK`, `FK` and `UK` as keys, so the constraints go in the JSON Schema.
  - **No comment on a field**, not even when it exists in some cases only: the JSON Schema already says it.
  - **The schema draws the entity and the entities it has or holds**: a FK to an entity kept outside it (an enum, a quantity) is only its column, with no box nor link for that entity; the whole picture is the [Data model](../data-model.md).
- **Each field is described once, in the JSON Schema**: its `description` says what the field is for the user and what must be respected about it, in one or two sentences, never what everyone knows already (what a primary key does) nor a rule that belongs to another page (what a faceplate shows). Arsenal draws the JSON Schema as a tree of the fields, so no table repeats it.
- **The boxes of the [Data model](../data-model.md) follow the same rule** (Product Owner, 2026-11-22): type, name and key only, no comment, so that each box reads exactly as the schema of its entity file. Each entity file written or changed brings its box in the data model to it in the same session.
- **In the [Data model](../data-model.md), only the title of the entity's box is coloured**, by a rule in the `themeCSS` line at the top of the diagram (`[id*='entity-NAME-'] .outer-path path`), never by a `style` line, which colours every other row.
- **What holds for every file is never written on an entity** (the `format_version` key, the names of the lists, the order of the keys): it is in [Files](../files.md).
- **The body says only what must be respected**: no history of the discussion, no "no display name", no quote, no "chosen by", no order of size, no reason already given by a field's description.
- No sentence that only counts the fields ("three fields, nothing else"): the schema already shows them.
- **Figma follows later**: a change made while the text is validated is not redrawn in Figma at once; the screens are gone over once the text is validated (Product Owner, 2026-11-21: "le but de là, c'est de valider le texte, et ensuite on repassera sur Figma").

## What it contains

| File | What it holds | Status |
| --- | --- | --- |
| [Designation](01-designation.md) | What identifies the equipment of a placed symbol, such as its tag or its location. | Draft |
| [Color](02-color.md) | One color of a palette, picked for the appearance of a type. | Draft |
| [Palette](03-palette.md) | A set of colors: the only colors a type can pick. | Draft |
| [Enum item](04-enum-item.md) | One value of an enum: the number the model receives and the name people read. | Draft |
| [Enum](05-enum.md) | A named list of items, picked by a signal whose value is an enum. | Draft |
| [Icon](06-icon.md) | One drawing of an icon set, picked for the appearance of a type. | Draft |
| [Icon set](07-icon-set.md) | A set of icons of one style or one origin: the icons a type can pick. | Draft |
| [Flag](08-flag.md) | A key each placed symbol of a type has on or off, written in the configuration files for a program outside. | Draft |
| [Link entity](09-link.md) | A path to a file or a folder, or a URL, in the documentation of a type. | Draft |
| [Documentation](10-documentation.md) | What explains a type to people: a description in Markdown and links. | Draft |
| [Conversion](11-conversion.md) | The two formulas that turn a value of a unit into the default unit of its quantity, and back. | Draft |
| [Unit](12-unit.md) | One way to count a quantity, with its name, its symbol and its conversion. | Draft |
| [Unit system](13-unit-system.md) | The units of a quantity that belong to one system, such as metric or imperial. | Draft |
| [Quantity](14-quantity.md) | What a value measures, with its default unit and its unit systems; one file each. | Draft |
| [Value type](15-value-type.md) | What kind of value a signal holds, and for a number, the quantity it measures. | Draft |
| [Signal](16-signal.md) | A value that goes between the front and the model, as an input or an output. | Draft |
| [Command target](17-command-target.md) | The signal a command sends its value to, and that fixed value. | Draft |
| [Command](18-command.md) | What the front sends with one click: a fixed value to an input, an override of an output, or a trigger for the layer above the model. | Draft |
| [Appearance](19-appearance.md) | The icon and the color a type shows, copied when picked; null, those of its parent. | Draft |
| [Display format](20-display-format.md) | The unit and the decimals a preset shows an integer or a real with. | Draft |
| [Boolean texts](21-boolean-texts.md) | The words a preset shows for true and for false. | Draft |
| [Preset value](22-preset-value.md) | How a preset starts and shows one signal: its start value, and its display format or its boolean texts. | Draft |
