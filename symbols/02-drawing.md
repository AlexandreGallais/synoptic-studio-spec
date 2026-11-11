# Drawing

> [Home](../README.md) › [Symbols](README.md) › Drawing · Previous: [Libraries and symbols](01-libraries-and-symbols.md) · Next: [Type, preset and faceplate](03-type-and-faceplate.md)

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

The symbol editor is a vector drawing editor, close to Figma and Inkscape for what it needs.

## Rules

- Every drawing mode is a tool of the tool bar. Nothing is hidden behind a double click.
- Everything drawn is a path. A rectangle, an ellipse and a polygon are paths once drawn.
- The drawing is made of layers, which are the layers of an SVG. The name "layer" is provisional. A layer can be the target of an animation or of an interaction (see [Animation](04-animation.md) and [Interactions](05-interactions.md)).
- Colours (fill, stroke) and the options of a shape (corner radius, for example) are not tools. They are in the right-hand panel, which shows the options that fit the selected shape.

## Moving around the drawing

- With the mouse: the scroll wheel, and the middle button, held down, which shows the hand while it is held.
- With the trackpad: the usual gestures to scroll and to zoom.
- The Hand tool does the same, from the tool bar.

## Tools of the tool bar

| Tool | What it does |
| --- | --- |
| Select | Select shapes, move them and resize them. |
| Hand | Move the view (not a shape). |
| Rectangle | Draw a rectangle. |
| Ellipse | Draw a circle or an ellipse. |
| Polygon | Draw a polygon. |
| Text | Write a text. A text can show a signal's value or unit (see [Animation](04-animation.md)). |
| Pen | Draw a path point by point, with straight lines and curves. It is also the tool for lines: there is no line tool. |
| Point editing | A mode to edit the points of a path: select, move, add and remove points and handles. |

## Other modes and tools

| What | Where | What it does |
| --- | --- | --- |
| Interaction zone | Only in the interaction mode, not in the tool bar | Draw a zone that reacts to a gesture (see [Interactions](05-interactions.md)). |
| Alignment | The right-hand panel, like point editing: selecting shapes switches it to alignment | Align the selected shapes. |
| Group | Not in the tool bar. Select several shapes, then right click and "Group", or Ctrl+G | Gather shapes in a group above the paths. |
| Boolean operations | Expert menu | Select two shapes, then make a new shape from them (intersection and the like). |
| Placement and duplication | Expert menu | Duplicate a shape along a rule. Examples: pick a point and a radius, then 30 copies of a shape equally spaced on the circle; or copies equally spaced along the edge of an existing shape or line. |

The expert menu holds the tools that are not for everyday drawing.

## The pen

| Action | Result |
| --- | --- |
| Click a point, then click another | A straight line between them. |
| Press on the second point and drag before releasing | The segment becomes a curve, shaped by the drag. |
| Click again, with no modifier | As in Figma, the next segment is a curve again. |
| Click again, holding a modifier key | The next segment is a straight line straight away. |

The modifier is an option wanted by the Product Owner, because a curve again after a curve is often a nuisance. The key is not chosen (Shift and Alt were mentioned), nor whether it only applies to the next segment or stays on.

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Paths, text, groups, layers | Symbol editor | Symbol drawing, animation and interaction targets | Draw, edit | No |

## Open questions

- Do groups get a size or a layout (vertical, horizontal, grid), like Figma frames? Kept in mind, not decided.
- The exact options of the expert tools (boolean operations, duplication) and of alignment.
- The pen modifier key and how it works.

All three are in [Open questions](07-open-questions.md).
