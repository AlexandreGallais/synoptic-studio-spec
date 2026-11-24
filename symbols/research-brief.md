# Documentary research of the symbols part: brief

> [Home](../README.md) › [Symbols](README.md) › Research brief

Status: both researches are back (2026-11-11). Questions 1 to 4: first report. Questions 5 to 22: second report. Their answers are written in the pages concerned, under "What the research found", with what is left to the Product Owner under "To decide by the Product Owner".

Where the reports are, in the `synoptic-studio-spec` project (folders ignored by Git, `rapport.md` and annexes beside it):

- first report: `research/t1-recherche-documentaire-claude-desktop-effets-svg/`;
- second report: `research/t4-recherche-documentaire-claude-desktop-partie-symboles/`.

## Questions and where the answers are

| Question | Answers in |
| --- | --- |
| 1. Which SVG effects keep the performance | [Effects and masks](04-drawing-mode/effects-and-masks.md), [Fill and border](04-drawing-mode/fill-and-border.md) |
| 2. How a polygon is placed in its box | [Polygon tool](04-drawing-mode/polygon.md) |
| 3. Handle mirroring: names and list | [Points and handles](05-point-editing-mode/points-and-handles.md) |
| 4. Modifier keys | [Select](03-editor/select.md), [Rectangle](04-drawing-mode/rectangle.md), [Pen](04-drawing-mode/pen.md) |
| 5. Fonts | [Text tool](04-drawing-mode/text.md) |
| 6. Gestures and name of the concept | [Interaction mode](07-interaction-mode/README.md) |
| 7. Animatable properties, mapping, enum | [Animation mode](08-animation-mode/README.md) |
| 8 to 11. Pipes | [Pipes](pipes/README.md) and its pages |
| 12. The assistant's questions | [Editor](03-editor/README.md), [Anchors](03-editor/anchors.md), [Select](03-editor/select.md), [Point editing mode](05-point-editing-mode/README.md), [Group](04-drawing-mode/group.md), [Animation mode](08-animation-mode/README.md), [Run mode](09-run-mode/README.md), [Connection points](pipes/connection-points.md) |
| 13. Libraries | [Libraries and symbols](01-libraries-and-symbols.md) |
| 14. Geometry of a symbol | [Editor](03-editor/README.md) |
| 15. Open paths | [Fill and border](04-drawing-mode/fill-and-border.md), Pipe ends (page removed, decision 0098) |
| 16. Boolean operations, duplication, distribution | [Boolean operations](03-editor/expert-menu/boolean-operations.md), [Placement and duplication](03-editor/expert-menu/placement-and-duplication.md), [Alignment mode](06-alignment-mode/README.md) |
| 17. Colours | [Fill and border](04-drawing-mode/fill-and-border.md) |
| 18. Texts that show a value | [Animation mode](08-animation-mode/README.md), [Text tool](04-drawing-mode/text.md) |
| 19. Animation, more | [Animation mode](08-animation-mode/README.md) |
| 20. Interaction, more | [Interaction mode](07-interaction-mode/README.md) |
| 21. Symbol file and SVG export | [Editor](03-editor/README.md) |
| 22. Desktop window | [Effects and masks](04-drawing-mode/effects-and-masks.md) |

## What the second report could not answer

- The texts of ISA-101, ISA-18.2, ISA-5.1, ISO 14617, EN 60617, ISO 10628, EEMUA 201, NUREG-0700: paid standards, not opened; what can be taken from the symbol standards without a copyright problem stays open.
- AVEVA and Siemens documentation (not readable or not reached); the connectors of Inkscape and FigJam.
- Key conflicts (Alt and Linux window managers, Ctrl+G in browsers); grid and snapping, HMI number format strings, colour variables: no source read.
- DEXPI terms (P&ID exchange): seen only in search results.

## The questions as they were sent

### 5. Fonts: licences, weights, italic, baseline fit

