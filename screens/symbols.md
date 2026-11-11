# Screens of the symbol editor

> [Home](../README.md) › [Screens](README.md) › Symbol editor

Status: draft, written by the assistant on 2026-11-11 from the [Symbols](../symbols/README.md) pages, themselves a draft. It adds no rule. Kinds and statuses are explained in the [guide of this folder](README.md). The pipes are in [Pipes](pipes.md).

## SY-01 · Symbol Libs

Path: Symbols.

```mermaid
mindmap
  root((SY-01 Symbol Libs))
    List of Symbol Libs
    Create a Symbol Lib
      Name
      Type Lib
    A Symbol Lib
      Change its Type Lib
      Open it
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-01.1 | List of Symbol Libs | List | The user selects one to see its content. | Decided | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-01.2 | Create a Symbol Lib | not said (button) | Asks a name and a Type Lib. | Decided (control not said) | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-01.3 | Name | Text field | — | Decided | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-01.4 | Type Lib | Select | One Type Lib; can serve several Symbol Libs. | Decided | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-01.5 | Change the Type Lib | Select | The user clicks the Symbol Lib and changes it; may break symbols. | Decided | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |

Gaps:

- Rename, duplicate (to change a look over time, the user creates a new Symbol Lib: is it a copy of the old one?), delete.
- Is the user warned before a change of Type Lib that breaks symbols, with the number of broken links?

## SY-02 · Content of a Symbol Lib

Path: Symbols › a Symbol Lib.

```mermaid
mindmap
  root((SY-02 Symbol Lib))
    Dynamic symbols
    Static symbols
    Base pipe style
    Pipe styles
    Create a symbol
      Static or dynamic
      Type, if dynamic
    Proposed
      Usage counter
      Named colours
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-02.1 | Dynamic symbols, static symbols | List | Flat lists, never a tree. | Decided | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-02.2 | Base pipe style, pipe styles | List | See [Pipes](pipes.md). | Decided | [Pipe styles](../symbols/pipes/pipe-styles.md) |
| SY-02.3 | Create a symbol | Button + Dialog | Asks first: static or dynamic. | Decided | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-02.4 | Type | Select | For a dynamic symbol, before drawing: the types of the Type Lib; a parent not ticked is greyed. | Decided | [Libraries](../metadata/10-libraries.md) |
| SY-02.5 | Open a symbol | not said (click) | Opens the symbol editor. | Decided | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-02.6 | Broken mark | — | A small red mark on a broken item. | Decided | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-02.7 | Usage counter | — | "Used by 38 pipes", on symbols and styles. | Proposed | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-02.8 | Named colours | List | A flat list "Colours" that symbols and styles point to. | Proposed | [Fill and border](../symbols/04-drawing-mode/fill-and-border.md) |

Gaps:

- Name of a symbol: never mentioned. Search, sort, thumbnails in the lists?
- Duplicate, rename and delete a symbol.

## SY-03 · Symbol editor: what every mode shares

Path: Symbols › a Symbol Lib › a symbol.

The layout below is what the pages describe; the place of the mode switch and of the symbol settings is not said.

```mermaid
block-beta
    columns 3
    top["Mode switch, zoom field, advanced tools menu (three dots)"]:3
    tools["Tool bar of the mode"] canvas["Drawing area"] panel["Right-hand panel of the mode"]
    second["Second tool bar of an advanced tool, can be hidden"]:3
```

