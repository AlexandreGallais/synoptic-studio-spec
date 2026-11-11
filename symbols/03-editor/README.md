# The symbol editor

> [Home](../../README.md) › [Symbols](../README.md) › Editor · Previous: [Type, preset and faceplate](../02-type-and-faceplate.md) · Next: [Drawing mode](../04-drawing-mode/README.md)

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

The symbol editor is a vector drawing editor, close to Figma and Inkscape for what it needs. It works with **modes** and **tools**. This page holds what is common to every mode; each mode has its own folder, with its tools inside.

## Rules

- A **tool** is what the mouse does in the drawing: select, draw a rectangle, write a text.
- A **mode** changes what the editor is for. Switching mode changes the tools of the tool bar and what the right-hand panel shows.
- Nothing is hidden behind a double click: to edit points, the user switches to the point editing mode.
- **Same keys on every platform** (Product Owner, 2026-11-11). Windows, macOS and Linux behave the same. Only keys that exist on all three are used: Shift, Ctrl and Alt (the Option key on a Mac), with letters, digits, arrows and function keys. No Command, Option or Windows key in the specs. Whenever a page asks which key to use, this rule applies first.
- Key shortcuts and modifier keys are allowed, as in every drawing software, but never alone: each one has a visible equivalent (an option in the panel or the tool bar). The software is used by everyone, including an expert of 80 who makes synoptics.
- Everything drawn stays a path, in the layers of an SVG, so the symbol stays a real SVG. A text stays a text, because it can show a value or a unit (see [Animation mode](../08-animation-mode/README.md)).
- The name "layer" is provisional. A layer can be the target of an animation or of an interaction.
- Colours (fill, border) and the options of a shape (corner radius, for example) are neither tools nor modes. They are in the right-hand panel, which shows the options that fit the selected shape.

## Modes

| Mode | What it is for | Tools in the tool bar | Right-hand panel |
| --- | --- | --- | --- |
| [Drawing](../04-drawing-mode/README.md) | The default mode: draw and arrange shapes. | Select, Hand, Group, Rectangle, Ellipse, Polygon, Pen, Text | Options of the selected shape (colours, corner radius...) |
| [Point editing](../05-point-editing-mode/README.md) | Edit the points of a path. | Select, Hand, Pen | Options of the selected point |
| [Alignment](../06-alignment-mode/README.md) | Place shapes in relation to each other. | Select, Hand | Alignment of the selected shapes |
| [Interaction](../07-interaction-mode/README.md) | Draw the zones that react to a gesture, and link them to commands. | Select, Hand, Interaction zone | The interactions of the selected place |
| [Animation](../08-animation-mode/README.md) | Link the signals to the parts of the drawing. | Select, Hand | The animations of the selected part |
| [Run](../09-run-mode/README.md) | Try the symbol with test values and see it at the size of another screen. | Hand | The test values, and the simulated screen |
| [Connection](../pipes/connection-points.md) (provisional) | Place the connection points where pipes attach. | Select, Hand, Connection point | The options of the selected point |

- The Connection mode is an assumption of the assistant: the Product Owner did not say which mode places the connection points (see [Connection points](../pipes/connection-points.md)).
- The Interaction, Animation and Run modes are only for a dynamic symbol: a static symbol has no interaction, no animation and nothing to test with signals.
- The [Expert menu](expert-menu/README.md) can add a second tool bar on top of the current mode.
- Other modes may be added later.

## Moving around the drawing

- Mouse: the scroll wheel, and the middle button held down, which shows the hand while it is held.
- Trackpad: the usual gestures, to scroll and to zoom.
- The [Hand tool](hand.md) does the same from the tool bar.
- The zoom is shown as a percentage, in one place of the editor, and the user can type a value in it. At 100%, the symbol is shown at its real size.
- Simulating the size of the symbol on another screen is done in the [Run mode](../09-run-mode/README.md), not here.

## What is common to the modes

| Page | What it holds |
| --- | --- |
| [Select](select.md) | The Select tool, in every mode except Run. |
| [Hand](hand.md) | The Hand tool, in every mode. |
| [Anchors](anchors.md) | The nine named points of a box, used by groups, polygons, alignment and pipe ends. |
| [Expert menu](expert-menu/README.md) | The menu of the tools that are not for everyday drawing. |

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Paths, text, groups, layers | Symbol editor | Symbol drawing, animation and interaction targets | Draw, edit | No |

## Open questions

The open questions are on the pages they concern, and listed in [Open questions](../10-open-questions.md).