- Context: see [Text tool](04-drawing-mode/text.md). Only fonts bundled with the software are offered, chosen among fonts free to be put in SVG files, with an option to embed them in the exported SVG.
- Question: which open fonts can be bundled and embedded in an SVG under their licence? How can the weights and the italic that a font really offers be read? How do software and browsers compute a text box that fits the baseline (ascent, descent, "trim") rather than the glyphs? Can SVG text carry a native stroke in every engine?

### 6. Interaction: the list of gestures and the name of the concept

The research answers these two points itself, with no question back. No priority: it goes in the next research that is launched, whatever it is.

- Context: see [Interaction mode](07-interaction-mode/README.md). An interaction links a place, a gesture and what happens (a command, or opening the faceplate). The Product Owner wants more gestures than left click, right click and double click.
- Question 6a: which gestures do supervision (SCADA, HMI), design and prototyping software offer on an element (click, double click, right click, hover, long press, drag, wheel, key...), which ones exist on every desktop platform and in a browser, and which ones should the list hold? Propose a list, labelled as an opinion.
- Question 6b: how do these tools name the concept "when a gesture is done on a place, something happens" (interaction, event, trigger, action, behaviour...) and the gesture itself? Metadata already uses "trigger" for a kind of command: the name must not be confused with it. Propose names, with sources, labelled as an opinion.

### 7. Animation: animatable properties, mapping, enum

The research answers the open questions of the animation page and proposes. No priority, same rule as question 6.

- Context: see [Animation mode](08-animation-mode/README.md). A signal animates a shape, a layer or a text.
- Question 7a: which properties of an SVG drawing can a signal drive, with a good performance and natively in SVG (rotation, position, size, colour, opacity, visibility, blinking, dash offset, gradient...)? Which ones to refuse? Propose a list, labelled as an opinion.
- Question 7b: which shapes of mapping from a value to a property do supervision and animation software offer (linear, with clamp, by steps or thresholds, curve, table of points...)? Which ones to offer?
- Question 7c: how is an enum animated (a look per value, a table value to property, a state machine...)? How do the tools of the field name these things?

### 8. Pipes: how other software models them

Context: [Pipes](pipes/README.md) and its pages. The Figma page "Flow Pipes" of the design system file holds, according to the Product Owner, everything about the look wanted: it must be read too, if the tool allows it.

- Question 8a: how do supervision and drawing software (SCADA and HMI editors, P&ID tools, Visio, draw.io, Inkscape connectors, Figma) model connection points on a symbol, junctions, crossings (line jumps, bridges, gaps), the order of two crossing lines, and the start and end shapes of a line?
- Question 8b: which names and which options do they use for a pipe style by content (water, oil, steam, electricity)? Which standards of colours and symbols exist (ISA 5.1, ISO 14617, EN 60617, ANSI) and what can be taken from them without copyright problems?
- Question 8c: what do they do that the Product Owner's list lacks? Propose, labelled as an opinion.

### 9. Pipes: computing them

- Question 9a: how to compute, in plain JavaScript, a thick polyline with rounded corners, borders on both sides, bridges and gaps at crossings, junctions (circle or square), and end shapes? Which classic algorithms (offset of a polyline, joins, arc fitting, segment intersection) and which edge cases (very short segments, close parallel pipes, three or more pipes at a point)?
- Question 9b: what does it cost with hundreds of pipes and thousands of crossings, in the browser, at 8.3 ms per frame during a gesture? What must be recomputed when one point moves, and what can be cached? What to hand to the geometry research (intersections, WebAssembly)?
- Question 9c: how are bridges and gaps made look good when the corner radius changes (a bridge as round as the pipe radius, a gap always the same)?

### 10. Pipes: flow dashes and animation

- Question 10a: how are dashes that travel from the start of a pipe to its end animated natively in SVG (dash offset, CSS animation, SMIL) with a good performance for many pipes? Which engines refuse it? Does it need a stroke, and how does that fit the rule "a border is a fill, not a stroke"?
- Question 10b: how do other tools drive the look of a pipe from a model (a colour by content or by state, a direction by flow, hot or cold)? Propose which signals could drive a pipe, labelled as an opinion.

### 11. Pipes: vocabulary