```mermaid
mindmap
  root((SY-03 Symbol editor))
    Modes
      SY-04 Drawing
      SY-05 Point editing
      SY-06 Alignment
      SY-07 Interaction
      SY-08 Animation
      SY-09 Run
      SY-10 Connection
    Symbol settings
      Static or dynamic
      Type
      Preset
      Faceplate entries ticked
    Moving around
      Hand tool
      Wheel and middle button
      Zoom field
    SY-11 Advanced tools
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-03.1 | Mode switch | not said | Drawing, Point editing, Alignment, Interaction, Animation, Run, Connection. Interaction, Animation and Run only for a dynamic symbol. | Decided (Connection: Proposed) | [Editor](../symbols/03-editor/README.md) |
| SY-03.2 | Static or dynamic | not said (toggle) | Switch at any time; nothing is deleted. | Decided | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| SY-03.3 | Type | Select | Changed in the symbol editor only, among the types of the Type Lib. | Decided | [Type, preset and faceplate](../symbols/02-type-and-faceplate.md) |
| SY-03.4 | Preset | Select | Then its defaults, display units, decimals, names and descriptions are edited here. | Decided | [Type, preset and faceplate](../symbols/02-type-and-faceplate.md) |
| SY-03.5 | Faceplate entries | Checkbox per entry | The full list is always there. | Decided | [Type, preset and faceplate](../symbols/02-type-and-faceplate.md) |
| SY-03.6 | Hand | Button (tool) | Moves the view; also the middle button held. In every mode. | Decided | [Hand](../symbols/03-editor/hand.md) |
| SY-03.7 | Zoom | Number field (%) | Shown in one place; the user can type a value; 100 % is the real size. | Decided | [Editor](../symbols/03-editor/README.md) |
| SY-03.8 | Select | Button (tool) | In every mode except Run; picks what the mode works on. | Decided | [Select](../symbols/03-editor/select.md) |
| SY-03.9 | Entirely enclosed | Toggle | Visible equivalent of Alt during a selection rectangle. | Decided | [Select](../symbols/03-editor/select.md) |
| SY-03.10 | Layer tree | Tree | Named by the fill and border page ("in the layer tree, the user sees one shape only"); never described. | Implied | [Fill and border](../symbols/04-drawing-mode/fill-and-border.md) |
| SY-03.11 | Undo, redo, save | not said | Listed as missing by the research. | Proposed | [Editor](../symbols/03-editor/README.md) |
| SY-03.12 | Grid, snapping, guides | not said | Minimum set proposed by the research. | Proposed | [Editor](../symbols/03-editor/README.md) |

Gaps:

- Where are the symbol settings (type, preset, faceplate entries): a mode of their own, a panel, a dialog?
- The layer tree: where, what each line shows (name, lock, hide, order), how a layer is named.
- Frame of the symbol (size, fit to content): proposed by the research, not placed in a screen.
- Where are the preset's defaults, display units and names edited in the symbol?

## SY-04 · Drawing mode

Path: symbol editor › Drawing (the default mode).

```mermaid
mindmap
  root((SY-04 Drawing))
    Tool bar
      Select
      Hand
      Group
      Rectangle
      Ellipse
      Polygon
      Pen
      Text
    Right-hand panel of a shape
      Fill
      Border
        Size
        Position
        Fill of the border
        Dash sequence
      Effects
      Mask
      Options of the shape
