# Group tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Group

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

Group is a tool of the tool bar, like Select or Rectangle: the user picks it to create a group. A group is also the object it creates.

A group is an SVG `g` element. Its first use is to give a structure to several shapes: for example, the [animation](../08-animation-mode/README.md) can then make the whole group turn.

## Rules

### Creating a group

- With the Group tool, from the tool bar.
- With Ctrl+G on a selection, or with right click and "Group". The tool is the visible equivalent of both.

### Two sizes: fit or own size

- In SVG, a group has no size of its own: it takes the size of what is inside. The editor overrides this, so that a group can be given a size and a position.
- The size is set like in Figma: a **width** and a **height**, each one either **fit** or **fixed**.
  - Fit, on both: the group is a plain SVG group. It wraps its children and nothing more. This is the default.
  - Fixed: the group has the size the user gave it, and it no longer fits its content.
- A group has no fill and no border (see [Fill and border](fill-and-border.md)).
- A group with its own size can be empty. The size and the position are only simulated by the editor: no rectangle is added inside the group, and the SVG bounding box is not relied on.

### Layout of the children

- It is available when the group has its own size. The panel offers the placement of the children in the group: centred, or aligned left, right, top or bottom, with anchors.
- All the children centred is the simple case. When the group fits its content, the biggest child gives the size, and the others are centred on it.
- The Product Owner does not want a flex display (rows, columns, gaps): he sees no case where it would be useful.

### Absolute children

- A child can be set **absolute**: it leaves the layout.
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
