# Pipes

> [Home](../../README.md) › [Symbols](../README.md) › Pipes · Previous: [Run mode](../09-run-mode/README.md)

Status: draft, with the second research report (`research/t4-…/rapport.md`, which also read the archived Figma page "Flow · Pipes"). Not validated.

Pipes are the lines that connect symbols in a synoptic. The user draws them with a pipe tool, and the editor computes the rest: joints, corners, junctions, crossings. This part of the specs covers what is **created in a library** (the styles) and what the symbol must offer (the connection points). How a pipe is drawn in a synoptic is in [Pipes in the synoptic](in-the-synoptic.md), which belongs to part 3.

## Rules

- A pipe connects the **connection points** of symbols (see [Connection points](connection-points.md)).
- A pipe is drawn with straight segments, by clicking. Everything else is computed.
- What a pipe looks like comes from its **pipe style**, kept in the Symbol Lib, never from options typed on each pipe.
- A Symbol Lib has **one base pipe style**, the shape of all its pipes, without colour. Each **pipe style** (water, oil, steam...) gives the fills of the body and of the border, plain colours or dash sequences, the movement of its dashes through the signals of a linked type, and can have its own body width, such as a smaller width for gas pipes; nothing else of the base changes (see [Pipe styles](pipe-styles.md)).
- The base pipe style and the pipe styles are shown with the same sections, in the same order.
- Dashes, on a body or a border, are a **sequence of coloured segments** (a gap is a transparent segment), computed along the pipe.
- **Junctions and crossings live in the pipe style**, not in separate lists of the Symbol Lib. They are computed, not edited by hand: the user chooses one style for a pipe, and the style says how all of it looks.

| Part of the pipe style | What it sets | Where | Page |
| --- | --- | --- | --- |
| Body and border | Width; border on both sides (width, inside, middle or outside); corner radius, the same for every style. | Base; a pipe style can have its own body width | [Pipe styles](pipe-styles.md) |
| Fills | Body fill and border fill: colour or dash sequence. | Each pipe style | [Pipe styles](pipe-styles.md) |
| Linked type and movement | A type of Metadata, optional; a signal for the direction of the dashes (stopped, forward, backward); the speed, a signal or a fixed value. | Each pipe style | [Pipe styles](pipe-styles.md#moving-dashes) |
| Junctions | Looks of a place where a pipe branches: kind and size; fill and border are the pipe's. | Base | [Junctions](junctions.md) |
| Crossings | What happens where a pipe passes over another: bridge, gap, nothing; the size is computed from the body width. | Base | [Crossings](crossings.md) |
| Start and end shapes | The shapes at the start or at the end of a pipe. | A list of their own, not in the styles | [Pipe ends](ends.md) |

- A Symbol Lib holds one base pipe style and several pipe styles; each library has its own, so that a software or a factory has its own look (same reason as for symbols: see [Libraries and symbols](../01-libraries-and-symbols.md)).
- A pipe is **one pipe, as a tree**: a branch drawn from a pipe belongs to that pipe. The whole tree has one pipe style and one flow (see [Junctions](junctions.md)).
- The look of the angles comes from the **corner radius of the style** only: there is no path kind (straight, right angles, rounded) to choose on each pipe.
- The editor of a pipe style offers a **Preview** with every case a pipe can meet, to see what an edit does (see [Preview](preview.md)).

```mermaid
flowchart LR
    SY["Symbol: connection points"] --> P["Pipe drawn in a synoptic"]
    B["Symbol Lib: base pipe style, shape, junctions, crossings"] --> L["Pipe styles: fills, movement, own width"]
    L --> P
    P --> C["Computed: corners, junctions, crossings, ends"]
    T["Preview in the library editor"] -.->|"shows every case"| L
```

## Everything is computed

The user only gives points and styles. The editor computes: the rounded corners, the junction where a branch leaves, the bridges or gaps at a crossing, the shape of the ends. The user does not edit these results by hand, except by choosing which pipe passes over another (see [Crossings](crossings.md)).

## Example

Base style: 6 px, border 1 px outside, corner radius 8 px, circle junctions, bridges.

| Pipe style | Fills | Movement | Own width |
| --- | --- | --- | --- |
| Water | Body blue; border dark grey | None: no type | — |
| Oil | Body dashes black 10, transparent 20, red 2; border dark grey | Signals of the type `oil_line` | — |
| Steam | Body white; border dashes grey 4, transparent 4 | Signals of the type `steam_line` | — |
| Gas | Body yellow; border dashes black 10, transparent 20, red 2 | Signals of the type `gas_line` | 3 px |
| Electricity | Body yellow; border yellow | None: no type | 2 px |

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Connection points | Symbol editor | Symbol | Create, edit | Pipes snap to them |
| Base pipe style and pipe styles, with junctions and crossings | Symbol Lib | Pipes of a synoptic | Create, edit, test | Choose a pipe style |
| Pipe drawing, junctions, crossings | Synoptic (part 3) | Synoptic | No | Draw, edit |

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.1 to 3.7). Nothing was measured. "Opinion" is the report's provisional opinion, not a decision.