```

### Tool bar

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-04.1 | Tools | Button | In this order: Select, Hand, Group, Rectangle, Ellipse, Polygon, Pen, Text. | Decided | [Drawing mode](../symbols/04-drawing-mode/README.md) |
| SY-04.2 | Pen: straight line | Button | Turns the curve being drawn back into a straight line. | Decided | [Pen](../symbols/04-drawing-mode/pen.md) |
| SY-04.3 | Pen: angle lock | Toggle + Select | Step 15°, 30°, 45° or 90° (45° usual). | Decided (steps: Proposed) | [Pen](../symbols/04-drawing-mode/pen.md) |

### Panel of a shape: fill, border, effects

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-04.4 | Fill | not said (select + colour) | None, plain colour with opacity, linear gradient (stops, angle), radial gradient (stops, centre). | Proposed | [Fill and border](../symbols/04-drawing-mode/fill-and-border.md) |
| SY-04.5 | Border | not said (toggle) | A shape can have a border; a group cannot. | Decided | [Fill and border](../symbols/04-drawing-mode/fill-and-border.md) |
| SY-04.6 | Border size | Number field (px) | Example 2 px. | Decided | [Fill and border](../symbols/04-drawing-mode/fill-and-border.md) |
| SY-04.7 | Border position | Radio | Outside, middle, inside. An open path: middle only (proposed). | Decided | [Fill and border](../symbols/04-drawing-mode/fill-and-border.md) |
| SY-04.8 | Fill of the border | Same as the fill | Colour or gradient. | Decided | [Fill and border](../symbols/04-drawing-mode/fill-and-border.md) |
| SY-04.9 | Dashes of the border | Dash sequence editor | Segments, each a length and a colour, transparent for a gap (see [PI-04](pipes.md#pi-04--dash-sequence-editor)). | Decided | [Fill and border](../symbols/04-drawing-mode/fill-and-border.md) |
| SY-04.10 | Caps and joins | not said (radio) | Butt, round, square; miter, round, bevel. For open paths. | Proposed | [Fill and border](../symbols/04-drawing-mode/fill-and-border.md) |
| SY-04.11 | Effects menu | List + Button | Add, edit, remove; native SVG only; each effect kept only if it holds the performance. | Decided | [Effects and masks](../symbols/04-drawing-mode/effects-and-masks.md) |
| SY-04.12 | Effects offered | Select | Cut, gradients, dashes, colour change, drop shadow, blur, mask, inner shadow: each subject to the POC. | Proposed | [Effects and masks](../symbols/04-drawing-mode/effects-and-masks.md) |
| SY-04.13 | Mask | not said (select a shape) | The shape that cuts is chosen by the user. | Decided | [Effects and masks](../symbols/04-drawing-mode/effects-and-masks.md) |

### Panel of a shape: options by tool

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-04.14 | Rectangle: corner radius | Number field | For the whole rectangle. | Decided | [Rectangle](../symbols/04-drawing-mode/rectangle.md) |
| SY-04.15 | Rectangle, ellipse, polygon: link width and height | Toggle | Visible equivalent of the square or circle key. | Decided | [Rectangle](../symbols/04-drawing-mode/rectangle.md) |
| SY-04.16 | Polygon: number of sides | Number field | 3 to 20. | Decided | [Polygon](../symbols/04-drawing-mode/polygon.md) |
| SY-04.17 | Polygon: how it fills its box | Radio | Filled, Equilateral (a third mode "like Figma": Open, advised against). | Decided | [Polygon](../symbols/04-drawing-mode/polygon.md) |
| SY-04.18 | Polygon: anchor | not said (9-point grid) | An anchor of the box, and whether a corner or a side touches it. | Decided | [Polygon](../symbols/04-drawing-mode/polygon.md) |
| SY-04.19 | Group: width, height | Radio each | Fit or fixed; fixed gives a size. | Decided | [Group](../symbols/04-drawing-mode/group.md) |
| SY-04.20 | Group: placement of the children | not said (9-point grid) | Centred, or aligned left, right, top, bottom, with anchors; no flex. | Decided | [Group](../symbols/04-drawing-mode/group.md) |
| SY-04.21 | Child: absolute | Toggle + two anchors | Anchor of the group, anchor of the child. | Decided | [Group](../symbols/04-drawing-mode/group.md) |
| SY-04.22 | Group: create | Button (tool), Ctrl+G, right click "Group" | Three ways. | Decided | [Group](../symbols/04-drawing-mode/group.md) |

### Panel of a text

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-04.23 | Font family | Select | Fonts bundled with the software only (OFL proposed). | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.24 | Size | Number field | — | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.25 | Bold | Button | There by default, next to the weight list. | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.26 | Weight | Select | Every weight the font has. | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.27 | Italic | Button | Only when the font has a real italic. | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.28 | Text colour, background colour | Colour | — | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.29 | Text border | Toggle + size + colour | Native SVG stroke; the research says it is simple. | Decided (to keep: Open) | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.30 | Lines | Toggle each + colour | Underline, strikethrough, line above. | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.31 | Alignment | Radio | Left, centre, right; top, middle, bottom. | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.32 | Spacing | Number field each | Letter spacing, word spacing, line height. | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.33 | Wrapping | Toggle | Lines wrap in the box. | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.34 | Fit mode | Radio | Fit to the glyphs, or fit to the line. | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-04.35 | Embed the fonts | Toggle | In the exported SVG. | Decided | [Text](../symbols/04-drawing-mode/text.md) |

Gaps:

- Rotation and mirror of a shape: no control anywhere (the research proposes rotation as a property).
- Position and size (X, Y, width, height) of the selected shape: never listed as fields of the panel.
- Opacity of a whole shape or layer.
- Formatting part of a text ("format a part of it"): which options apply to a part, which to the whole text?
- Where is the "embed the fonts" option: on each text, or in the export?

## SY-05 · Point editing mode

Path: symbol editor › Point editing.

```mermaid
mindmap
  root((SY-05 Point editing))
    Tool bar
      Select
      Hand
      Pen
    Right-hand panel
      List of the points
      Selected point
        Mode
          Corner radius
          Handles
        Radius
        Mirroring
      Selected handle
        X and Y
        Angle and length
      Actions
        Remove
        Add a point between two
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-05.1 | Tools | Button | Select, Hand, Pen. | Decided | [Point editing mode](../symbols/05-point-editing-mode/README.md) |
| SY-05.2 | List of the points | List | Shape by shape; selecting in the list selects on the canvas and back. All shapes, or the selected ones: Open. | Decided | [Point editing mode](../symbols/05-point-editing-mode/README.md) |
| SY-05.3 | Point mode | Radio | Corner radius or Handles; each keeps its settings. An ellipse point: handles only. | Decided | [Points and handles](../symbols/05-point-editing-mode/points-and-handles.md) |
| SY-05.4 | Corner radius | Number field | — | Decided | [Points and handles](../symbols/05-point-editing-mode/points-and-handles.md) |
| SY-05.5 | Mirroring | Radio | None, Mirror angle, Mirror angle and length. | Decided | [Points and handles](../symbols/05-point-editing-mode/points-and-handles.md) |
| SY-05.6 | Handle X, Y | Number field | Linked to angle and length. | Decided | [Points and handles](../symbols/05-point-editing-mode/points-and-handles.md) |
| SY-05.7 | Handle angle, length | Number field | Linked to X and Y. | Decided | [Points and handles](../symbols/05-point-editing-mode/points-and-handles.md) |
| SY-05.8 | Remove | Button | Removes the selected points. | Decided | [Point editing mode](../symbols/05-point-editing-mode/README.md) |
| SY-05.9 | Add a point between two | Button | When two points are selected. | Decided | [Point editing mode](../symbols/05-point-editing-mode/README.md) |

