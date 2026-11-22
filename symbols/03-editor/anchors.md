# Anchors

> [Home](../../README.md) › [Symbols](../README.md) › [Editor](README.md) › Anchors

Status: draft, written by the assistant to put one word for one idea. Not validated.

The word "anchor" is used by several pages. They all mean the same thing, and this page says it once.

## Rules

- An **anchor** is a named point of the box of an element, used to say where something is placed in relation to that element.
- A box has nine anchors: the four corners, the four middles of the sides, and the centre.
- Two anchors are used together: an anchor of one element and an anchor of another (or of the same box). Example: the bottom left corner of a child on the top right corner of its group.

| Page | What the anchor is used for |
| --- | --- |
| [Group](../04-drawing-mode/group.md) | Place an absolute child on the group, and the children in a group with its own size. |
| [Polygon](../04-drawing-mode/polygon.md) | Place the polygon in its box: a corner or a side touches the anchor. |
| [Alignment mode](../06-alignment-mode/README.md) | Place the shapes to place on the reference, inside or outside. |
| [Pipe ends](../pipes/ends.md) | Say where the pipe is attached to the end shape. |

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, section 3.15). No tool read aligns on the real outline of a shape. Opinion of the report: on a real shape, the anchors are **the centre, plus the eight points where a ray from the centre (top, bottom, left, right, diagonals) meets the outline**. On a rectangle, the four middles match; the corners differ when the rectangle is rounded.

## Open questions

- Anchors on a real shape: the proposal above, to confirm (see [Alignment mode](../06-alignment-mode/README.md)).
- Whether the anchors are always nine, or if the user can add their own.