### How other software models pipes

- The software read (draw.io, Visio, Ignition, AutoCAD Plant 3D, JointJS, GoJS, yFiles, libavoid) agree on four objects: a **connection point** with a direction, the **pipe** (or link), the **crossing** ("line jump": arc, gap, square or nothing, with a size), and, less often, the **junction**. Confidence: high.
- Which pipe passes over another is decided by a general rule: the stacking order (draw.io), the orientation (yFiles: horizontal over vertical), or a page setting (Visio). No software read offers the click on a crossing that the project wants: it stays, as an exception to a default rule.
- No colour of content is universal: four colour codes of piping (ASME A13.1, BS 1710, ISO 14726, DIN 2403) disagree on steam, natural gas, nitrogen, acids and oxygen. The rule "the content only names and groups the styles" is consistent with this: the editor holds no colour of content.
- The texts of the symbol standards (ISA-5.1, ISO 14617, EN 60617, ISO 10628) are paid and were not opened: what can be taken from them without a copyright problem stays open.

### The archived Figma page "Flow · Pipes"

An archived inspiration, not a decision. It differs from these pages on several points:

| Subject | Archived Figma page | These specs |
| --- | --- | --- |
| Where junctions, crossings and ends live | Inside the pipe style | Inside the pipe style (decided 2026-11-11, was four separate lists) |
| A branch | The pipe stays one pipe (a tree) | The same: one pipe as a tree (decided 2026-11-23) |
| Anchors of an end shape | Four, at the middle of the sides; one side chosen | Nine (sides and corners) |
| Corner radius | In the style, "for rounded paths"; the path kind (straight, right angles, rounded) is chosen per pipe | In the style only, no path kind per pipe (decided 2026-11-23) |
| Name of the display of every case | Pipe style preview | Preview (decided 2026-11-23) |
| Names | Core, Outline, Line, Part, Plain | Fill, Border, Flow dashes, End shape, Flat |
| Inline symbols | Yes: a symbol with two connection points slides along the pipe | Absent |
| Usage counter | "Used by 38 pipes" | Absent |
| Dashes | A line style (continuous or dashed) | Flow dashes, maybe animated |

### What the others do and this part lacks (opinion of the report)

| Missing | Opinion |
| --- | --- |
| **Inline symbol** placed on a pipe (valve, reducer, flow arrow), sliding along it, bends included | Add: the clearest gap. |
| Size of a bridge or a gap, set in the style | Not taken: computed from the body width (decision 0096, see [Crossings](crossings.md)). |
| Default rule of which pipe is on top | Write it: the last drawn is on top; the click is the exception. |
| Orthogonal lock while drawing a pipe | Add, like the angle lock of the pen. |
| Path kind per pipe (straight, right angles, rounded) | Not taken: the corner radius of the style is enough (decided 2026-11-23). |
| Usage counter of a style | Add: it prepares the display of broken links. |
| Colouring by topology (zenon) | Refuse: the editor does not know what a fluid is. |
| Automatic routing around symbols (libavoid) | Not in the first version: a path is drawn by clicks. |

