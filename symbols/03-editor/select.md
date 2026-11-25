# Select tool

> [Home](../../README.md) › [Symbols](../README.md) › [Editor](README.md) › Select

Status: draft. Not validated.

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

- A click on a shape selects it. What is clickable is the **real shape** (a circle is clickable as a circle, not as the square around it), including its inside when the fill is transparent: a shape with a transparent fill stays clickable.
- Several shapes can be selected, with the usual meaning of the keys, "un vrai Shift et un vrai Contrôle" (Product Owner, 2026-11-26): Ctrl and a click adds a shape to the selection or removes it; Shift and a click in the [layers](layers.md) adds every layer between the last one clicked and this one; on the drawing, Shift and a click adds the shape like Ctrl (assistant's reading). A plain click resets the selection. In the point editing mode, several points are selected the same way. In the [alignment mode](../06-alignment-mode/README.md#the-reference-and-the-shapes-to-place-a-normal-selection), the first shape selected is the reference and the next ones are the shapes to place (Product Owner, 2026-11-26).
- A press in the empty space, held while dragging, draws a selection rectangle.
- By default, every shape the rectangle touches is selected. A modifier key makes the rectangle select only the shapes it contains entirely. Like every modifier, it has a visible option too.

## Moving and resizing

- The selected shapes can be moved with the mouse.
- A selection has a box with small squares on its sides and corners, to resize it.
- Resizing never applies a scale or a transform. A rectangle that grows gets a bigger width and a bigger height. Its border does not grow: the border has the fixed value the user gave it.
- A text is resized the same way, with one rule more: its box is shown when it is selected, and dragging the box enlarges the text zone only. The size of the text does not change (see [Text](../04-drawing-mode/text.md)).

## What the research found

Source: the research report (`research/t1-…/rapport.md`).

- In every software read, Shift adds to the selection or removes from it. Shift is therefore taken: the key for "entirely enclosed" must be another one.
- Selection rectangle, "entirely enclosed": Option (Alt) while dragging in Sketch; the direction of the drag in AutoCAD (left to right: enclosed entirely; right to left: everything crossed); no way in Figma (asked by its users since 2021). In Inkscape the same Alt key does the opposite (takes what the stroke touches).
- Figma: Ctrl or Command while dragging takes nested layers. Sketch: Command ignores groups.

Second research report (`research/t4-…/rapport.md`, section 3.15):

- The clickable real shape, transparent fill included, is native: `pointer-events` has values that make the inside clickable whatever the fill. Opinion of the report: let the browser do the hit test, with no computation in JavaScript. (The definitions of the values were not on the page opened.)

## Decided

- **Keys must exist on every platform** (Windows, macOS, Linux), the same everywhere: see the rule in the [editor](README.md). "Option" does not exist on Windows, so the specs name the key **Alt** (it is the Option key on a Mac).
- A selection rectangle selects only the shapes it contains entirely while **Alt** is held. The option in the panel stays as the visible equivalent.

## Open questions

- None.
