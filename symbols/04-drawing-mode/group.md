# Group tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Group

Status: draft. Not validated.

Group is a tool of the tool bar, like Select or Rectangle: the user picks it to create a group. A group is also the object it creates.

A group is an SVG `g` element. Its first use is to give a structure to several shapes: for example, the [animation](../08-animation-mode/README.md) can then make the whole group turn.

## Rules

### Creating a group

- With the Group tool, from the tool bar.
- With Ctrl+G on a selection, or with right click and "Group". The tool is the visible equivalent of both.

### Two sizes: hug or fixed

- In SVG, a group has no size of its own: it takes the size of what is inside. The editor overrides this, so that a group can be given a size and a position.
- The size is set like in Figma: a **width** and a **height**, each one either **Hug** or **Fixed**, with the [size fields](../../controls/size-fields.md): W and H on one line, the mode in each field with a small arrow that opens a menu Fixed, Hug (Product Owner, 2026-11-24; "Hug" was called "fit" before).
  - Hug, on both: the group is a plain SVG group. It wraps its children and nothing more. This is the default.
  - Fixed: the group has the size the user gave it, and it no longer wraps its content.
  - The width and the height are **always shown**, in Hug too: the user sees the size of the group, and changes it in the same field (Product Owner, 2026-11-24).
- Under the size, its X and Y. **No rotation**: a group is always a rectangle upright, its sides horizontal and vertical (Product Owner, 2026-11-26: "il n'y a pas de rotation possible pour les groupes et point barre"). **No corner radius**, not even greyed (Product Owner, 2026-11-26: "me fais pas ça dans les groupes").
- A group has no fill and no border (see [Fill and border](fill-and-border.md)).
- A group with its own size can be empty. The size and the position are only simulated by the editor: no rectangle is added inside the group, and the SVG bounding box is not relied on.

### Layout of the children

**Only the children** say how they are placed: the group itself has no setting for it (Product Owner, 2026-11-26: "on peut dégager ça du groupe et laisser ça qu'aux enfants [...] sur le parent, ça, rien"). It replaces the placement of the children on the group, set earlier the same day.

- **Each child** has its section "In the group": Free or Anchored, in one click, always with an anchor in a 9-point grid (see [Geometry](geometry.md#in-the-group)).
- **The first child gives the default**: an element that enters the group takes the placement and the anchor of the first child of the group, then keeps its own; changing it later does not move the others (Product Owner, 2026-11-26: "le premier enfant [...] ça définit le défaut du groupe"; the assistant's reading of the sentence). The very first child starts Free, at the top left anchor (assistant's proposal).
- The placement works whether the width and the height of the group are Hug or Fixed: its free children follow their own anchor when a Fixed group is resized (Product Owner, 2026-11-26: "peu importe si le width et le height sont en hug ou en fixed").
- No flex display (rows, columns, gaps): no case where it would be useful.

### Absolute children

- A child can be set **absolute**: it leaves the layout. It is the "Anchored" placement with two different anchors (see [Geometry](geometry.md#in-the-group)).
- Its position is given by two [anchors](../03-editor/anchors.md): an anchor of the group and an anchor of the child. Example: the child's bottom left corner on the group's top right corner.
- This puts the child outside the shape of the group while it stays in the group.
- An absolute child does not change the size of the group.

### The runtime

- The runtime may do more than an SVG can. It places the children again when something changes: a text that grows, for example.

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, section 3.15). Figma gives a child constraints (left, right, centre, both, scale) to its parent frame; a Figma group has none. Opinion of the report: the layout without flex is enough for symbols; the anchors play the role of constraints.

## Open questions

- The list of anchors and the exact options of the panel. See [Open questions](../10-open-questions.md).
- How the Group tool is used with the mouse: click the shapes one by one, or draw a frame.
