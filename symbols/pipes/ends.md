# Pipe ends

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Pipe ends

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

A start shape and an end shape can be set on a pipe. They are created in the Symbol Lib and chosen in the synoptic.

## Rules

- An end shape is drawn in a small editor of its own: a **box** of the size the user wants, with an **anchor** at each side and each corner of the box (see [Anchors](../03-editor/anchors.md)).
- The user draws the shape freely inside the box, with the tools of the [drawing mode](../04-drawing-mode/README.md).
- The anchor says where the pipe is attached to the shape, and so how the shape is placed on the end of the pipe.
- The fill of the shape follows the colour of the pipe: when the pipe changes style, the end changes colour with it.
- A pipe can have a start shape, an end shape, both, or none. The start and the end can be different shapes.

## Example

| End shape | Drawn as | Anchor |
| --- | --- | --- |
| Arrow | A triangle | Middle of the back side |
| Flange | A thin rectangle across the pipe | Middle of the box |
| Cap | A half circle | Middle of the flat side |

## Open questions

- Is the whole shape filled with the pipe colour, or only the parts the user marks (so that a border stays its own colour)?
- Does the end shape rotate with the last segment of the pipe, and can it be mirrored?
- Is the end shape a symbol of the lib (a static symbol with a connection point) or a separate kind of object?
- Does the end shape change the length of the pipe, or does it sit on top of the end?
