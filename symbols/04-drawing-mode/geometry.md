# Geometry of a shape: size, position, rotation

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Geometry

Status: draft. Asked by the Product Owner on 2026-11-25; the form is the assistant's, which the Product Owner left to it ("je te laisse le contrôle"), reviewed on the test screens on 2026-11-26 (decision 0109). Not validated.

What every element of the drawing has in common: a [group](group.md), a [rectangle](rectangle.md), an [ellipse](ellipse.md), a [polygon](polygon.md), a path drawn with the [pen](pen.md) and a [text](text.md). It is the first section of the right-hand panel.

## Rules

- **Size**: W and H, the [size fields](../../controls/size-fields.md), with the link icon. Fixed or Hug only for what can wrap a content (a group, a text).
- **Position**: X and Y, two number fields on one line, in pixels, without unit, under the size.
- **Rotation**: a number field in degrees, on the line under X and Y; the box and its anchors turn with the element. It is the only transform of an element (opinion of the research, see [Editor](../03-editor/README.md#geometry-of-a-symbol)). **Never for a group**, always upright (Product Owner, 2026-11-26).
- **Corner radius**: on the line of the rotation, a number field with an icon inside and no label (Product Owner, 2026-11-26: "Corner radius, tu l'écris pas"). For a rectangle, a polygon and a path; **shown greyed for an ellipse**, so that every shape has the same lines (Product Owner, 2026-11-26); never shown for a group.
- **Aligned**: W and H have the width of X and Y; every line keeps the room of one icon on its right, used or not (the link of W and H), so that every field lines up ([layout rule](../../screens/README.md#fields-on-two-columns-and-an-icon-slot), Product Owner, 2026-11-26).
- **Everywhere the same**: these fields are in the panel of every kind of element, in the same order (Product Owner, 2026-11-25: "il faut que tu appliques ça partout").

### In the group

Every element inside a group (a rectangle, an ellipse, a polygon, a path, a text, a group) has a **section of its own, "In the group"**, **first in its panel**, above its geometry (Product Owner, 2026-11-26: "que ce soit un carré, un rond, un polygone, peu importe. Mais il faut que ce soit une section à part"; first: "il y a in the group en premier"). Only the children have it: the group itself has no placement (see [Group](group.md#layout-of-the-children)). It says how the element is placed in its group:

- **Two placements, Free or Anchored**, chosen in one click with a [segmented control](../../screens/README.md#a-segmented-control-for-two-to-four-short-options) (Product Owner, 2026-11-26: "soit libre, soit avec ancre. Il n'y en a que deux"). "As the group" is no longer offered.
- **Always an anchor**, in a 9-point grid, in both placements: every placement is computed from an anchor, so that a resized group never leaves a position to guess (Product Owner, 2026-11-26: "ce sera toujours un calcul par rapport à une ancre").
- **The grid is large**: nine rectangles, thicker than before, as wide as the segmented control Free │ Anchored above it, easy to click rather than small squares (Product Owner, 2026-11-26: "je préfère qu'il y ait des rectangles, mais que ce soit plus facile à cliquer"). The same grid wherever the panel has one (the anchor of a child, the placement of a polygon in its box, the alignment of a text).

| Placement | Anchor | X and Y | What it does |
| --- | --- | --- | --- |
| Free | A 9-point grid | Typed | The element does not touch the anchor: the user puts it where they want, its X and Y measured from the anchor. When the group is resized, it **follows the anchor**, at the same distance: anchored at the top right, it keeps its distance to the top right corner (Product Owner, 2026-11-26: "elle va suivre ce redimensionnement par rapport au coin en haut à droite"). |
| Anchored | A 9-point grid | Shown, read only | The element **touches** the anchor: its matching anchor on the anchor of the group, its top right corner on the top right corner. When the group is resized, it stays stuck there ("ça colle le coin, tout bêtement"). |

- Free with the top left anchor is the X and Y of an element at the root (assistant's proposal: the anchor of a free element starts at the top left).
- An element put in a group takes the placement and the anchor of the first child of the group, then keeps its own (Product Owner, 2026-11-26: "le premier enfant [...] ça définit le défaut du groupe"; see [Group](group.md#layout-of-the-children)).
- An element at the root of the symbol has no section "In the group": its X and Y are typed.
- The anchors of the element and of the group can differ, to put the element outside the group: it is the absolute child of [Group](group.md#absolute-children), reached by a second 9-point grid "Anchor of the element", shown under the first once the user asks for it (assistant's proposal).

```mermaid
block-beta
    columns 3
    t["Section In the group, first"]:3
    p["Placement: Free │ Anchored, one click, the whole width"]:3
    g["Anchor: 9-point grid of rectangles, the whole width"]:3
    w["W 72"] h["H 34"] link["Link"]
    x["X 64"] y["Y 0"] e1[" "]
    r["Rotation 0°"] c["Corner radius 4"] e2[" "]
```

## Order of the right-hand panel

The panel reads from where the element is to how it looks (Product Owner, 2026-11-26, replacing the order of 2026-11-25 where the options of the polygon came first):

1. **The element**: its title (kind and name).
2. **In the group**, for an element inside a group: its placement and its anchor (see [above](#in-the-group)). A group has no placement of its own.
3. **Geometry**: W and H; X and Y; the rotation and the corner radius (see [Rules](#rules)).
4. **The options that make its shape**, when it has some: sides and box of a [polygon](polygon.md#rules).
5. **Opacity**: one line, the opacity of the whole element (Product Owner, 2026-11-25; see [Opacity](effects-opacity-and-blend.md#opacity)). No section "Effects" in this version.
6. **Fill**, then **border**: see [Fill and border](fill-and-border.md).

A text keeps its own sections after the opacity (see [Text](text.md)).

## Where it is used

| Screen | Control |
| --- | --- |
| [SY-04](../../screens/symbols.md#sy-04--drawing-mode) · every element | Size, position, rotation (SY-04.36, SY-04.37, SY-04.38) |
| [SY-04](../../screens/symbols.md#sy-04--drawing-mode) · a child of a group | Placement in the group (SY-04.21) |

## Open questions

- Mirror (horizontal, vertical): recomputed in the points, as the research proposes, or not offered?
- The anchor a free element starts with: the top left (proposal)?

Skew and tilt in 3D are not offered: set aside with the [catalogue of the effects](effects-and-masks.md#catalogue-of-the-effects) (Product Owner, 2026-11-25).
