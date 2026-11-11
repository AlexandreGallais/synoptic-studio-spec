# Points and handles

> [Home](../../README.md) › [Symbols](../README.md) › [Point editing mode](README.md) › Points and handles

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

What the right-hand panel offers when a point or a handle is selected in the [point editing mode](README.md).

## Rules

### Two modes for a point

A selected point is in one of two modes, and the user switches between them freely:

| Mode | What it is |
| --- | --- |
| Corner radius | The point is rounded with a corner radius. |
| Handles | The point has handles that shape the curve. |

- Each mode keeps its own settings. Switching to the corner radius mode and back to the handles mode gives the handles as they were, and the other way round. Nothing is forgotten.
- The points of a [rectangle](../04-drawing-mode/rectangle.md), of a [polygon](../04-drawing-mode/polygon.md) and of a path can each have their own corner radius or their handles.
- A point of an [ellipse](../04-drawing-mode/ellipse.md) has no corner radius mode: it has handles only.

### Mirroring of the handles

When a point is selected, the user chooses how its two handles follow each other:

| Mirroring | Meaning |
| --- | --- |
| None | The two handles are independent. |
| Mirror angle | The two handles keep opposite angles. Their lengths are free. |
| Mirror angle and length | The two handles keep opposite angles and the same length. |

### Editing a handle

When a handle is selected, it can be edited in two ways, which stay linked:

- by its position: **X** and **Y**;
- by its **angle** and its **length** (its radius).

Changing X and Y changes the angle and the length, and the other way round. The angle and length way is for a handle that must go at a precise angle, which X and Y alone do not give easily.

## Open questions

- None kept here. The names and the list of mirroring modes are in the [research brief](../research-brief.md).
