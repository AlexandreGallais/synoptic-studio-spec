# Drawing mode

> [Home](../../README.md) › [Symbols](../README.md) › Drawing mode · Previous: [Editor](../03-editor/README.md) · Next: [Point editing mode](../05-point-editing-mode/README.md)

Status: draft. Not validated.

The default mode of the [editor](../03-editor/README.md): draw and arrange shapes.

## Rules

- Tool bar: [Select](../03-editor/select.md), [Hand](../03-editor/hand.md), then in this order: [Group](group.md), [Rectangle](rectangle.md), [Ellipse](ellipse.md), [Polygon](polygon.md), [Pen](pen.md), [Text](text.md). The order: groups, then the basic shapes, then the pen, then the text.
- The Group, Rectangle, Ellipse, Polygon, Pen and Text tools exist only in this mode (the Pen is also in the point editing mode).
- Right-hand panel: the options of the selected shape (colours, corner radius, effects...).
- Everything drawn becomes a path, except a text, which stays a text.
- Every shortcut has a visible equivalent (see the [editor](../03-editor/README.md)).

## Tools of this mode

| Tool | What it does |
| --- | --- |
| [Group](group.md) | Creates a group (an SVG `g`), fit to its content or with its own size, with a layout of its children. |
| [Rectangle](rectangle.md) | Draws a rectangle, with a corner radius. 4 points. |
| [Ellipse](ellipse.md) | Draws an oval or a circle. 4 points, no corner radius. |
| [Polygon](polygon.md) | Draws a polygon of 3 to 20 sides, with anchors. One point per side. |
| [Pen](pen.md) | Draws a path point by point, and lines. Two buttons: straight line, angle lock. |
| [Text](text.md) | Writes a text, written or linked to a signal or to its unit. |

## What shapes have in common

The rectangle, the ellipse and the polygon share the same pages.

| Page | What it holds |
| --- | --- |
| [Fill and border](fill-and-border.md) | Colour or gradient, border (not an SVG stroke) outside, in the middle or inside, size, dashes. A group has neither. |
| [Effects and masks](effects-and-masks.md) | Only native SVG effects and masks, kept only if they keep the performance. |
| [Points and handles](../05-point-editing-mode/points-and-handles.md) | In the point editing mode: corner radius or handles per point, mirroring, angle and length. |
