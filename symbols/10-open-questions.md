# Symbols: open questions

> [Home](../README.md) › [Symbols](README.md) › Open questions · Previous: [Run mode](09-run-mode/README.md)

Status: draft. Everything in this part is still a draft: these are the questions raised while writing it.

This file is the index of the open questions. A question sits in the file it concerns and is listed here; once answered, it is removed from both and the answer goes in the rules.

| Question | Page | Written as |
| --- | --- | --- |
| Names to review: layer, interaction, gesture (left click, right click...), zone, symbol mode, static and dynamic. "Symbol Lib" and "Type Lib" are settled. Metadata already uses "trigger" for a kind of command: a gesture must not be confused with it. | All | A research on the vocabulary can be done, as for Metadata. |
| Everything left to the documentary research: which SVG effects keep the performance, how a polygon is placed in its box (and a "like Figma" mode), the names of the handle mirroring modes, the modifier keys. | [Research brief](research-brief.md) | One research, launched at the end when the Product Owner says so. No task before. |
| Options of each expert entry, of the alignment panel and of the group (anchors, placement of the children). | [Expert menu](03-editor/expert-menu/README.md), [Alignment mode](06-alignment-mode/README.md), [Group](04-drawing-mode/group.md) | To describe, page by page. |
| Properties an animation can drive, shape of the mapping (linear or not), animation of an enum. | [Animation mode](08-animation-mode/README.md) | To describe. |
| Can a text that shows a value become an input on click, from the symbol editor? | [Animation mode](08-animation-mode/README.md) | To confirm. |
| Gesture list, and can an interaction open the faceplate? | [Interaction mode](07-interaction-mode/README.md) | To settle. |
| Do interactions work in the Run mode? | [Run mode](09-run-mode/README.md) | Open. |
| How are an unwired dynamic symbol and the placement in a synoptic handled? | Part 3 | Belongs to the synoptic part, not written yet. |

```mermaid
flowchart LR
    Q["An open question"] -->|"sits in"| F["The page it concerns"]
    Q -->|"is listed in"| I["This index"]
    A["Answered"] -->|"removed from both, answer written in the page's rules"| F
```