Gaps:

- Position X, Y of a selected point: only the handles have fields.
- How the corner radius of a point is edited precisely: "to be detailed later".

## SY-06 · Alignment mode

Path: symbol editor › Alignment.

```mermaid
mindmap
  root((SY-06 Alignment))
    Tool bar
      Select
      Hand
    Alignment panel
      Reference shown
      Anchor
      Inside or outside
      Proposed
        Distribution with equal spacing
        Gap
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-06.1 | Tools | Button | Select, Hand. | Decided | [Alignment mode](../symbols/06-alignment-mode/README.md) |
| SY-06.2 | Reference | — | The first shape selected; the panel shows which one. | Decided | [Alignment mode](../symbols/06-alignment-mode/README.md) |
| SY-06.3 | Anchor | not said (9-point grid) | On a real shape: the centre and eight points on the outline (proposed). | Decided (anchors on a real shape: Proposed) | [Anchors](../symbols/03-editor/anchors.md) |
| SY-06.4 | Inside or outside | Radio | Placement on the limit of the reference. | Decided | [Alignment mode](../symbols/06-alignment-mode/README.md) |
| SY-06.5 | Distribution with equal spacing | Button + number field | A typed gap between the edges. | Proposed | [Alignment mode](../symbols/06-alignment-mode/README.md) |
| SY-06.6 | Apply | not said | Does the shape move as soon as an anchor is chosen, or on a button? | Implied | — |

Gaps:

- One anchor for all the shapes to place, or one each (Open).
- When does the placement happen: at once, or on an "Apply" button?

## SY-07 · Interaction mode

Path: symbol editor › Interaction (dynamic symbol only).

```mermaid
mindmap
  root((SY-07 Interaction))
    Tool bar
      Select
      Hand
      Interaction zone
    Panel of the selected place
      Interactions
        Place
        Gesture
        Effect
          Send a command
          Open the faceplate
      Proposed
        Disabled when
        Confirm before sending
        Tooltip
        Keyboard order
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-07.1 | Interaction zone | Button (tool) | Draws a zone by hand. | Decided | [Interaction mode](../symbols/07-interaction-mode/README.md) |
| SY-07.2 | Place | — | A drawn zone, the whole symbol, or a layer (its real shape). | Decided | [Interaction mode](../symbols/07-interaction-mode/README.md) |
| SY-07.3 | Interactions of the place | List | Several gestures per place. | Decided | [Interaction mode](../symbols/07-interaction-mode/README.md) |
| SY-07.4 | Gesture | Select | Click, double click, right click, while pressed, key (proposed list). | Decided (list: Proposed) | [Interaction mode](../symbols/07-interaction-mode/README.md) |
| SY-07.5 | Effect | Radio + Select | A command of the type (set a signal, trigger), or open the faceplate. | Decided | [Interaction mode](../symbols/07-interaction-mode/README.md) |
| SY-07.6 | Disabled when | Select (boolean output signal) | The place looks inactive and sends nothing. | Proposed | [Interaction mode](../symbols/07-interaction-mode/README.md) |
| SY-07.7 | Confirm before sending | Toggle | Off by default. | Proposed | [Interaction mode](../symbols/07-interaction-mode/README.md) |
| SY-07.8 | Tooltip | Text field | Plain text. | Proposed | [Interaction mode](../symbols/07-interaction-mode/README.md) |
| SY-07.9 | Keyboard order | not said | Order of the places reached with Tab. | Proposed | [Interaction mode](../symbols/07-interaction-mode/README.md) |

