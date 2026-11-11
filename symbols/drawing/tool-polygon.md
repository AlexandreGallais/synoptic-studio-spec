# Polygon tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing](../02-drawing.md) › Polygon

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

The polygon is drawn by dragging a box, like the rectangle and the ellipse. It becomes a path. A polygon does not always touch all the sides of its box, so the tool has options, set in the right-hand panel.

## Rules

- **Number of sides**: chosen by the user, from 3 to 20.
- **How the polygon fills its box**: the Product Owner wants one of two behaviours, never a blend of both.

| Mode | The polygon... |
| --- | --- |
| Filled | fills the box as much as possible. It is not forced to be equilateral. |
| Equilateral | keeps all its sides equal. It is not forced to fill the box. |

- **Anchors**: the user says where the polygon is placed in its box, with anchors on the box (its sides and its corners). Two ways to use an anchor:
  - a **corner** of the polygon touches the anchor;
  - a **side** of the polygon touches the anchor.
- Example: "a side always touches the left anchor, whatever the number of sides".

## Open questions

- Figma draws its polygon in a way the Product Owner does not understand: a triangle does not fill the box, and it is not clear why. Whether a third mode "like Figma" is kept depends on a documentary research on how Figma, and drawing software in general, place a polygon in its box. It will be done at the end, like the one done for Metadata. See [Open questions](../07-open-questions.md).
