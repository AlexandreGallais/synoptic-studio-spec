# Open questions

> [Home](../README.md) › [Synoptics](README.md) › Open questions · Previous: [Data model](11-data-model.md)

Status: written by the assistant, with the extrapolation of this part. Each question gives the option the assistant advises, never a decision; they are settled at the review of the part. A question settled leaves this list for its page.

## The most structuring

These change the data model; to settle first.

| # | Question | Advised | Page |
| --- | --- | --- | --- |
| 1 | A pipe that **ends on another pipe** of another style: a branch of that pipe (it takes its style), or two pipes that meet? (A pipe is one tree, decided.) | Two pipes that meet: a style is never changed by a click. | [Pipes](05-pipes.md#open-questions) |
| 2 | Does the runtime read the synoptic file, or a **published view**? | A published view, self-contained. | [Outputs](10-outputs.md#open-questions) |

## The others

| # | Question | Advised | Page |
| --- | --- | --- | --- |
| 3 | A fixed frame (a target screen) or an infinite canvas? | A fixed frame. | [Synoptics and views](01-synoptics-and-views.md#open-questions) |
| 4 | Can a synoptic change kind (installation, view)? | No at first. | [Synoptics and views](01-synoptics-and-views.md#open-questions) |
| 5 | One installation per folder, or several? | Several (one per building). | [Synoptics and views](01-synoptics-and-views.md#open-questions) |
| 6 | Names of the modes: Build, Pipes, Annotate, Links, Test. | Working names, to review. | [Synoptic editor](02-synoptic-editor.md#open-questions) |
| 7 | The Library: a panel on the left or a floating window? | A panel on the left, above the objects. | [Synoptic editor](02-synoptic-editor.md#open-questions) |
| 8 | May Replace offer a symbol of a sub-type? | No: the type of a placed symbol never changes. | [Placed symbols](03-placed-symbols.md#open-questions) |
| 9 | Do borders grow with the size of a placed symbol? | No: they keep their width. | [Placed symbols](03-placed-symbols.md#open-questions) |
| 10 | Texts of a placed symbol turned by 180°: the right way up? | Yes. | [Placed symbols](03-placed-symbols.md#open-questions) |
| 11 | Changing the Symbol Lib: matched by name then type, or by an identifier of each symbol? | By name then type, corrected in a table. | [Placed symbols](03-placed-symbols.md#changing-the-symbol-lib-of-a-synoptic) |
| 12 | Designations that are not required, shown in the panel: only those used by the faceplate of the type, or all? | Only those used. | [Panel of a placed symbol](04-placed-symbol-panel.md#identity) |
| 13 | The name of the instance ID. | Not treated by the research T5, which covered Metadata only. | [Panel of a placed symbol](04-placed-symbol-panel.md#identity) |
| 14 | A duplicate designation text: a warning or refused? | A warning. | [Faults](08-faults.md#what-puts-something-in-fault) |
| 15 | A symbol on a pipe: follows the bends, or stays on one segment? | Stays on one segment. | [Pipes](05-pipes.md#symbols-on-a-pipe) |
| 16 | Pipe styles offered when several Symbol Libs are used. | All, grouped by library. | [Pipes](05-pipes.md#open-questions) |
| 17 | Images in a synoptic, and in which format? | SVG only at first. | [Annotations](06-annotations.md#open-questions) |
| 18 | A link on a placed symbol whose symbol already reacts to a click. | Not allowed; a link zone is drawn over it instead. | [Navigation links](07-navigation-links.md#open-questions) |
| 19 | "Back": a link drawn by the user or a button of the runtime? | A button of the runtime. | [Navigation links](07-navigation-links.md#open-questions) |
| 20 | Publishing with errors. | Allowed after a warning. | [Faults](08-faults.md#open-questions) |
| 21 | Is "unwired" an information worth showing? | Yes, hidden by default. | [Faults](08-faults.md#open-questions) |
| 22 | Scenarios of the Test mode: in the synoptic file or apart? | In the synoptic file. | [Test mode](09-test-mode.md#open-questions) |
| 23 | Format of the connection graph: the project's own, or SSP? | The project's own first; SSP to study. | [Outputs](10-outputs.md#open-questions) |
| 24 | A pipe whose style is linked to a type: do its branches share its values, or can a branch have its own? | Shared: the tree is one pipe and one flow. | [Pipes](05-pipes.md#a-pipe-whose-style-is-linked-to-a-type) |
| 25 | Interface description of the models: what makes a signal "needed", per type or per placed symbol, which format? | Per type, a signal needed as soon as one placed symbol of the project uses it; written at Publish. | [Outputs](10-outputs.md#the-interface-description-of-the-models) |

## Left for later

Ideas, not to be asked now.

- **A read-only way in for model authors**: the synoptic views opened without editing, and a click on a placed symbol shows a summary sheet of its type (signals, commands and their descriptions). Whether it is a mode of the application, what the sheet holds, and whether it is in these specs: not described.
