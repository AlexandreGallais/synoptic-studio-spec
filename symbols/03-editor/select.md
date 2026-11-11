# Select tool

> [Home](../../README.md) › [Symbols](../README.md) › [Editor](README.md) › Select

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

Select is in the tool bar of every mode except the Run mode. What it does depends on the mode.

| Mode | What Select picks |
| --- | --- |
| [Drawing](../04-drawing-mode/README.md) | Shapes: to select them, move them and resize them. |
| [Point editing](../05-point-editing-mode/README.md) | Points and handles of a path. |
| [Alignment](../06-alignment-mode/README.md) | The shapes to place in relation to each other. |
| [Interaction](../07-interaction-mode/README.md) | The shapes, or the places, on which an interaction is set. |
| [Animation](../08-animation-mode/README.md) | The parts of the drawing that a signal animates. |
| [Run](../09-run-mode/README.md) | Nothing: Select is not offered. |

## Selecting

- A click on a shape selects it.
- Several shapes can be selected: with Shift or Ctrl held, a click adds a shape to the selection (or removes it). In the point editing mode, several points can be selected the same way.
- A press in the empty space, held while dragging, draws a selection rectangle.
- By default, every shape the rectangle touches is selected. A modifier key makes the rectangle select only the shapes it contains entirely. Like every modifier, it has a visible option too.

## Moving and resizing

- The selected shapes can be moved with the mouse.
- A selection has a box with small squares on its sides and corners, to resize it.
- Resizing never applies a scale or a transform. A rectangle that grows gets a bigger width and a bigger height. Its border does not grow: the border has the fixed value the user gave it.
- A text is resized the same way, with one rule more: its box is shown when it is selected, and dragging the box enlarges the text zone only. The size of the text does not change (see [Text](../04-drawing-mode/text.md)).

## Open questions

- None kept here. Which modifier key selects only the shapes entirely inside the rectangle is in the [research brief](../research-brief.md).