Gaps:

- For a typed-value command: the value is typed where (the faceplate, a text that becomes an input)?
- Remove an interaction; edit or delete a zone.

## SY-08 · Animation mode

Path: symbol editor › Animation (dynamic symbol only).

```mermaid
mindmap
  root((SY-08 Animation))
    Tool bar
      Select
      Hand
    Panel of the selected part
      Animations
        Signal
        Property
        Mapping
        Proposed
          Transition
          Pivot
      Text
        Shows the value
        Shows the unit only
        Show the unit
        Becomes an input
          Number input
          Text input
          Enum menu
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-08.1 | Animations of the part | List | The part is a shape, a layer or a text. | Decided | [Animation mode](../symbols/08-animation-mode/README.md) |
| SY-08.2 | Signal | Select | Output signals of the type only. | Decided | [Animation mode](../symbols/08-animation-mode/README.md) |
| SY-08.3 | Property | Select | Rotation, position, opacity, visibility, fill or border colour, fill level, blink (proposed list). | Proposed | [Animation mode](../symbols/08-animation-mode/README.md) |
| SY-08.4 | Mapping | Select + fields | Bounded linear (input range, output range), by ranges (table), two values (boolean), state table (enum). | Proposed | [Animation mode](../symbols/08-animation-mode/README.md) |
| SY-08.5 | Transition | Radio + number field | None, or a short linear duration. | Proposed | [Animation mode](../symbols/08-animation-mode/README.md) |
| SY-08.6 | Pivot | 9-point grid or a point | Centre by default. | Proposed | [Animation mode](../symbols/08-animation-mode/README.md) |
| SY-08.7 | Text: what it shows | Radio | Written text, the value of a signal, or the unit of a signal only. | Decided | [Text](../symbols/04-drawing-mode/text.md) |
| SY-08.8 | Text: show the unit | Toggle | With the value. | Decided | [Animation mode](../symbols/08-animation-mode/README.md) |
| SY-08.9 | Text: becomes an input | Radio + Select (command) | Number input, text input, or enum menu; sends a command. | Decided | [Animation mode](../symbols/08-animation-mode/README.md) |
| SY-08.10 | Number format | Toggles | Thousand separator, sign, leading zeros, notation. | Proposed | [Animation mode](../symbols/08-animation-mode/README.md) |

Gaps:

- Blink: its rate is fixed (proposed), but is it a property, or a mapping of a boolean?
- Remove an animation; two animations on the same property (proposed: forbidden, flagged).

## SY-09 · Run mode (name proposed: Test mode)

Path: symbol editor › Run (dynamic symbol only).

```mermaid
mindmap
  root((SY-09 Run))
    Tool bar
      Hand
    Test values
      Number input or slider
      Enum select
      Boolean switch
      Proposed
        Quality of each signal
    Simulated screen
      Size
      Resolution
      Proposed
        Scale factor of the system
    Simulation log
    Simulated faceplate
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-09.1 | Test value of a number | Number field or Slider | Within the bounds of the signal. | Decided | [Run mode](../symbols/09-run-mode/README.md) |
| SY-09.2 | Test value of an enum | Select | — | Decided | [Run mode](../symbols/09-run-mode/README.md) |
| SY-09.3 | Test value of a boolean | Toggle | — | Proposed | [Run mode](../symbols/09-run-mode/README.md) |
| SY-09.4 | Quality of a signal | Select | Good, uncertain, bad. | Proposed | [Run mode](../symbols/09-run-mode/README.md) |
| SY-09.5 | Simulated screen | Number fields (or a list of screens) | Size and resolution; scale factor proposed. | Decided | [Run mode](../symbols/09-run-mode/README.md) |
| SY-09.6 | Simulation log | List | A line per action: time, place, gesture, effect, value (proposed form). | Decided (form: Open) | [Run mode](../symbols/09-run-mode/README.md) |
| SY-09.7 | Simulated faceplate | Panel | Opens when an interaction opens the faceplate. | Decided (form: Open) | [Run mode](../symbols/09-run-mode/README.md) |

