# Fill and border of a shape

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Fill and border

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

What every shape has in common: the [rectangle](rectangle.md), the [ellipse](ellipse.md) and the [polygon](polygon.md). They are set in the right-hand panel.

## Rules

- A shape has a **fill** (its background) and can have a **border**.
- The border is not an SVG stroke. It is a fill, so that it can be placed **outside**, **in the middle** or **inside** the shape.
- The border is simulated. In the layer tree, the user sees one shape only. In the exported SVG, it is two different shapes: the shape and its border.
- A [group](group.md) has no fill and no border: a group does not do that, it only gives a structure. A shape keeps them, which keeps a little of the logic of SVG.

### What a fill can be

The background can be a plain colour, or a gradient. The border can be given the same kinds of fill as the background, so it can also be a gradient.

Proposed by the assistant, the Product Owner asked it to think of what can be offered. To confirm:

| Kind | Notes |
| --- | --- |
| Plain colour | With opacity. |
| Linear gradient | Several colour stops, an angle. |
| Radial gradient | Several colour stops, a centre. |
| None | No fill. |

### Border options

- **Size**: the width of the border, in pixels. Example: a border of 2 px.
- **Position**: outside, in the middle, or inside the shape.
- **Fill**: a colour or a gradient, as above.
- **Dashes**: the border can be dotted or dashed, as the user wants. The user types two values: the length of a dash and the space between two dashes. Example: dash 2, space 2.

### Dashes: what the research says

- Native SVG dashes (`stroke-dasharray`) exist only for a stroke. The border of the project is a fill, so two ways remain: keep a hidden stroke under the hood, or compute each dash as a small shape. The second is a geometric calculation redone at each resize, for the geometry research. Which one: to decide by the Product Owner.
- The cost follows the number of dashes (the perimeter divided by dash plus space). The editor needs a maximum number of dashes per shape, set by the POC (P8).
- No source gives the cost of a gradient or of its number of colour stops: a short POC (P8) is planned.

## What the second research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.18, 3.20). "Opinion" is the report's, not a decision.

### Open paths (lines drawn with the pen)

- SVG 2 has no inner or outer stroke. Opinion: an open path has no inside, so only the **middle** position makes sense; inside and outside are greyed out. Confidence: medium.
- Line caps: butt, round, square. Line joins: miter (with a limit, 4 by default, beyond which it becomes a bevel), round, bevel. Opinion: offer these three caps and three joins.
- A border "in the middle" looks exactly like a native stroke. Opinion: allowing a native stroke under the hood **in this case only** would settle at once the dashes, the caps and the joins, and leave to the computation only the inside and outside borders. Two ways of rendering to maintain.
- Arrows on a line: SVG markers exist (start, middle, end). Opinion: one single concept, the end shape of the Symbol Lib, for lines and pipes (see [Pipe ends](../pipes/ends.md)).

### Gradients

- The part of SVG 2 read defines linear and radial gradients, `spreadMethod` (pad, reflect, repeat) and a focal circle. Opinion: linear and radial; neither `spreadMethod` nor focal point in the first version. The absence of a conic gradient was not confirmed by the part read.

### Colours

| Subject | Sources | Opinion of the report |
| --- | --- | --- |
| HMI guides ("high-performance", ISA-101, known through secondary sources) | Grey background and muted colours; bright colours for the abnormal; never colour alone; alarm colours reserved; about seven colours safely told apart; some vendors defend realistic graphics. | Help without imposing: a "high-performance" palette by default; a contrast check; a warning when a colour reserved to alarms is used elsewhere. |
| Named colours | The archived Figma page gives each style its own colour value; Figma variables and Ignition style classes were not read. | A flat list "Colours" in the Symbol Lib; symbols, pipe styles and state tables point to it by identifier. Confidence: low. |
| Colour blindness | Colour cannot be the only way to carry information (WCAG level A). | In a state table, offer a second cue (shape, text); a colour-blind preview later. |
| Colour picker | The `EyeDropper` interface is experimental, not in every engine, secure contexts only. | Hex, HSL and opacity; an eyedropper of the editor itself, reading the colour of a shape of the drawing. |

## To decide by the Product Owner

1. Open paths: middle position only, three caps, three joins?
2. A native stroke allowed under the hood for a "middle" border (this also settles the dashes question above)?
3. Named colours in the Symbol Lib, and a "high-performance" palette by default?
