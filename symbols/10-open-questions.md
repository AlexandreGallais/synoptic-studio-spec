# Symbols: open questions

> [Home](../README.md) › [Symbols](README.md) › Open questions · Previous: [Run mode](09-run-mode/README.md) · Next: [Enums of a Symbol Lib](11-enums-of-a-symbol-lib.md)

Status: draft. Everything in this part is still a draft: these are the questions raised while writing it. Both researches are back (2026-11-11): their answers and opinions are in the pages; what is left is for the Product Owner to decide.

This file is the index of the open questions. A question sits in the file it concerns and is listed here; once answered, it is removed from both and the answer goes in the rules.

## To decide by the Product Owner, after the researches

| Question | Page | Opinion of the research |
| --- | --- | --- |
| Names: Advanced tools, Path, Interaction zone, Preview, Test mode; Layer kept. (Static and dynamic: dropped, one kind of symbol, 2026-11-15.) | [Editor](03-editor/README.md) | Those names. |
| Rotation as the only transform of a shape; frame of a symbol; minimum snapping and guides; editor data in one `<metadata>` block; missing features to add now. | [Editor](03-editor/README.md) | See the page. |
| Desktop window; does "all in JavaScript" allow a shell in Rust? Browsers to hold at 8.3 ms; which effects go in the specs (two lots?); effect suspended during a gesture; colour filter or recomputed colours. | [Effects and masks](04-drawing-mode/effects-and-masks.md) | Electron, and the installed web app first; two lots of effects. |
| Open paths (middle only, caps, joins); native stroke for a plain "middle" border or every border computed; dashes of shape borders computed like pipes; named colours and a "high-performance" palette. (Dash sequences of coloured segments: decided 2026-11-11.) | [Fill and border](04-drawing-mode/fill-and-border.md) | Yes to open paths and colours. |
| OFL fonts embedded whole; text border kept. | [Text tool](04-drawing-mode/text.md) | Yes. |
| Third polygon mode "like Figma"; anchors on corners reserved to 3 and 4 sides or another meaning. | [Polygon](04-drawing-mode/polygon.md) | Drop the third mode. |
| Modifier keys (square, from the centre, angle lock). "Entirely enclosed" is settled: Alt. | [Select](03-editor/select.md), [Rectangle](04-drawing-mode/rectangle.md), [Pen](04-drawing-mode/pen.md) | Conventions written; key conflicts not researched. |
| Free form: options of the former shape; points list. | [Point editing mode](05-point-editing-mode/README.md) | Drop the options of the former shape; list the selected shapes. |
| Anchors on a real shape; distribution with equal spacing; one anchor for all the shapes to place or one each. | [Alignment mode](06-alignment-mode/README.md), [Anchors](03-editor/anchors.md) | Centre plus eight points on the outline; add the distribution. |
| Boolean operations and duplication rules. | [Boolean operations](03-editor/expert-menu/boolean-operations.md), [Placement and duplication](03-editor/expert-menu/placement-and-duplication.md) | Four operations; polar, along a path, grid. |
| Gesture list; names Interaction, Gesture, Effect; feedback, "disabled when", confirmation, keyboard. | [Interaction mode](07-interaction-mode/README.md) | Short list; those names; write them here. |
| Animatable properties, shapes of mapping, blinking bounded, quality of a value, number format. (Enum: the columns of the Symbol Lib replace the state table, 2026-11-17.) | [Animation mode](08-animation-mode/README.md) | See the page. |
| Where the Enums page of a Symbol Lib opens from; kinds of value of a column; values of the columns of a template; an item without value; a deleted column; a value or a named colour. | [Enums of a Symbol Lib](11-enums-of-a-symbol-lib.md) | Not researched (2026-11-17). |
| **Text that becomes an input: HTML field laid over the text instead of a `foreignObject`.** The text writes an input signal directly, without a command (decision 0014). | [Animation mode](08-animation-mode/README.md) | HTML field over the text: proposed in decision 0006, settled after POC P12. |
| Do the signals carry a quality in the contract with the model? | [Animation mode](08-animation-mode/README.md) | Yes, shown by default. |
| Name "Test mode"; form of the simulation log and of the simulated faceplate; the signals used as bounds of an animation listed with the test values. | [Run mode](09-run-mode/README.md) | Test mode; a log line: time, place, gesture, effect, value; bound signals listed, inputs included. |
| A bound of a bounded linear animation typed as a number, besides a signal in or out. | [Animation mode](08-animation-mode/README.md#the-input-range-of-a-bounded-linear-animation) | Yes: assistant's reading of the Product Owner's words (2026-11-17). |
| A branch as one pipe or two; a type of Metadata for a pipe; path kind per pipe. (Junctions, crossings and ends inside the pipe style; symbol connected to a pipe: decided 2026-11-11.) | [Pipes](pipes/README.md) | One pipe; yes, three signals. |
| Symbol connected to a pipe: which symbols, pipe cut under it or not, how its position is kept, what happens when the pipe changes. | [Pipes in the synoptic](pipes/in-the-synoptic.md) | Two connection points, pipe continuous under it (archived Figma page). |
| Properties a signal can drive on a pipe style; a type on the base style; a branch with its own values and propagation; global stop and "reduce motion"; path kind per pipe. (Base style with overrides, dash sequences, computed dashes, moving dashes with a direction, propagation at junctions, optional type on a pipe style: decided 2026-11-11.) | [Pipe styles](pipes/pipe-styles.md) | Global stop and "reduce motion": yes. |
| Size of bridges and gaps; default "last drawn on top"; borders on a bridge. | [Crossings](pipes/crossings.md) | Size in the style; last drawn on top. |
| Four or nine anchors on an end shape; copy an end shape from another style; arrows of a symbol's lines. | [Pipe ends](pipes/ends.md) | Not settled by the report. |

## Raised by the review of 2026-11-15

| Question | Page | Proposal of the assistant |
| --- | --- | --- |
| Thumbnail of a symbol in the list: the symbol itself, or its outlines only; what else an item shows. | [Libraries and symbols](01-libraries-and-symbols.md) | Outlines only, as Figma's outline view, with the name. |
| Look of the Interaction, Animation and Run modes before a type is chosen. | [Libraries and symbols](01-libraries-and-symbols.md) | Greyed in the mode menu, with a tooltip "choose a type first". |
| Place of the base pipe style. | [Libraries and symbols](01-libraries-and-symbols.md) | First item of the pipe styles list. |
| Place of the floating tool bar: bottom or top of the drawing area. | [Editor](03-editor/README.md) | Bottom, centred (the Product Owner's leaning). |
| Key and ratio of the precise move; does it also apply to whole shapes. | [Precise move](03-editor/precise-move.md) | See the page. |
| What a line of the layer tree shows besides its name (lock, hide, icon of its kind). | [Layers](03-editor/layers.md) | Icon of the kind, name, hide, lock. |

## Raised by the review of 2026-11-16

| Question | Page | Proposal of the assistant |
| --- | --- | --- |
| How a Symbol Lib looks in the navigation bar (the bar itself is decided: Libraries button, separator, every Symbol Lib). | [Libraries and symbols](01-libraries-and-symbols.md) | Initials in a square, the name on hover. |
| Type choice among all the types: how it stays quick when the tree grows. | [Libraries and symbols](01-libraries-and-symbols.md) | A tree with a search field, as in Metadata. |

## Still open, not researched

| Question | Page | Written as |
| --- | --- | --- |
| Key conflicts (Alt and the Linux window managers, Ctrl+G in browsers). | [Editor](03-editor/README.md) | Not found by the research. |
| What can be taken from the symbol standards (ISA-5.1, ISO 14617, EN 60617, ISO 10628) without a copyright problem. | [Pipes](pipes/README.md) | Paid standards, not opened. |
| Options of each entry of the advanced tools, of the alignment panel and of the group (anchors, placement of the children). | [Advanced tools](03-editor/expert-menu/README.md), [Alignment mode](06-alignment-mode/README.md), [Group](04-drawing-mode/group.md) | To describe, page by page. |
| Connection points: which mode places them, their names, the snapping zone. | [Connection points](pipes/connection-points.md) | To describe. |
| What the faceplate opened by an interaction allows once the symbol is placed (display only, or display with commands). | Part 3 | Belongs to the synoptic part, not written yet. |
| How are an unwired symbol with a type, a placed symbol (linked instance) and its scale handled in a synoptic? | Part 3 | Belongs to the synoptic part, not written yet. |

```mermaid
flowchart LR
    Q["An open question"] -->|"sits in"| F["The page it concerns"]
    Q -->|"is listed in"| I["This index"]
    A["Answered"] -->|"removed from both, answer written in the page's rules"| F
```
