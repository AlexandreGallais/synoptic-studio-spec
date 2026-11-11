# Documentary research of the symbols part: brief

> [Home](../README.md) › [Symbols](README.md) › Research brief

Status: questions 1 to 4 were researched and the report is back (2026-11-11). Its answers are written in the pages concerned, under "What the research found". Questions 5 to 12 and the questions of the pages not discussed yet are not sent.

Where the report is: in the `synoptic-studio-spec` project, folder `research/t1-recherche-documentaire-claude-desktop-effets-svg/` (`rapport.md`, annexes beside it). That folder is ignored by Git.

## Questions and where the answers are

| Question | Answers in |
| --- | --- |
| 1. Which SVG effects keep the performance | [Effects and masks](04-drawing-mode/effects-and-masks.md), [Fill and border](04-drawing-mode/fill-and-border.md) |
| 2. How a polygon is placed in its box | [Polygon tool](04-drawing-mode/polygon.md) |
| 3. Handle mirroring: names and list | [Points and handles](05-point-editing-mode/points-and-handles.md) |
| 4. Modifier keys | [Select](03-editor/select.md), [Rectangle](04-drawing-mode/rectangle.md), [Pen](04-drawing-mode/pen.md) |

## Not researched yet

### 5. Fonts: licences, weights, italic, baseline fit

- Context: see [Text tool](04-drawing-mode/text.md). Only fonts bundled with the software are offered, chosen among fonts free to be put in SVG files, with an option to embed them in the exported SVG.
- Question: which open fonts can be bundled and embedded in an SVG under their licence? How can the weights and the italic that a font really offers be read? How do software and browsers compute a text box that fits the baseline (ascent, descent, "trim") rather than the glyphs? Can SVG text carry a native stroke in every engine?

### 6. Interaction: the list of gestures and the name of the concept

Asked by the Product Owner (2026-11-11): the assistant must answer these two points itself, in its research, without asking the Product Owner. No priority: it goes in the next research that is launched, whatever it is. Noted here so that it is not forgotten.

- Context: see [Interaction mode](07-interaction-mode/README.md). An interaction links a place, a gesture and what happens (a command, or opening the faceplate). The Product Owner wants more gestures than left click, right click and double click.
- Question 6a: which gestures do supervision (SCADA, HMI), design and prototyping software offer on an element (click, double click, right click, hover, long press, drag, wheel, key...), which ones exist on every desktop platform and in a browser, and which ones should the list hold? Propose a list, labelled as an opinion.
- Question 6b: how do these tools name the concept "when a gesture is done on a place, something happens" (interaction, event, trigger, action, behaviour...) and the gesture itself? Metadata already uses "trigger" for a kind of command: the name must not be confused with it. Propose names, with sources, labelled as an opinion.

### 7. Animation: animatable properties, mapping, enum

Asked by the Product Owner (2026-11-11), who does not want to read the animation page and its open questions: the assistant answers them in its next research and proposes. No priority, same rule as question 6.

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
- Names to review (see the index of open questions): layer, interaction, gesture, zone, symbol mode, static and dynamic.
- Anything that looks missing in the part compared with the symbol editors of SCADA and HMI software (grouping of symbols in a synoptic, symbol variants, states with a look each, templates, import of an SVG, export, undo and redo, grid and snapping, rulers and guides, shortcuts, accessibility). Propose a list, labelled as an opinion.

## What the report leaves open

Written as questions to the Product Owner in the pages: the desktop window and the browsers to hold (effects page), the dashes of a fill-based border (fill and border page), the third polygon mode and the anchors on corners (polygon page). The key of "entirely enclosed" is settled (Alt), and every key follows the cross-platform rule of the editor page. The measures come from the POC plan P0 to P8 (effects page).

## What stays out of the research

The code, the performance measures (they come from the POC), the geometric engine and the intersection calculations (another research), the SaaS, phones and tablets, and the final choice of effects (the Product Owner decides, on the report and the POC).
