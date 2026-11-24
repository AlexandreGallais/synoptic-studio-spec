# Screens of the pipes

> [Home](../README.md) › [Screens](README.md) › Pipes

Status: draft, written by the assistant from the [Pipes](../symbols/pipes/README.md) pages, themselves a draft; its add buttons follow the layout rule "a title and a small + on its right". It adds no rule. Kinds and statuses are explained in the [guide of this folder](README.md).

The pipes are made in a Symbol Lib, on its page Pipes ([SY-00.4](symbols.md#sy-00--navigation-bar-of-the-symbol-mode), end of 2026-11-17) and drawn in a synoptic (part 3, not written). One base pipe style gives the shape of every pipe of the library, without colour, and its linked type and movement; each pipe style gives the fills and can override the type, the movement and the body and border widths, each with a reset.

```mermaid
flowchart LR
    LIB["Symbol Lib, page Pipes"] --> BASE["PI-01 Base pipe style"]
    LIB --> STY["PI-02 Pipe styles: Water, Oil, Steam..."]
    LIB --> END["PI-03 Start and end shapes"]
    STY --> DASH["PI-04 Dash sequence editor"]
    BASE --> PRE["PI-05 Preview"]
    STY --> PRE
    STY -.-> SYN["PI-06 Pipes in a synoptic, part 3"]
```

## Layout of the page Pipes

The page Pipes of a Symbol Lib follows the layout rules, as [SY-12](symbols.md#sy-12--enums-of-a-symbol-lib): the list on the left, the selected style on the right. Proposed by the assistant on 2026-11-23, to comment on the test screens.

```mermaid
block-beta
    columns 4
    rail["Navigation bar SY-00, Pipes selected"] list["Base pipe style at the top; Pipe styles: title, search, +, each with a swatch of its body; Start and end shapes: title, +"] options["Options of the selected item, in sections, two columns"]:1 preview["Preview PI-05, always visible on the right"]
```

- The left column holds, from top to bottom: the **base pipe style**, with a tag "Base", at the very top, above the title of the pipe styles (accepted on 2026-11-24); the list of the **pipe styles**, with its small + to add one; the list of the **start and end shapes**, with its small + to add one, each set up in [PI-03](#pi-03--end-shape-editor).
- The options are grouped in **the same sections, in the same order**, for the base and for a pipe style: Linked type, Body, Border, Corners, Junctions, Crossings, Movement (decisions 0096 and 0097).
- An end shape has a page of its own, with a drawing area instead of the two columns of options ([PI-03](#pi-03--end-shape-editor)).
- Every option is changed in place and written at once (see [Files and conflicts](../storage/files-and-conflicts.md#saving)).
- Test screens in Figma, page Spec, section "Symbol mode · test screens (2026-11-23)": "PI-01 · Pipes page of a Symbol Lib · base pipe style" and "PI-02 · Pipes page of a Symbol Lib · pipe style Gas", redrawn on 2026-11-24 (decisions 0096 and 0097); "PI-03 · Pipes page of a Symbol Lib · end shape Arrow", drawn on 2026-11-24. Quick tests, no design-system component.

## PI-01 · Base pipe style

Path: Symbols › a Symbol Lib › Base pipe style. One per Symbol Lib.

```mermaid
mindmap
  root((PI-01 Base pipe style))
    Linked type, optional
    Body
      Width
    Border
      Width, 0 for none
      Position
    Corners
      Corner radius, the same for every style
    Junctions
      Kind
      Size, greyed out for Flat
    Crossings
      Kind
    Movement
      Direction, a signal of the type
      Speed, a value or a signal picked in the field
    Preview
```

No colour and no dash in the base: the fills are in [PI-02](#pi-02--pipe-style).

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| PI-01.19 | Linked type | Select | First section. Optional; any type of Metadata. Taken by every pipe style that does not override it (2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#linked-type) |
| PI-01.1 | Width | Number field (px) | Width of the body. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.2 | Body fill | — | Removed: moved to the pipe styles ([PI-02.2](#pi-02--pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.3 | Border on or off | — | Removed (2026-11-24): a border width of 0 is no border. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#the-base-pipe-style) |
| PI-01.4 | Border width | Number field (px) | On both sides, the same. 0: no border. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.5 | Border position | Radio | Inside, middle, outside the edge of the body. Greyed out when the width is 0 (proposed). | Decided (greyed: Proposed) | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.6 | Border fill | — | Removed: moved to the pipe styles ([PI-02.3](#pi-02--pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.7 | Corner radius | Number field (px) | Section Corners. 0 keeps sharp angles; also shapes the bridges. The same for every pipe style. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.8 | Moving dashes | — | Removed: no on or off; the movement comes from the direction signal ([PI-01.9](#pi-01--base-pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-01.9 | Direction | Select (signals of the linked type) | Section Movement, shown when a type is linked. One enum signal of the built-in enum "pipe direction": stopped, start to end, end to start. | Decided (shown only with a type: Proposed) | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-01.10 | Speed | Number field with a small icon inside to pick a signal (unit: Open) | Section Movement, under Direction. A fixed value is typed; the icon picks a signal of the linked type instead (decision 0041). | Decided (unit: Open) | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-01.11 | Junction kind | Radio | Flat (the pipes join in one clean outline, no marker), circle, square. | Decided | [Junctions](../symbols/pipes/junctions.md) |
| PI-01.12 | Junction size | Number field (px) | For a circle or a square only: greyed out when the kind is Flat (2026-11-24). Fixed or a multiple of the width: Open. Example: 12 px. | Decided (fixed or multiple: Open) | [Junctions](../symbols/pipes/junctions.md) |
| PI-01.17 | Junction fill | — | Removed: the junction takes the body fill of the pipe style (2026-11-23). | Decided | [Junctions](../symbols/pipes/junctions.md) |
| PI-01.18 | Junction border | — | Removed: the junction has the border of the pipe, with the same width and position. | Decided | [Junctions](../symbols/pipes/junctions.md) |
| PI-01.13 | Crossing kind | Radio | Bridge (an arch), gap (the pipe underneath is cut in two), none (one passes over the other). | Decided | [Crossings](../symbols/pipes/crossings.md) |
| PI-01.14 | Crossing size | — | Removed (2026-11-24): computed from the body width, so that every crossing looks the same; the bridge follows the corner radius. | Decided (formula: Open) | [Crossings](../symbols/pipes/crossings.md) |
| PI-01.15 | End shapes | — | Removed: the end shapes are not in the base pipe style; they have their own list on the Pipes page ([PI-03](#pi-03--end-shape-editor)). | Decided | [Pipe ends](../symbols/pipes/ends.md) |
| PI-01.16 | Preview | — | Always visible next to the style, redrawn at each change ([PI-05](#pi-05--preview)). | Decided | [Preview](../symbols/pipes/preview.md) |

Gaps:

- Usage counter "used by 38 pipes" (proposed).

## PI-02 · Pipe style

Path: Symbols › a Symbol Lib › Pipe styles › a style (Water, Oil, Steam...).

```mermaid
mindmap
  root((PI-02 Pipe style))
    Name
    Linked type
      The base's, or its own, with a reset
      Animations of the colours
    Body
      Width, the base's or its own, with a reset
      Body fill
        Colour
        Dash sequence
    Border
      Width, the base's or its own, with a reset
      Border fill
        Colour
        Dash sequence
    Corners, Junctions, Crossings
      Shown, set by the base
    Movement
      The base's, or its own, with a reset
      Direction, a signal of the type
      Speed, a value or a signal picked in the field
```

The sections are those of [PI-01](#pi-01--base-pipe-style), in the same order. A value the style can override shows the base's value until it is overridden; an overridden value has a reset next to its field.

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| PI-02.1 | Name | Text field | Free text: Water, Oil, Steam, Electricity. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-02.8 | Linked type | Select + reset | First section. The base's type until another is chosen; any type of Metadata (no library of types). Its signals feed Movement and the animations. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#linked-type) |
| PI-02.12 | Body width | Number field (px) + reset | Section Body. The base's width until the user types one (gas pipes drawn thinner). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#overriding-a-value-of-the-base) |
| PI-02.2 | Body fill | Radio + Colour or dash sequence | Section Body. A plain colour, or a dash sequence that runs from the start of the pipe to its end, edited in place ([PI-04](#pi-04--dash-sequence-editor)); example: black 10, transparent 20, red 2. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-02.13 | Border width | Number field (px) + reset | Section Border. The base's border width until the user types one, chosen apart from the body width (2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#overriding-a-value-of-the-base) |
| PI-02.3 | Border fill | Radio + Colour or dash sequence | Section Border. Like the body. Greyed out when the border width is 0 (proposed). | Decided (greyed: Proposed) | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-02.14 | Corners, Junctions, Crossings; border position | Read-only values, section tagged "Base" | The base's values, shown in their sections so that the user sees the whole pipe (accepted on 2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#the-same-sections-everywhere) |
| PI-02.15 | Direction | Select (signals of the linked type) + reset | Section Movement. The base's signal until another is chosen. The signal says whether the dashes move and which way: stopped, start to end, end to start: one enum signal of the built-in enum "pipe direction", no second signal. Overriding the type overrides the direction and the speed too; resetting the type gives back the base's. No signal, or no type: the dashes do not move. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-02.11 | Speed | Number field with a small icon inside to pick a signal, + reset (unit: Open) | Section Movement, under Direction. A fixed value is typed in the field; the icon inside picks a signal of the linked type instead, as for the bounds of a signal in Metadata (decision 0041). No radio "fixed or signal" (2026-11-24). | Decided (unit: Open) | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-02.9 | Animations | List, like [SY-08](symbols.md#sy-08--animation-mode) | Section Linked type. Output signals drive the colours, and more ("plenty of things"). | Decided (properties beyond these: Open) | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-02.4 | Dashes or not | — | Removed: the body fill and the border fill choose between a colour and a dash sequence. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-02.5 | Override another option | — | Removed (2026-11-24): no list of overridden options; only the linked type, the movement, the body width and the border width can be overridden. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#overriding-a-value-of-the-base) |
| PI-02.6 | Tag "Base" on an option | — | Removed with the list of overridden options; the read-only sections are tagged "Base" ([PI-02.14](#pi-02--pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#the-same-sections-everywhere) |
| PI-02.7 | Reset to the base | Icon button, next to the field of an overridden value | Shown only when the value is overridden; gives back the base's value, so that it is always clear which values come from the base (2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#overriding-a-value-of-the-base) |
| PI-02.10 | Moving dashes | — | Removed (2026-11-24): no on or off; the movement comes from the direction signal ([PI-02.15](#pi-02--pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |

Gaps:

- Create, duplicate, delete a pipe style; what happens to the pipes that use a deleted style?
- Which properties a signal can drive beyond speed, direction and colours (Open).
- Unit of the speed of the moving dashes (pixels per second?).

## PI-03 · End shape editor

Path: Symbols › a Symbol Lib › Pipes › Start and end shapes › create (small +) or open one. A list of its own, after the pipe styles ([layout](#layout-of-the-page-pipes)). The page was proposed by the assistant on 2026-11-24 (see [The page of an end shape](../symbols/pipes/ends.md#the-page-of-an-end-shape)).

```mermaid
block-beta
    columns 4
    list["List of the Pipes page, the shape selected"] draw["Drawing area: box, nine anchors, piece of pipe; tool bar at the bottom"] options["End shape, Box, Attach point, Shapes, Fill of the selected shape"] preview["Preview PI-05"]
```

```mermaid
block-beta
    columns 3
    a1["anchor"] a2["anchor"] a3["anchor"]
    a4["anchor: the pipe arrives here"] box["Box W x H: the shape is drawn here with the drawing tools"] a6["anchor"]
    a7["anchor"] a8["anchor"] a9["anchor"]
```

```mermaid
mindmap
  root((PI-03 End shape))
    Drawing area
      Box and its nine anchors
      Piece of pipe on the attach point
      Tool bar of SY-04, without Text
    End shape
      Name
      Delete, red button
    Box
      Width
      Height
    Attach point
      Grid of the nine anchors
    Shapes
      One line per shape
    Fill of the selected shape
      Pipe body, pipe border or colour
    Preview
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| PI-03.5 | Name of the end shape | Text field | Free text: Arrow, Flange, Cap. | Proposed | [Pipe ends](../symbols/pipes/ends.md#the-page-of-an-end-shape) |
| PI-03.6 | Delete the end shape | Red button + warning | A whole thing ([layout rules](README.md#delete-a-warning-only-for-a-whole-thing)). | Proposed | [Pipe ends](../symbols/pipes/ends.md#the-page-of-an-end-shape) |
| PI-03.1 | Box size | Number field (px) each | Width and height, the size the user wants. The shape keeps this size on every pipe, whatever its width (2026-11-24). | Decided | [Pipe ends](../symbols/pipes/ends.md) |
| PI-03.3 | Attach point | Grid of the nine anchors | Where the end point of the pipe is put. Nine anchors (specs) or four at the middle of the sides (archived Figma page): Open. | Decided (number: Open) | [Pipe ends](../symbols/pipes/ends.md) |
| PI-03.2 | Drawing area | Editor | The box, its anchors, the chosen one marked, and a piece of pipe of the base style arriving from the left on it. | Decided (piece of pipe: Proposed) | [Pipe ends](../symbols/pipes/ends.md) |
| PI-03.7 | Tool bar | Floating bar, at the bottom of the drawing area | Select, Hand, Group, Rectangle, Ellipse, Polygon, Pen: the tools of [SY-04](symbols.md#sy-04--drawing-mode), without Text. | Decided (tools of the drawing mode), Proposed (without Text) | [Pipe ends](../symbols/pipes/ends.md) |
| PI-03.8 | Shapes | List | The shapes drawn in the box, one line each; a click selects. | Proposed | [Pipe ends](../symbols/pipes/ends.md#the-page-of-an-end-shape) |
| PI-03.4 | Fill of the selected shape | Radio: Pipe body, Pipe border, Colour | The shape takes the body fill or the border fill of the pipe's style, or a colour of its own; its border has the same choice, shape by shape (2026-11-24). | Decided | [Pipe ends](../symbols/pipes/ends.md) |
| PI-03.9 | Preview | Fixed cases | The shape at the end and at the start of a pipe of several styles, on a straight pipe and after a bend, turned with the last segment. | Proposed | [Pipe ends](../symbols/pipes/ends.md#the-page-of-an-end-shape) |

Gaps:

- How the shape sits on a pipe: end point on the attach point, turned with the last segment, turned the other way at the start (proposed); mirrored across the pipe?
- Colour of a shape that takes the pipe's fill when that fill is a dash sequence (Oil).
- Can every pipe style use every end shape?

## PI-04 · Dash sequence editor

Path: wherever a fill or a border can take dashes: [PI-02](#pi-02--pipe-style), and the border of a shape ([SY-04](symbols.md#sy-04--drawing-mode)).

```mermaid
mindmap
  root((PI-04 Dash sequence))
    Segments in order
      Length
      Colour
        Transparent for a gap
    Add a segment
    Remove a segment
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| PI-04.1 | Segments | List | Repeated along the line, in order, as long as wanted: "black 4, transparent 4"; "black 10, transparent 20, red 2", then black, transparent, red again. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-04.2 | Length | Number field (px) | Per segment. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-04.3 | Colour | Colour, with transparent | A gap is a transparent segment. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-04.4 | Add a segment | Button (icon with a small +) | On the right of the title "Segments" ([layout rules](README.md#a-title-and-a-small--on-its-right), 2026-11-16). | Decided | [Layout rules](README.md#a-title-and-a-small--on-its-right) |
| PI-04.5 | Remove a segment | Icon button (trash), on the line of each segment | Removes the segment from the sequence. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#dash-sequences) |
| PI-04.6 | Reorder a segment | not said | — | Implied | — |

Gaps:

- A ready-made list of common sequences (dashes, dots, dash and dot)?
- A maximum number of dashes per shape, set by the POC P8 (fill and border page).

## PI-05 · Preview

Path: next to the base pipe style or a pipe style being edited, always visible.

| ID | Case | What it shows | Status | Source |
| --- | --- | --- | --- | --- |
| PI-05.1 | Straight pipe | Body fill, width, border, dash sequences. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.2 | Right angle | Corner radius. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.3 | Other angles | An angle other than 90°, a very short segment. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.4 | Junction, several junctions | A pipe and one of its branches; a 3-way and a 4-way. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.5 | Crossing | Both ways. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.6 | Start and end | End shapes of the list on a pipe of the style. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.7 | Connected to a symbol | A pipe on a connection point. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.8 | Base and style side by side | The fills and the own widths of the style. | Proposed | [Preview](../symbols/pipes/preview.md) |
| PI-05.9 | Symbol connected to a pipe | On a straight segment and in a bend. | Proposed | [Preview](../symbols/pipes/preview.md) |

Gaps:

- Do the dashes move in the preview?

## PI-06 · Pipes in a synoptic (part 3, preview)

Path: a synoptic › pipe tool. Part 3 is not written: this only gathers what the pipes pages already say.

```mermaid
mindmap
  root((PI-06 Pipe in a synoptic))
    Pipe tool
      Click point after point
      Snaps to connection points
      Click inside a pipe for a branch of it
    Panel of a pipe
      Pipe style
      Start shape
      End shape
    Crossing
      Hover highlights it
      Click swaps which pipe is on top
    Symbol on a pipe
      Connect to the pipe
      Slides along the pipe only
    Proposed
      Orthogonal lock
      Swap all crossings
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| PI-06.1 | Pipe tool | Button (tool) | Click point after point, straight segments; snaps to connection points. | Decided | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.2 | Branch | — | Click inside a pipe, then draw. The branch belongs to that pipe: one pipe as a tree, one style, one flow. | Decided | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.3 | Pipe style | Select | Among the styles of the Symbol Lib. | Decided | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.4 | Start shape, end shape | Select each | A shape of the list of start and end shapes, or none. | Decided | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.5 | Swap a crossing | Click on the crossing | Highlighted on hover. | Decided | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.6 | Connect to the pipe | not said (action on the symbol) | The symbol fits onto the pipe and only slides along it. | Decided | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.7 | Free the symbol | not said | Undo "connect to the pipe". | Proposed | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.8 | Orthogonal lock | Toggle | While drawing. | Proposed | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.9 | Crossings of a pipe, swap all | List + Button | Archived Figma page. | Proposed | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |

Gaps:

- Everything about part 3: this screen is only a reminder of what was said.
