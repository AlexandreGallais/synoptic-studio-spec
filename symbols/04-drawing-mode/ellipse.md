# Ellipse tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Ellipse

Status: draft. Not validated.

## Rules

- Draws an ellipse by dragging: an oval or a circle. It becomes a path with 4 points, as in Figma.
- The same modifier key and the same visible option as for the [Rectangle](rectangle.md) force the width and the height to be equal: a circle.
- **Geometry**: size, position and rotation, first in the panel (see [Geometry](geometry.md)).
- **No corner radius**: it makes no sense for an ellipse. The right-hand panel shows it **greyed**, on the line of the rotation, so that every shape has the same lines (Product Owner, 2026-11-26: "je veux bien que tu mettes quand même le corner radius, et puis venir le griser"). Once turned into a free form in the point editing mode, its points take a corner radius (see below).
- **Points**: in the [point editing mode](../05-point-editing-mode/README.md), the 4 points can be edited with their handles (see [Points and handles](../05-point-editing-mode/points-and-handles.md)). When a point is added or removed, the ellipse becomes a free form, and its points gain the corner radius mode (see [Point editing mode](../05-point-editing-mode/README.md)).
- **Fill and border**: the ones every shape has (see [Fill and border](fill-and-border.md)).
- **Opacity and clip**: the ones every shape has (see [Effects](effects-and-masks.md#where-each-kept-entry-is-set)).
