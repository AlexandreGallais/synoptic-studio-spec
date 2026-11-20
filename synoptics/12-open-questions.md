# Open questions

> [Home](../README.md) › [Synoptics](README.md) › Open questions · Previous: [Data model](11-data-model.md)

Status: written by the assistant on 2026-11-20, with the extrapolation of this part. Each question gives the option the assistant advises, never a decision. The Product Owner settles them at the review of the part.

## The most structuring

These change the data model; to settle first.

| # | Question | Advised | Page |
| --- | --- | --- | --- |
| 1 | Is a summary view a synoptic whose placed symbols **reference** those of an installation, a plain copy, or a view stored in the installation file? | References: `P-101` is wired once. | [Synoptics and views](01-synoptics-and-views.md#open-questions) |
| 2 | Does a placed symbol have an **instance ID** of its own, or is one identifier (the tag) its key? | An instance ID of its own; its name waits for task T5. | [Panel of a placed symbol](04-placed-symbol-panel.md#open-questions) |
| 3 | What may a synoptic change in the preset of a placed symbol: only the faceplate texts, or also the default values, units and decimals? The draft of Metadata says both. | Both, kept as changes from the preset, with a reset. | [Panel of a placed symbol](04-placed-symbol-panel.md#preset) |
| 4 | A **branch**: two pipes, or one pipe as a tree? (Already asked in Pipes.) | One pipe as a tree, as the research advised. | [Pipes](05-pipes.md#branches) |
| 5 | Does the runtime read the synoptic file, or a **published view**? | A published view, self-contained. | [Outputs](10-outputs.md#open-questions) |

## The others

| # | Question | Advised | Page |
| --- | --- | --- | --- |
| 6 | A fixed frame (a target screen) or an infinite canvas? | A fixed frame. | [Synoptics and views](01-synoptics-and-views.md#open-questions) |
| 7 | Can a synoptic change kind (installation, view)? | No at first. | [Synoptics and views](01-synoptics-and-views.md#open-questions) |
| 8 | One installation per folder, or several? | Several (one per building). | [Synoptics and views](01-synoptics-and-views.md#open-questions) |
| 9 | Names of the modes: Build, Pipes, Annotate, Links, Test. | Working names, to review. | [Synoptic editor](02-synoptic-editor.md#open-questions) |
| 10 | The Library: a panel on the left or a floating window? | A panel on the left, above the objects. | [Synoptic editor](02-synoptic-editor.md#open-questions) |
| 11 | May Replace offer a symbol of a sub-type? | No: the type of a placed symbol never changes. | [Placed symbols](03-placed-symbols.md#open-questions) |
| 12 | Do borders grow with the size of a placed symbol? | No: they keep their width. | [Placed symbols](03-placed-symbols.md#open-questions) |
| 13 | Texts of a placed symbol turned by 180°: the right way up? | Yes. | [Placed symbols](03-placed-symbols.md#open-questions) |
| 14 | Changing the Symbol Lib: matched by name then type, or by an identifier of each symbol? | By name then type, corrected in a table. | [Placed symbols](03-placed-symbols.md#changing-the-symbol-lib-of-a-synoptic) |
| 15 | Identifiers shown in the panel: only those used by the preset, or all? | Only those used. | [Panel of a placed symbol](04-placed-symbol-panel.md#identity) |
| 16 | A duplicate identifier text: a warning or refused? | A warning. | [Faults](08-faults.md#what-puts-something-in-fault) |
| 17 | A symbol on a pipe: follows the bends, or stays on one segment? | Stays on one segment. | [Pipes](05-pipes.md#symbols-on-a-pipe) |
| 18 | Pipe styles offered when several Symbol Libs are used. | All, grouped by library. | [Pipes](05-pipes.md#open-questions) |
| 19 | Images in a synoptic, and in which format? | SVG only at first. | [Annotations](06-annotations.md#open-questions) |
| 20 | A link on a placed symbol whose symbol already reacts to a click. | Not allowed; a link zone is drawn over it instead. | [Navigation links](07-navigation-links.md#open-questions) |
| 21 | "Back": a link drawn by the user or a button of the runtime? | A button of the runtime. | [Navigation links](07-navigation-links.md#open-questions) |
| 22 | Publishing with errors. | Allowed after a warning. | [Faults](08-faults.md#open-questions) |
| 23 | Is "unwired" an information worth showing? | Yes, hidden by default. | [Faults](08-faults.md#open-questions) |
| 24 | Scenarios of the Test mode: in the synoptic file or apart? | In the synoptic file. | [Test mode](09-test-mode.md#open-questions) |
| 25 | Format of the connection graph: the project's own, or SSP? | The project's own first; SSP to study. | [Outputs](10-outputs.md#open-questions) |
| 26 | The address of a signal: on the instance ID or on the tag? | On the instance ID. | [Outputs](10-outputs.md#the-address-of-a-signal) |
| 27 | A pipe whose style is linked to a type: does a branch have its own values? (Already asked in Pipes.) | Its own values. | [Pipes](05-pipes.md#a-pipe-whose-style-is-linked-to-a-type) |
