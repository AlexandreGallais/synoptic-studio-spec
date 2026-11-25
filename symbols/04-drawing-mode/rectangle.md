# Rectangle tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Rectangle

Status: draft. Not validated.

## Rules

- Draws a rectangle by dragging. It becomes a path with 4 points.
- While drawing, a modifier key forces the width and the height to be equal: a square. The key is not chosen yet (Shift or Ctrl, see below).
- The panel has a visible option that links the width and the height, for the same result.
- Keys must be the same on every platform (Shift, Ctrl, Alt only: see the rule in the [editor](../03-editor/README.md)). Keys in other software (research report): square with Shift in Figma, Sketch and Illustrator, with Ctrl in Inkscape and CorelDRAW; from the centre with Alt (Option) in Figma and Sketch, with Shift in Inkscape and CorelDRAW. The same applies to the ellipse (circle) and the polygon.
- **Geometry**: size, position and rotation, first in the panel (see [Geometry](geometry.md)).
- **Corner radius**: set in the right-hand panel, for the whole rectangle, **under the height**, in the section of the geometry (Product Owner, 2026-11-25: under Effects, it was out of place).
- **Points**: in the [point editing mode](../05-point-editing-mode/README.md), the 4 points can be edited, each with its corner radius or its handles (see [Points and handles](../05-point-editing-mode/points-and-handles.md)). When a point is added, removed or moved, the rectangle becomes a free form that loses nothing of its fill, border and effects (see [Point editing mode](../05-point-editing-mode/README.md)).
- **Fill and border**: the ones every shape has (see [Fill and border](fill-and-border.md)).
- **Opacity and clip**: the ones every shape has (see [Effects](effects-and-masks.md#where-each-kept-entry-is-set)).
