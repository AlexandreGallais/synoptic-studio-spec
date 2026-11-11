# Drawing mode

> [Home](../../README.md) › [Symbols](../README.md) › Drawing mode · Previous: [Editor](../03-editor/README.md) · Next: [Point editing mode](../05-point-editing-mode/README.md)

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

The default mode of the [editor](../03-editor/README.md): draw and arrange shapes.

## Rules

- Tool bar: [Select](../03-editor/select.md), [Hand](../03-editor/hand.md), then in this order: [Group](group.md), [Rectangle](rectangle.md), [Ellipse](ellipse.md), [Polygon](polygon.md), [Pen](pen.md), [Text](text.md).
- The order is the one the Product Owner chose: groups, then the basic shapes (rectangle, ellipse, polygon), then the pen, then the text.
- The Group, Rectangle, Ellipse, Polygon, Pen and Text tools exist only in this mode (the Pen is also in the point editing mode).
- Right-hand panel: the options of the selected shape (colours, corner radius...).
- Everything drawn becomes a path, except a text, which stays a text.

## Tools of this mode

| Tool | What it does |
| --- | --- |
| [Group](group.md) | Gathers shapes in a group, which can have a layout. |
| [Rectangle](rectangle.md) | Draws a rectangle, with a corner radius. |
| [Ellipse](ellipse.md) | Draws an oval or a circle. |
| [Polygon](polygon.md) | Draws a polygon of 3 to 20 sides. |
| [Pen](pen.md) | Draws a path point by point, and lines. |
| [Text](text.md) | Writes a text, which can show a value or a unit. |
