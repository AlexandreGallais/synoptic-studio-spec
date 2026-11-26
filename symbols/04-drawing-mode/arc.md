# Arc tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Arc

Status: draft. Not in V1: kept for a later version (Product Owner, 2026-11-26: "l'arc, on va pas le mettre dans cette version [...] par contre, c'est une super option"). Not validated.

## Rules

- Draws an arc: an ellipse drawn only from a **start angle** to an **end angle** ("c'est une ellipse, sauf qu'on peut lui donner un angle de début, un angle de fin").
- **Place**: in the tool bar of the drawing mode, right after the [Ellipse](ellipse.md).
- **Thickness**: the width of the ring.
- **Fill and border**: the ones every shape has (see [Fill and border](fill-and-border.md)); a border only when needed.
- **Track**: behind the arc, a ring of another colour, from one angle to another ("le background, il est de telle couleur, de tel angle à tel angle").
- **Why a shape**: the ring gauge of the [catalogue of the animations](../08-animation-mode/animation-catalogue.md#not-in-v1-kept-for-later) (row 8, Arc) cannot really be split from its shape; a shape of its own is the simplest (Product Owner, 2026-11-26).

## Where it is used

| Screen | Element |
| --- | --- |
| [SY-04](../../screens/symbols.md#sy-04--drawing-mode) | SY-04.1, tools: Arc after Ellipse, not in V1 |
| [Catalogue of the animations](../08-animation-mode/animation-catalogue.md#not-in-v1-kept-for-later) | Row 8, Arc, kept for later |

## Open questions

- A signal that moves the end angle (a ring gauge): an animation of this shape, the animation Arc kept, or both?
- Once drawn, does the arc become a path like the other shapes, or keep its angles so that they stay editable?
- The track: one range of angles only, or several?
