# Groups

> [Home](../../README.md) › [Symbols](../README.md) › [Editor](README.md) › Groups

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

A group is neither a tool nor a mode. It is used in the drawing, but it is not tied to one mode.

## Rules

- To make one, the user selects several shapes, then right click and "Group", or Ctrl+G. A group gathers shapes: an empty group does not exist.
- By default, the children of a group are placed freely (absolute), and the group has the size of what is inside it.
- A group can be given a **layout**, set in the right-hand panel, like the auto layout of Figma or a flex display in CSS: everything inside is laid out horizontally or vertically, and starts from a corner, for example the bottom left. Grids are not decided.
- A child can leave the layout and stay placed freely, fixed or tied to a corner of the group: "this one goes to the bottom right of the group, that one to the top right".
- The runtime may do more than an SVG can. A group with a layout can have its own size, and the runtime recalculates the layout when something changes: a text that grows, for example, pushes or follows the others as the layout says.
- The Product Owner finds this complicated but wants it to be possible.

## Open questions

- The exact options of the group layout. See [Open questions](../10-open-questions.md).
- Is "Group" also an entry of the tool bar, besides Ctrl+G and the right click? The Product Owner said "the groups to add to the tools" after saying a group is neither a tool nor a mode.
