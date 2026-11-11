# Polygon tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Polygon

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

The polygon is drawn by dragging a box, like the rectangle and the ellipse. It becomes a path, with one point per side. A polygon does not always touch all the sides of its box, so the tool has options, set in the right-hand panel.

## Rules

- **Number of sides**: chosen by the user, from 3 to 20.
- **How the polygon fills its box**: two modes wanted by the Product Owner, never a blend of both.

| Mode | The polygon... |
| --- | --- |
| Filled | fills the box as much as possible. It is not forced to be equilateral. |
| Equilateral | keeps all its sides equal. It is not forced to fill the box. |

- A third mode, "like Figma", may be added. Figma is not equilateral and does not fill the box either: it depends on the [research brief](../research-brief.md).
- **Anchors**: the user says where the polygon is placed in its box, with anchors on the box (its sides and its corners). Two ways to use an anchor:
  - a **corner** of the polygon touches the anchor;
  - a **side** of the polygon touches the anchor.
- Example: "a side always touches the left anchor, whatever the number of sides".
- **Points**: like the rectangle and the ellipse, its points can be edited in the [point editing mode](../05-point-editing-mode/README.md). Each point can have its own corner radius, or its handles (see [Points and handles](../05-point-editing-mode/points-and-handles.md)).
- **Fill and border**: the ones every shape has (see [Fill and border](fill-and-border.md)).
- **Effects and mask**: the ones every shape has (see [Effects and masks](effects-and-masks.md)).

## Open questions

- None kept here. Why Figma places its polygon the way it does, and whether a "like Figma" mode is kept, are in the [research brief](../research-brief.md).
