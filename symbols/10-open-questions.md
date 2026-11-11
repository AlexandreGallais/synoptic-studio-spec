# Symbols: open questions

> [Home](../README.md) › [Symbols](README.md) › Open questions · Previous: [Run mode](09-run-mode/README.md)

Status: draft. Everything in this part is still a draft: these are the questions raised while writing it.

This file is the index of the open questions. A question sits in the file it concerns and is listed here; once answered, it is removed from both and the answer goes in the rules.

| Question | Page | Written as |
| --- | --- | --- |
| Names to review: layer, interaction, gesture (left click, right click...), zone, symbol mode, static and dynamic. "Symbol Lib" and "Type Lib" are settled. Metadata already uses "trigger" for a kind of command: a gesture must not be confused with it. | All | A research on the vocabulary can be done, as for Metadata. |
| Desktop window (embedded Chromium or system view) and browsers to hold at 8.3 ms; which effects go in the specs (two lots?); effect suspended during a gesture; colour filter or recomputed colours. | [Effects and masks](04-drawing-mode/effects-and-masks.md) | The research report is back; the Product Owner decides. |
| Dashes of a fill-based border: hidden stroke or computed dashes. | [Fill and border](04-drawing-mode/fill-and-border.md) | To decide. |
| Third polygon mode "like Figma" (the report advises dropping it); anchors on corners reserved to 3 and 4 sides or another meaning. | [Polygon](04-drawing-mode/polygon.md) | To decide. |
| Modifier keys (square, from the centre, angle lock). Rule: only keys that exist on every platform. "Entirely enclosed" is settled: Alt. | [Select](03-editor/select.md), [Rectangle](04-drawing-mode/rectangle.md), [Pen](04-drawing-mode/pen.md) | The conventions are written; the Product Owner chooses. |
| Point editing: options of the former shape once it becomes a free form (corner radius, sides...); list of points in the panel: all shapes or the selected ones. | [Point editing mode](05-point-editing-mode/README.md) | To confirm. |
| Fonts research (question 5 of the brief). | [Research brief](research-brief.md) | Not sent yet. |
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
