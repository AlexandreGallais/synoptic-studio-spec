# Screens of the pipes

> [Home](../README.md) › [Screens](README.md) › Pipes

Status: draft, written by the assistant from the [Pipes](../symbols/pipes/README.md) pages, themselves a draft; its add buttons follow the layout rule "a title and a small + on its right". It adds no rule. Kinds and statuses are explained in the [guide of this folder](README.md).

The pipes are made in a Symbol Lib, on its page Pipes ([SY-00.4](symbols.md#sy-00--navigation-bar-of-the-symbol-mode), end of 2026-11-17) and drawn in a synoptic (part 3, not written). One base pipe style gives the shape of every pipe of the library, without colour, and its linked type and movement; each pipe style, the look of the library for one item of the built-in enum `pipe_style`, gives the fills and can override the type, the movement and the body and border widths, each with a reset.

```mermaid
flowchart LR
    LIB["Symbol Lib, page Pipes"] --> BASE["PI-01 Base pipe style"]
    LIB --> STY["PI-02 Pipe styles: Water, Oil, Steam..."]
    STY --> DASH["PI-04 Segment list"]
    BASE --> PRE["PI-05 Preview"]
    STY --> PRE
    STY -.-> SYN["PI-06 Pipes in a synoptic, part 3"]
```

## Layout of the page Pipes

The page Pipes of a Symbol Lib follows the layout rules, as [SY-12](symbols.md#sy-12--enums-of-a-symbol-lib): the list on the left, the selected style on the right. Proposed by the assistant on 2026-11-23, to comment on the test screens.

```mermaid
block-beta
    columns 4
    rail["Navigation bar SY-00, Pipes selected"] list["Base pipe style at the top; Pipe styles: title, search, +, each with a swatch of its body"] options["Options of the selected item, in sections, two columns"]:1 preview["Preview PI-05, always visible on the right"]
```

- The left column holds, from top to bottom: the **base pipe style**, with a tag "Base", at the very top, above the title of the pipe styles (accepted on 2026-11-24); the list of the **pipe styles**, one per item of the enum `pipe_style`, in the order of their keys. Its title has **no +**: in its place, a **small link opens the enum `pipe_style` on the Enums page of Metadata** ([MD-09](metadata.md#md-09--enums)), where items are added (2026-11-24, decision 0099). There is no list of start and end shapes (decision 0098).
- The options are grouped in **the same sections, in the same order**, for the base and for a pipe style: Linked type, Body, Border, Corners, Junctions, Crossings, Movement (decisions 0096 and 0097).
- The sections sit **at the same place** for the base and for a pipe style: Linked type, Body and Border in the first column; Corners, Junctions, Crossings and Movement in the second (2026-11-24).
- The size of a crossing, computed, is not shown: neither a note nor a read-only row (2026-11-24).
- Every option is changed in place and written at once (see [Files and conflicts](../storage/files-and-conflicts.md#saving)).
- Test screens in Figma, page Spec, section "Symbol mode · test screens (2026-11-23)": "PI-01 · Pipes page of a Symbol Lib · base pipe style" and "PI-02 · Pipes page of a Symbol Lib · pipe style Gas", redrawn on 2026-11-24 (decisions 0096, 0097 and 0098); PI-02 shows its item of `pipe_style`, read-only, instead of a name, the styles by key, and a link to the enum in Metadata instead of the + (decision 0099). Quick tests, no design-system component.

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
      Direction, a value or a signal picked in the field
      Speed, a value or a signal picked in the field
    Preview
```

No colour and no dash in the base: the fills are in [PI-02](#pi-02--pipe-style).

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| PI-01.19 | Linked type | Select | First section. Optional; any type of Metadata. Taken by every pipe style that does not override it (2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#linked-type) |
| PI-01.1 | Width | Number field, no unit | Width of the body, in pixels. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.2 | Body fill | — | Removed: moved to the pipe styles ([PI-02.2](#pi-02--pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.3 | Border on or off | — | Removed (2026-11-24): a border width of 0 is no border. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#the-base-pipe-style) |
| PI-01.4 | Border width | Number field, no unit | On both sides, the same. 0: no border. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.5 | Border position | Segmented control | Inside, Middle, Outside the edge of the body, one click, as the border of a shape (2026-11-26, replaces the select). Greyed out when the width is 0 (proposed). | Decided (greyed: Proposed) | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.6 | Border fill | — | Removed: moved to the pipe styles ([PI-02.3](#pi-02--pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.7 | Corner radius | Number field, no unit | Section Corners. 0 keeps sharp angles; also shapes the bridges. The same for every pipe style. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-01.8 | Moving dashes | — | Removed: no on or off; the movement comes from the direction ([PI-01.9](#pi-01--base-pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-01.9 | Direction | Select with a small icon inside to pick a signal | Section Movement, always shown, even without a type. The three items of the built-in enum "pipe direction" (stopped, start to end, end to start), or, with the icon, a signal of the linked type of that enum; without a type, the icon is greyed (2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-01.10 | Speed | Number field in px/s with a small icon inside to pick a signal | Section Movement, under Direction. A fixed value is typed, in pixels per second (2026-11-26); the icon picks another signal of the linked type, a number, instead (decision 0041), converted to px/s by two pairs value → px/s (decision 0109). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-01.11 | Junction kind | Segmented control | Flat (the pipes join in one clean outline, no marker), Circle, Square; one click ([layout rule](README.md#a-segmented-control-for-two-to-four-short-options), 2026-11-26). | Decided | [Junctions](../symbols/pipes/junctions.md) |
| PI-01.12 | Junction size | Number field, no unit | For a circle or a square only: greyed out when the kind is Flat (2026-11-24). Fixed or a multiple of the width: Open. Example: 12. | Decided (fixed or multiple: Open) | [Junctions](../symbols/pipes/junctions.md) |
| PI-01.17 | Junction fill | — | Removed: the junction takes the body fill of the pipe style (2026-11-23). | Decided | [Junctions](../symbols/pipes/junctions.md) |
| PI-01.18 | Junction border | — | Removed: the junction has the border of the pipe, with the same width and position. | Decided | [Junctions](../symbols/pipes/junctions.md) |
| PI-01.13 | Crossing kind | Segmented control | One click ([layout rule](README.md#a-segmented-control-for-two-to-four-short-options), 2026-11-26). Bridge (an arch), gap (the pipe underneath is cut in two), none (one passes over the other). | Decided | [Crossings](../symbols/pipes/crossings.md) |
| PI-01.14 | Crossing size | — | Removed (2026-11-24): computed from the body width, so that every crossing looks the same; the bridge follows the corner radius. | Decided (formula: Open) | [Crossings](../symbols/pipes/crossings.md) |
| PI-01.15 | End shapes | — | Removed: no end shapes; an arrow or a flange at the end of a pipe is a symbol (decision 0098). | Decided | [Pipes](../symbols/pipes/README.md) |
| PI-01.16 | Preview | — | Always visible next to the style, redrawn at each change ([PI-05](#pi-05--preview)). | Decided | [Preview](../symbols/pipes/preview.md) |

Gaps:

- Usage counter "used by 38 pipes" (proposed).

## PI-02 · Pipe style

Path: Symbols › a Symbol Lib › Pipe styles › a style (Water, Oil, Steam...).

```mermaid
mindmap
  root((PI-02 Pipe style))
    Item of pipe_style
      Key, display name, description
    Linked type
      The base's, or its own, with a reset
      Animations of the colours
    Body
      Width, the base's or its own, with a reset
      Body fill, a segment list
        One line, a plain colour
        Several lines, dashes
    Border
      Width, the base's or its own, with a reset
      Border fill, colours stacked, no length
    Corners, Junctions, Crossings
      Shown, set by the base
    Movement
      The base's, or its own, with a reset
      Direction, a value or a signal picked in the field
      Speed, a value or a signal picked in the field
```

The sections are those of [PI-01](#pi-01--base-pipe-style), in the same order. A value the style can override shows the base's value until it is overridden; an overridden value has a reset next to its field.

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| PI-02.1 | Name | — | Removed (2026-11-24, decision 0099): a pipe style has no name of its own; it shows its item of `pipe_style` ([PI-02.16](#pi-02--pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#pipe-styles) |
| PI-02.16 | Item of pipe_style | Read-only values | At the top, above the sections: the key, the display name and the description of the item this style draws, kept in the enum, not in the style (2026-11-24). Always read-only here, base item or not: changed in Metadata only (2026-11-24). | Decided | [The enum pipe_style](../symbols/pipes/pipe-styles.md#the-enum-pipe_style) |
| PI-02.8 | Linked type | Select + reset | First section. The base's type until another is chosen; when the base has a type, only that type or one of its sub-types (2026-11-26); else any type of Metadata (no library of types). Its signals feed Movement and the animations. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#linked-type) |
| PI-02.12 | Body width | Number field, no unit, + reset | Section Body. The base's width until the user types one (gas pipes drawn thinner). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#overriding-a-value-of-the-base) |
| PI-02.2 | Body fill | [Segment list](../controls/segment-list.md) ([PI-04](#pi-04--segment-list)) | Section Body. One line: a plain colour; several lines: a dash sequence that runs from the start of the pipe to its end; example: black 100 % 10, black 0 % 20, red 100 % 2. No radio "colour or dash sequence" (2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#dash-sequences) |
| PI-02.13 | Border width | Number field, no unit, + reset | Section Border. The base's border width until the user types one, chosen apart from the body width (2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#overriding-a-value-of-the-base) |
| PI-02.3 | Border fill | [Colour fields](../controls/colour-field.md) stacked, small + on the title | Section Border. Colours stacked, no length, no dashes (2026-11-26, as every border); no strip under the lines, the preview shows the result (2026-11-26). Greyed out when the border width is 0 (proposed). | Decided (greyed: Proposed) | [Pipe styles](../symbols/pipes/pipe-styles.md#pipe-styles) |
| PI-02.17 | Colour that follows an enum | Small signal icon inside a colour field of the body or the border | Picks an enum signal of the linked type, then a colour column of that enum ([SY-12](symbols.md#sy-12--enums-of-a-symbol-lib)); the line takes the colour of the current value (Product Owner, 2026-11-26; the form: assistant's). Greyed without a type. | Decided (link), Proposed (form) | [Pipe styles](../symbols/pipes/pipe-styles.md#linked-type) |
| PI-02.14 | Corners, Junctions, Crossings; border position | Read-only values, section tagged "Base" | The base's values, shown in their sections so that the user sees the whole pipe (accepted on 2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#the-same-sections-everywhere) |
| PI-02.15 | Direction | Select with a small icon inside to pick a signal, + reset | Section Movement. The base's direction until another is chosen: stopped, start to end or end to start, chosen in the list, or a signal of the type of the built-in enum "pipe direction" picked with the icon (2026-11-24); no second signal. Overriding the type overrides the direction and the speed too; resetting the type gives back the base's. No type: only fixed values, the icon greyed. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-02.11 | Speed | Number field in px/s with a small icon inside to pick a signal, + reset | Section Movement, under Direction. A fixed value is typed in the field, in pixels per second; the icon inside picks another signal of the linked type instead, as for the bounds of a signal in Metadata (decision 0041), converted to px/s (as PI-01.10). No radio "fixed or signal" (2026-11-24). | Decided (unit), Proposed (conversion) | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |
| PI-02.9 | Animations | List, like [SY-08](symbols.md#sy-08--animation-mode) | Section Linked type. Output signals drive the colours, and more ("plenty of things"). | Decided (properties beyond these: Open) | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-02.4 | Dashes or not | — | Removed: the body fill and the border fill choose between a colour and a dash sequence. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| PI-02.5 | Override another option | — | Removed (2026-11-24): no list of overridden options; only the linked type, the movement, the body width and the border width can be overridden. | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#overriding-a-value-of-the-base) |
| PI-02.6 | Tag "Base" on an option | — | Removed with the list of overridden options; the read-only sections are tagged "Base" ([PI-02.14](#pi-02--pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#the-same-sections-everywhere) |
| PI-02.7 | Reset to the base | Icon button, next to the field of an overridden value | Shown only when the value is overridden; gives back the base's value, so that it is always clear which values come from the base (2026-11-24). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#overriding-a-value-of-the-base) |
| PI-02.10 | Moving dashes | — | Removed (2026-11-24): no on or off; the movement comes from the direction ([PI-02.15](#pi-02--pipe-style)). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md#moving-dashes) |

Gaps:

- Create, duplicate, delete a pipe style; what happens to the pipes that use a deleted style?
- Which properties a signal can drive beyond speed, direction and colours (Open).

## PI-03 · End shape editor (removed)

Removed on 2026-11-24 (decision 0098): a pipe has no start or end shape; an arrow, a flange or a cap at its end is a symbol with a connection point. The ID PI-03 is not reused.

## PI-04 · Segment list

Path: in place, the body fill of [PI-02](#pi-02--pipe-style), the only fill that takes dashes since 2026-11-26 (no border has dashes). The control is described in [Segment list](../controls/segment-list.md) (2026-11-24; it was a separate dash sequence editor).

```mermaid
mindmap
  root((PI-04 Segment list))
    Title, small plus on its right
    Lines in order
      Colour field
        Colour and opacity
        0 percent for a gap
      Length
      Minus to remove
    One line, a plain colour
    Several lines, dashes
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| PI-04.1 | Lines | List | One line per segment, repeated along the line, in order, as long as wanted: "black 100 % 4, black 0 % 4"; "black 10, transparent 20, red 2", then black, transparent, red again. One line: a plain colour. | Decided | [Segment list](../controls/segment-list.md) |
| PI-04.2 | Length | Number field, no unit | On each line, after the colour. | Decided | [Segment list](../controls/segment-list.md) |
| PI-04.3 | Colour | [Colour field](../controls/colour-field.md) | Colour │ opacity on each line; a gap is a line at 0 %. | Decided | [Segment list](../controls/segment-list.md) |
| PI-04.4 | Add a line | Button (small +) | On the right of the title of the section, Body fill ([layout rules](README.md#a-title-and-a-small--on-its-right)). | Decided | [Segment list](../controls/segment-list.md) |
| PI-04.5 | Remove a line | Icon button (−), at the end of each line | Removes the segment (2026-11-24: a −, no longer a bin). | Decided | [Segment list](../controls/segment-list.md) |
| PI-04.6 | Reorder a line | not said | — | Implied | — |

Gaps:

- A ready-made list of common sequences (dashes, dots, dash and dot)?
- A maximum number of dashes per shape, set by the POC P8 (fill and border page).

## PI-05 · Preview

Path: next to the base pipe style or a pipe style being edited, always visible.

The preview is **exactly the same** for the base and for every pipe style: the same cases, at the same places, drawn with the style being edited; only the pipe under the crossing is drawn with the base style (Product Owner, 2026-11-24).

| ID | Case | What it shows | Status | Source |
| --- | --- | --- | --- | --- |
| PI-05.1 | Straight pipe | Body fill, width, border, dash sequences. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.2 | Right angle | Corner radius. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.3 | Other angles | An angle other than 90°, a very short segment. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.4 | Junction, several junctions | A pipe and one of its branches; a 3-way and a 4-way. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.5 | Crossing | The style being edited passes over a pipe of the base style, by its crossing kind (2026-11-24). | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.6 | Start and end | Removed: no end shapes (decision 0098). | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.7 | Connected to a symbol | A pipe on a connection point. | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.8 | Base and style side by side | Removed: the preview is the same for the base and every style; the crossing over the base shows the difference (2026-11-24). | Decided | [Preview](../symbols/pipes/preview.md) |
| PI-05.9 | Symbol connected to a pipe | On a straight segment and in a bend. | Proposed | [Preview](../symbols/pipes/preview.md) |
| PI-05.10 | Free ends | A pipe whose two ends are connected to nothing (decision 0098). | Proposed | [Preview](../symbols/pipes/preview.md) |

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
| PI-06.4 | Start shape, end shape | — | Removed: an end of a pipe is free or connected to a symbol (decision 0098). | Decided | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.5 | Swap a crossing | Click on the crossing | Highlighted on hover. | Decided | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.6 | Connect to the pipe | not said (action on the symbol) | The symbol fits onto the pipe and only slides along it. | Decided | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.7 | Free the symbol | not said | Undo "connect to the pipe". | Proposed | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.8 | Orthogonal lock | Toggle | While drawing. | Proposed | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |
| PI-06.9 | Crossings of a pipe, swap all | List + Button | Archived Figma page. | Proposed | [Pipes in the synoptic](../symbols/pipes/in-the-synoptic.md) |

Gaps:

- Everything about part 3: this screen is only a reminder of what was said.
