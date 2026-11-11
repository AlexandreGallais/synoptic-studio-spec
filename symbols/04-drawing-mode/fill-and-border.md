# Fill and border of a shape

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Fill and border

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

What every shape has in common: the [rectangle](rectangle.md), the [ellipse](ellipse.md) and the [polygon](polygon.md). They are set in the right-hand panel.

## Rules

- **Fill**: a shape has a background colour.
- **Border**: a shape can have a border, with its own colour, different from the fill.
- The border is not an SVG stroke. It is a fill, so that it can be placed **outside**, **in the middle** or **inside** the shape.
- The border is simulated. In the layer tree, the user sees one shape only. In the exported SVG, it is two different shapes: the shape and its border.
- A [group](group.md) has no fill and no border: a group does not do that, it only gives a structure. A shape keeps them, which keeps a little of the logic of SVG.