### Vocabulary (opinion of the report)

| Concept | Words found | Proposed name |
| --- | --- | --- |
| The pipe | pipe, connector, edge, link, schematic line | **Pipe** |
| What it contains | service, fluid, appearance, content | **Content** (a group label; "fluid" excludes electricity; "service" is the trade word) |
| The style | appearance, connector style, pipe style | **Pipe style** (kept rather than "pipe type", decision 0095) |
| The connection point | connection point, pin, port, anchor point | **Connection point** ("anchor" is already taken by the nine anchors) |
| The junction | junction, branch, junction marker, waypoint | **Junction** (the place), **Junction marker** (the shape), **Branch** (the pipe that leaves) |
| The crossing | line jump, bridge, jumpover, gap, loop | **Crossing**, of type **Bridge**, **Gap** or **None** |
| Start and end | arrowhead, start, end, parts, marker | **Start**, **End**, **End shape**; avoid "cap", which is the end of a stroke in SVG |

### Computing pipes

- The computation holds in plain JavaScript with known bricks (arc at a corner, offset of a polyline, cut, arc for a bridge). Only the search of the crossings is to measure: comparing every segment with every other costs the square of their number; a spatial index and a recomputation limited to the two segments next to the moved point should bring it back to a few tens of tests (hypothesis, not a result).
- Opinion: never draw a bridge or a gap with a mask (Ignition hit the limit of the number of masks of the browser); compute the geometry. Confidence: medium.
- What is recomputed when a point moves:

```mermaid
flowchart TD
    M["A point of the pipe moves"] --> A["Its two neighbouring segments"]
    A --> B["The roundings of the corners touched"]
    A --> C["The crossings of these segments, searched again"]
    A --> D["Junctions, ends and inline symbols on these segments"]
    C --> F["The bridge or gap of the other pipe concerned"]
    X["The rest of the synoptic"] --> K["Kept in cache"]
```

- For the geometry research (not this part): offset of a polyline with arcs (body, borders, kinds of joins); search of the crossings between segments and arcs, with a spatial index, incremental; cut of a path at a point and insertion of an arc; length along a path (position of an inline symbol, start of the dashes).
- POC proposed, **P9**: 100, 300 then 1 000 pipes of 5 segments, 1 000 to 10 000 crossings, one point moved with the mouse; work time per frame in plain JavaScript, with and without index; ways A and B of [Pipe styles](pipe-styles.md).

## Decided

- Junctions and crossings live **inside the pipe style**, as in the archived Figma page and as the report advised. They are computed: the user picks a style for a pipe and does not edit these parts by hand.
- A symbol can be **connected to a pipe**: it fits onto it and can only be moved along it (see [Pipes in the synoptic](in-the-synoptic.md)).
- A pipe style can be **linked to a type** of Metadata. Its dashes **move** only through the signals of that type: a direction signal (stopped, start to end, end to start) and a speed, a signal or a fixed value; no on or off option. The movement **propagates** into the branches at a junction. The model also drives the colours (decision 0096, see [Pipe styles](pipe-styles.md)).
- One **base pipe style** per Symbol Lib, without colour; **pipe styles** give the fills; dashes as **sequences of coloured segments**, for pipes and for every border; dashes computed as cleanly as possible, an odd cut in a corner accepted (decision 0095).
- A pipe style changes **nothing of the base but its body width**: no list of overridden options. Base and pipe styles show the same sections in the same order (decision 0096).
- The **size of a crossing** is computed from the body width, not set (decision 0096).
- The **start and end shapes** are not in the base pipe style: they have a list of their own on the Pipes page, after the pipe styles (decision 0095).
- A branch leaves **one pipe as a tree**, with one pipe style and one flow, as in the archived Figma page and in Ignition (decision 0094).
- **No path kind per pipe**: the corner radius of the style gives the look of every angle (decision 0094).
- The display of every case is named **Preview** (decision 0094).

## Open questions

- The list is in [Open questions](../10-open-questions.md).
