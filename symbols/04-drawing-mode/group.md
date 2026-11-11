# Group tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Group

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

Group is a tool of the tool bar, like Select or Rectangle: the user can pick it to create a group. A group is also the object it creates, which gathers shapes.

## Rules

- The tool is in the tool bar of the [drawing mode](README.md).
- Besides the tool, a group can be created from a selection with Ctrl+G, or with right click and "Group". Both have the tool as their visible equivalent.
- A group gathers shapes: an empty group does not exist.
- By default, the children of a group are placed freely (absolute), and the group has the size of what is inside it.
- A group can be given a **layout**, set in the right-hand panel, like the auto layout of Figma or a flex display in CSS: everything inside is laid out horizontally or vertically, and starts from a corner, for example the bottom left. Grids are not decided.
- A child can leave the layout and stay placed freely, fixed or tied to a corner of the group: "this one goes to the bottom right of the group, that one to the top right".
- The runtime may do more than an SVG can. A group with a layout can have its own size, and the runtime recalculates the layout when something changes: a text that grows, for example, pushes or follows the others as the layout says.
- The Product Owner finds the layout complicated but wants it to be possible.

## Open questions

- The exact options of the group layout, and how the tool is used with the mouse. See [Open questions](../10-open-questions.md).
