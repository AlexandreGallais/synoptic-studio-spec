# Polygon tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Polygon

Status: draft and the research report of 2026-11-11. Not validated.

The polygon is drawn by dragging a box, like the rectangle and the ellipse. It becomes a path, with one point per side. A polygon does not always touch all the sides of its box, so the tool has options, set in the right-hand panel.

## Rules

- **Number of sides**: chosen by the user, from 3 to 20.
- **How the polygon fills its box**: two modes, never a blend of both.

| Mode | The polygon... |
| --- | --- |
| Filled | fills the box as much as possible. It is not forced to be equilateral. |
| Equilateral | keeps all its sides equal. It is not forced to fill the box. |

- **Anchors**: the user says where the polygon is placed in its box, with the [anchors](../03-editor/anchors.md) of the box (its sides and its corners). Two ways to use an anchor:
  - a **corner** of the polygon touches the anchor;
  - a **side** of the polygon touches the anchor.
- Example: "a side always touches the left anchor, whatever the number of sides".
- **In the panel**: the options of the polygon (sides, how it fills its box, anchor, what touches it) come **first**, before the size and the position, since they make its shape (Product Owner, 2026-11-25); then the [geometry](geometry.md), the fill, the border and the opacity.
- **Points**: like the rectangle and the ellipse, its points can be edited in the [point editing mode](../05-point-editing-mode/README.md). Each point can have its own corner radius, or its handles (see [Points and handles](../05-point-editing-mode/points-and-handles.md)).
- **Fill and border**: the ones every shape has (see [Fill and border](fill-and-border.md)).
- **Opacity and clip**: the ones every shape has (see [Effects](effects-and-masks.md#where-each-kept-entry-is-set)).

## What the research found

Source: the research report (`research/t1-…/rapport.md`).

### Why Figma's triangle does not fill its box

- Figma says its polygon box keeps the same shape and size when sides are added, so the box does not change when the number of sides changes. To fit the box to the shape, the user flattens it.
- The report deduces (not written by Figma, to check in two minutes in Figma) that the vertices are on the ellipse inscribed in the box, one vertex at the top middle. In a square box the polygon is regular; in another box it is stretched like the ellipse. A triangle in a 100 × 100 box: vertices (50; 0), (93.30; 75), (6.70; 75).
- Consequence: the top always touches, the bottom touches for an even number of sides, the left and right touch for a multiple of 4.
- Figma users complain about the empty space at the bottom and about alignment. Figma gives a perfect polygon with Shift.

### The four variants

| Variant | Construction | Touches the box | Equal sides | Where |
| --- | --- | --- | --- | --- |
| A · Filled | The regular polygon is stretched, in width and in height, to the box. | The four sides, for any number of sides. | Only if the box has the polygon's natural ratio. | Illustrator (stretched), CorelDRAW without Ctrl. |
| B · Equal sides | The regular polygon grows, without distortion, until it touches two opposite sides. | Two opposite sides; empty space in the other direction. | Always. | CorelDRAW with Ctrl, Illustrator ("equal sides" button). |
| C · Inscribed ellipse | Vertices on the ellipse inscribed in the box. | Top always; bottom if even; sides if multiple of 4. | Only if the box is square. | Figma. |
| D · Centre and radius | A centre, a radius, an angle. | No dragged box. | Always. | Inkscape. |

- Filled is A, Equilateral is B: the two modes are exactly the two states Illustrator and CorelDRAW offer.
- Opinion of the report: **do not keep a third mode "like Figma" (C)**. It blends the two others (regular in a square box, stretched elsewhere, never filled), which is not wanted. Its only own advantage, a centre and radius that do not move when the number of sides changes, matters little in a tool that draws by dragging a box. D is not kept either: it does not start from a box. Confidence: medium. The Product Owner decides.

### Geometry by number of sides

Values from a computation made for the report, one vertex at the top. "Natural ratio" is width / height of the regular polygon.

| Sides | Natural ratio | B, square box: width × height | B: touches at the bottom | B: touches on the sides |
| --- | --- | --- | --- | --- |
| 3 | 1.1547 | 100 % × 86.6 % | a side | a corner |
| 4 | 1.0000 | 100 % × 100 % | a corner | a corner |
| 5 | 1.0515 | 100 % × 95.1 % | a side | a corner |
| 6 | 0.8660 | 86.6 % × 100 % | a corner | a side |
| 7 | 1.0257 | 100 % × 97.5 % | a side | a corner |
| 8 | 1.0000 | 100 % × 100 % | a corner | a corner |
| 9 | 1.0154 | 100 % × 98.5 % | a side | a corner |
| 10 | 0.9511 | 95.1 % × 100 % | a corner | a side |
| 12 | 1.0000 | 100 % × 100 % | a corner | a corner |
| 16 | 1.0000 | 100 % × 100 % | a corner | a corner |
| 20 | 1.0000 | 100 % × 100 % | a corner | a corner |

Odd numbers of sides (11 to 19) follow the pattern of 3, 5, 7, 9: a ratio slightly above 1 (11: 1.0103, 13: 1.0073, 15: 1.0055, 17: 1.0043, 19: 1.0034); even numbers not multiple of 4 (14: 0.9749, 18: 0.9848) follow 6 and 10.

Examples (computed): a triangle in a 100 × 100 box. Filled: vertices (50; 0), (100; 100), (0; 100), sides 111.80, 100 and 111.80, fills the box and is not equilateral. Equilateral: base 100, height 86.60, 13.40 of empty space, placed by the anchor.

### Anchors seen by the geometry

- In Equilateral, the polygon leaves empty space in one direction. The anchor says where that space goes, and which part of the polygon, a corner or a side, points to the anchor.
- In Filled, the polygon touches all four sides already. The anchor can only choose the starting orientation: a corner towards the anchor, or a side towards the anchor.
- A corner of the polygon can touch a corner of the box only for 3 or 4 sides. From 5 sides the polygon angle exceeds 90° (108° for 5 sides) and would leave the box.

## To decide by the Product Owner

1. Keep or drop a third mode "like Figma"? The report advises dropping it. Check beforehand the vertices of Figma's triangle (above), if wanted.
2. Anchors on corners: reserve them to 3 and 4 sides, or give them another meaning (place the empty space)?