- Question 11: how do the standards and the tools name "what a pipe contains" (content, fluid, medium, service, line type), a "junction" (tee, branch, node, joint), a "crossing" (jump, bridge, hop, overpass), a "connection point" (port, terminal, nozzle, connector, snap point), a "pipe style", and the start and end of a line (terminator, arrowhead, end cap)? Propose names, with sources, labelled as an opinion.

### 12. The whole symbols part: the assistant's own questions

Written after a full pass over the part (2026-11-11). They are not for the Product Owner: the research answers them, with options and opinions.

- Anchors: what is an anchor on a real shape (a circle, a free form) for the alignment? How do other tools place a shape against the outline of another, inside and outside (Figma, Illustrator "align to key object", Sketch, Penpot, CAD snaps)?
- Hit area: how do drawing tools define the clickable area of a shape with a transparent fill (pointer-events in SVG, Figma, Inkscape)? What does it cost to compute a hit test on a real outline in JavaScript at 8.3 ms?
- Free form: what do other tools do when a rectangle, an ellipse or a polygon gets or loses a point (Figma, Illustrator "expand", Sketch "convert to path")? Which options of the former shape should stay and which go?
- Points list: how do other tools list the points of a selection in a panel (Figma "vector" panel, Illustrator, Inkscape XML editor and node tool)? All the shapes or the selected ones? What about performance with thousands of points?
- Interaction in the Run mode: how do prototyping tools (Figma prototype, Framer) and HMI tools simulate an interaction without a model, with a log of the actions?
- Faceplate: how do supervision tools open a faceplate (pop-up, side panel, window), and what is the usual difference between a read-only one and one with commands?
- Text as an input: how do HMI tools turn a displayed value into an input on click (number with a keypad, slider, enum menu), and what are the pitfalls (focus, validation, bounds, units)? How is it done in an SVG `foreignObject` in all engines?
- Run mode screen simulation: how do tools simulate another screen size and density (device frames, zoom, scroll)? Is a size and density list enough?
- Hierarchy: groups, layers, absolute children and the layout "centred or aligned with anchors" without flex: which tools do this, and is it enough for real symbols?
- Keys: for each action of the specs with a key, which keys exist on every platform (Shift, Ctrl, Alt) without a conflict with the operating systems or the browser (Ctrl+G, Alt in browsers, Alt in Linux window managers)?
- Static symbols: do they need connection points? Do they need names, tags, categories? How do other tools separate "decor" and "equipment"?
- Names to review (see the index of open questions): layer, interaction, gesture, zone, symbol mode, static and dynamic, and also expert menu, free form, corner radius mode, fit and fixed, absolute child, reference and shapes to place, interaction zone, connection mode, test display, Run mode. Propose names, with sources, labelled as an opinion; the names settled in decision 0002 (Signal, Command, Trigger, Faceplate, Preset, Quantity) and "Symbol Lib", "Type Lib" are not reopened.
- Anything that looks missing in the part compared with the symbol editors of SCADA and HMI software (grouping of symbols in a synoptic, symbol variants, states with a look each, templates, import of an SVG, export, undo and redo, grid and snapping, rulers and guides, shortcuts, accessibility). Propose a list, labelled as an opinion.

### 13. Libraries: placed symbols, updates, broken links, signal quality

- Context: [Libraries and symbols](01-libraries-and-symbols.md). A look changes over time by creating a new Symbol Lib; a broken link shows a small red mark, with no automatic repair.
- Question 13a: how do supervision tools (Ignition, WinCC Unified, AVEVA, FactoryTalk View, zenon, PcVue...) link a symbol placed in a screen to the symbol of its library: a linked instance updated everywhere, a copy, or both? How do they version a library or a symbol?
- Question 13b: how do they show a broken binding (missing signal, wrong type) while editing and while running?
- Question 13c: do they show the quality of a value on a symbol (OPC UA status good, uncertain, bad; stale value; lost connection), and how? Should the animation offer it? Labelled as an opinion.

### 14. Geometry of a symbol: frame, scaling, rotation, crisp rendering

