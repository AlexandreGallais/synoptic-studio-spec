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
| Alignment: what an anchor is on a real shape (circle, free form), a gap between shapes, one anchor for all the shapes to place or one each. | [Alignment mode](06-alignment-mode/README.md) | To confirm. |
| Pipes: everything listed at the end of each page of [Pipes](pipes/README.md) (connection points and their mode, pipe styles and their corner radius, junctions, crossings, end shapes, test display, flow dashes), and the Figma page "Flow Pipes", not read yet. | [Pipes](pipes/README.md) | Questions 8 to 11 of the [brief](research-brief.md). |
| The assistant's own questions on the whole symbols part (anchors on real shapes, hit area, free form, points list, faceplate, text as input, keys, missing features...). | All | Question 12 of the [brief](research-brief.md). |
| Fonts research (question 5 of the brief). | [Research brief](research-brief.md) | Not sent yet. |
| Questions added after a full pass (2026-11-11): placed symbols and their updates, broken links and signal quality; frame, scaling, rotation and crisp rendering; borders, caps and joins of open paths; boolean operations, duplication, distribution; named colours and HMI style guides; number formatting and missing values; smooth animation, pivot, blinking; interaction feedback, confirmation, keyboard access; symbol file and SVG export; desktop window. | All | Questions 13 to 22 of the [brief](research-brief.md), for the second research. |
| Options of each expert entry, of the alignment panel and of the group (anchors, placement of the children). | [Expert menu](03-editor/expert-menu/README.md), [Alignment mode](06-alignment-mode/README.md), [Group](04-drawing-mode/group.md) | To describe, page by page. |
| Properties an animation can drive, shape of the mapping (linear or not), animation of an enum. | [Animation mode](08-animation-mode/README.md) | The assistant answers them in its next research (question 7 of the [brief](research-brief.md)), not the Product Owner. |
| Gesture list, and name of the interaction concept. | [Interaction mode](07-interaction-mode/README.md) | The assistant answers them in its next research (question 6 of the [brief](research-brief.md)), not the Product Owner. |
| Form of the simulation log and of the simulated faceplate in the Run mode (the principle is settled: nothing is sent, the action is only shown). | [Run mode](09-run-mode/README.md) | To describe. |
| What the faceplate opened by an interaction allows once the symbol is placed (display only, or display with commands). | Part 3 | Belongs to the synoptic part, not written yet. |
| How are an unwired dynamic symbol and the placement in a synoptic handled? | Part 3 | Belongs to the synoptic part, not written yet. |

```mermaid
flowchart LR
    Q["An open question"] -->|"sits in"| F["The page it concerns"]
    Q -->|"is listed in"| I["This index"]
    A["Answered"] -->|"removed from both, answer written in the page's rules"| F
```
