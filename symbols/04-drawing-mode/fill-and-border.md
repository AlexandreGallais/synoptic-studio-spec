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