Gaps:

- A list of common screens, or only free fields?
- Clear the log; reset all the test values.

## SY-10 · Connection mode (proposed)

Path: symbol editor › Connection (assumption of the assistant).

```mermaid
mindmap
  root((SY-10 Connection))
    Tool bar
      Select
      Hand
      Connection point
    Panel of a point
      Position
      Direction
      Name
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-10.1 | Connection point | Button (tool) | Places a point where a pipe attaches. | Proposed | [Connection points](../symbols/pipes/connection-points.md) |
| SY-10.2 | Position | Number fields | — | Decided | [Connection points](../symbols/pipes/connection-points.md) |
| SY-10.3 | Direction | not said | The direction in which the pipe leaves the point. | Proposed | [Connection points](../symbols/pipes/connection-points.md) |
| SY-10.4 | Name | Text field | Inlet, outlet... | Open | [Connection points](../symbols/pipes/connection-points.md) |

Gaps:

- Is this mode also offered to static symbols (proposed: yes)?
- Size of the snapping zone.

## SY-11 · Advanced tools (name proposed; "Expert menu" today)

Path: symbol editor › three dots menu.

```mermaid
mindmap
  root((SY-11 Advanced tools))
    Menu with three dots
    Second tool bar
      Can be hidden
    Boolean operations
      Union
      Subtract
      Intersect
      Exclude
    Placement and duplication
      Polar
      Along a path
      Grid
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| SY-11.1 | Three dots menu | Button + menu | Lists every entry. | Decided | [Expert menu](../symbols/03-editor/expert-menu/README.md) |
| SY-11.2 | Second tool bar | — | Shows the tools of the entry; can be hidden. | Decided | [Expert menu](../symbols/03-editor/expert-menu/README.md) |
| SY-11.3 | Boolean operation | Button each | Union, subtract, intersect, exclude; the result is a new shape. | Decided (list: Proposed) | [Boolean operations](../symbols/03-editor/expert-menu/boolean-operations.md) |
| SY-11.4 | Duplication rule | Radio | Polar, along a path, grid. | Decided (polar, along a path), Proposed (grid) | [Placement and duplication](../symbols/03-editor/expert-menu/placement-and-duplication.md) |
| SY-11.5 | Duplication options | Number fields + Toggle | Count or spacing, start and end angle, copies rotated or not. | Proposed | [Placement and duplication](../symbols/03-editor/expert-menu/placement-and-duplication.md) |

Gaps:

- How the reference of a duplication is picked (a point and a radius, a line): with the mouse, in fields, or both?
- Preview of the copies before they are made?
