# Documentary research of the symbols part: brief

> [Home](../README.md) › [Symbols](README.md) › Research brief

Status: questions 1 to 4 were researched and the report is back (2026-11-11). Its answers are written in the pages concerned, under "What the research found". Questions 5 and 6 and the questions of the pages not discussed yet are not sent.

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

## What the report leaves open

Written as questions to the Product Owner in the pages: the desktop window and the browsers to hold (effects page), the dashes of a fill-based border (fill and border page), the third polygon mode and the anchors on corners (polygon page). The key of "entirely enclosed" is settled (Alt), and every key follows the cross-platform rule of the editor page. The measures come from the POC plan P0 to P8 (effects page).

## What stays out of the research

The code, the performance measures (they come from the POC), the geometric engine and the intersection calculations (another research), the SaaS, phones and tablets, and the final choice of effects (the Product Owner decides, on the report and the POC).