- Context: [Editor](03-editor/README.md), [Select](03-editor/select.md) (resizing never applies a scale), [Group](04-drawing-mode/group.md).
- Question 14a: how do editors define the frame of a symbol (fixed artboard or fit to content, origin, `viewBox`, units)?
- Question 14b: when a placed symbol is resized in a screen, do tools scale it (transform) or lay it out again? How do they keep border widths and text sizes (constraints like Figma's left, right, centre, scale; scale modes of HMI tools)? How does this fit the rule "resizing never applies a scale" and the anchors of groups?
- Question 14c: the specs say nothing about rotating or flipping a shape. How do tools store a rotation (a property, or baked into the path), and what happens to the box, the anchors, the corner radius and the "no transform" rule?
- Question 14d: crisp lines: half-pixel alignment of odd widths, snap to the pixel grid, `shape-rendering`, high-density screens. What do editors offer?
- Question 14e: grid, snapping (points, edges, centres, guides), rulers, guides, smart guides, moving with the arrows: what is the usual set, and what is the minimum for a symbol editor? Labelled as an opinion.

### 15. Open paths and lines

- Context: [Pen](04-drawing-mode/pen.md) (also the tool for lines), [Fill and border](04-drawing-mode/fill-and-border.md) (a border is a fill, inside, middle or outside).
- Question 15a: what is the border of an open path, which has no inside? How do Figma (centre only for an open path), Illustrator and Inkscape handle it?
- Question 15b: line caps (butt, round, square) and joins (miter, round, bevel, miter limit) are not in the specs. Which ones to offer, and how do they fit a fill-based border (hidden stroke or computed outline, as for dashes)?
- Question 15c: arrowheads on a line drawn in a symbol: offered by tools? Linked with the pipe ends?

### 16. Boolean operations, duplication, distribution

- Context: [Boolean operations](03-editor/expert-menu/boolean-operations.md), [Placement and duplication](03-editor/expert-menu/placement-and-duplication.md), [Alignment mode](06-alignment-mode/README.md).
- Question 16a: which boolean operations do drawing tools offer (union, subtract, intersect, exclude, divide, trim, merge, crop, outline...), under which names? Live (Figma) or destructive (Illustrator Pathfinder)? What happens to the fill, border and effects of the result? Propose a list, labelled as an opinion.
- Question 16b: which duplication rules exist (polar, along a path, grid: AutoCAD arrays, Illustrator Transform Each and Repeat, Inkscape Arrange and Clone tiler, Affinity Power duplicate), with which options (count, spacing, start and end angle, copies turned along the path)? Are the copies linked or independent? Labelled as an opinion.
- Question 16c: tools offer "distribute" (equal spacing) next to "align". Is it missing from the alignment mode?

### 17. Colours, named colours, HMI style guides

- Context: [Fill and border](04-drawing-mode/fill-and-border.md), [Pipe styles](pipes/pipe-styles.md), [Libraries and symbols](01-libraries-and-symbols.md).
- Question 17a: what do ISA-101 (high-performance HMI) and the other guides (ASM, EEMUA 201, NUREG-0700) say about symbol design: grey backgrounds, colour kept for alarms and abnormal states, limited animation, blinking? What can an editor offer to help? Labelled as an opinion.
- Question 17b: should the Symbol Lib hold named colours (colour styles, variables) that symbols and pipe styles point to, so that a factory changes one colour everywhere (Figma variables, Ignition style classes, WinCC palettes)? Labelled as an opinion.
- Question 17c: colour-blind safety of red and green states and of pipe content colours.
- Question 17d: colour picker: colour formats (hex, HSL, opacity), the eyedropper in a browser (EyeDropper API, not in every engine).
- Question 17e: gradient kinds native in SVG: linear and radial only (no conic; mesh gradients dropped from SVG 2)? Which options are worth offering (spread, focal point)?

### 18. Texts that show a value

- Context: [Text tool](04-drawing-mode/text.md), [Animation mode](08-animation-mode/README.md). Decimals and display units come from the preset.
- Question 18a: how do HMI displays format a number: thousand separators, locale (decimal comma), sign, leading zeros, scientific notation, format strings ("#,##0.00")?
- Question 18b: what does a text show when the value is missing, out of bounds, not a number, or too long for its box ("####", "---", ellipsis, shrink to fit)?
- Question 18c: text along a path, vertical text: offered, needed?
- Question 18d: translatable texts in symbols (multi-language screens, as in WinCC): in the scope or not? Labelled as an opinion.

### 19. Animation: beyond question 7

- Context: [Animation mode](08-animation-mode/README.md).
- Question 19a: when a value changes, does the drawing jump or move smoothly (interpolation, duration)? What do HMI tools do with irregular update rates?
- Question 19b: the pivot of a rotation or a scale: centre, anchor, or a point chosen by the user? How do tools set it?
- Question 19c: two animations on the same property: which wins (priority, last one, combination)?
- Question 19d: blinking: rates in the alarm guides (ISA-101, ISA-18.2), the WCAG limit of three flashes per second, the "reduced motion" preference of the system.
- Question 19e: many animated symbols in one screen: what the sources say about the cost of CSS transforms, SVG attribute changes and SMIL (no measure: it goes to the POC plan).

### 20. Interaction: beyond question 6

- Context: [Interaction mode](07-interaction-mode/README.md).
- Question 20a: feedback on an interactive place: highlight on hover, cursor shape, pressed state, disabled state when the command cannot be sent, tooltip. What do HMI tools do?
- Question 20b: confirmation of sensitive commands (select then confirm, "are you sure?"): usual practice in HMI guides? Should an interaction have a "confirm" option? Labelled as an opinion.
- Question 20c: keyboard access to the interactions of a symbol (reach with Tab, act with Enter or Space), SVG accessibility (focus, role, label), WCAG. What must the specs require? Labelled as an opinion.

### 21. Symbol file and SVG export

- Context: [Editor](03-editor/README.md) (the symbol stays a real SVG), [Fill and border](04-drawing-mode/fill-and-border.md) (the border is two shapes in the export), [Storage](../storage/README.md).
- Question 21a: how do editors keep their own data in an SVG and still give a real SVG (Inkscape namespace, `data-*` attributes, `<metadata>`, a JSON file beside it)? What survives other tools?
- Question 21b: which SVG features import well in other HMI tools (Ignition, WinCC Unified, AVEVA): SVG 1.1 or 2, filters, `foreignObject`, embedded fonts? What to avoid for a portable export?
- Question 21c: import of an SVG made elsewhere (Inkscape, Illustrator, draw.io): what is converted (strokes, transforms, CSS, `use`, text) and what is lost? Is import worth having? Labelled as an opinion.

### 22. Desktop window: Chromium without Electron?

- Context: [Effects and masks](04-drawing-mode/effects-and-masks.md), question 1 of "To decide". The Product Owner postponed the choice; he wants the lightest and simplest to maintain for an open source application, and wonders whether Chromium can be used without Electron.
- Question 22: which options exist (Electron; Tauri with the system view, which is Chromium through WebView2 on Windows and WebKit elsewhere; a Chromium or CEF backend for Tauri, and its status; CEF directly; NW.js; Wails; Neutralino; a web app installed from Chrome or Edge)? For each: engine per system, size, updates, maintenance, licence, and what the first report says about GPU filters and 120 Hz. Options and an opinion, no decision.

## Order of treatment

The research answers every question. If its budget runs short, it follows this order and lists what is left in "Open questions": pipes (8 to 11), interaction (6, 20), animation (7, 19), the assistant's questions (12), libraries (13), geometry (14), open paths (15), colours (17), texts (18), boolean operations and duplication (16), symbol file (21), fonts (5), desktop window (22).

## What the first report leaves open

Written as questions to the Product Owner in the pages: the desktop window and the browsers to hold (effects page), the dashes of a fill-based border (fill and border page), the third polygon mode and the anchors on corners (polygon page). The key of "entirely enclosed" is settled (Alt), and every key follows the cross-platform rule of the editor page. The measures come from the POC plan P0 to P8 (effects page).

## What stays out of the research

The code, the performance measures (they come from the POC), the geometric engine and the intersection calculations (another research), the SaaS, phones and tablets, and the final choice of effects.
