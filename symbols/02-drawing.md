# Drawing

> [Home](../README.md) › [Symbols](README.md) › Drawing · Previous: [Libraries and symbols](01-libraries-and-symbols.md) · Next: [Type, preset and faceplate](03-type-and-faceplate.md)

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

The symbol editor is a vector drawing editor, close to Figma and Inkscape for what it needs. It works with **modes** and **tools**. This page holds the general rules and the map of the pages of this part; each mode, each tool and each expert entry has its own page.

## Rules

- A **tool** is what the mouse does in the drawing: select, draw a rectangle, write a text.
- A **mode** changes what the editor is for. Switching mode changes the tools of the tool bar and what the right-hand panel shows.
- Nothing is hidden behind a double click: to edit points, the user switches to the point editing mode.
- Key shortcuts and modifier keys are allowed, as in every drawing software, but never alone: each one has a visible equivalent (an option in the panel or the tool bar). The software is used by everyone, including an expert of 80 who makes synoptics.
- Everything drawn stays a path, in the layers of an SVG, so the symbol stays a real SVG. A text stays a text, because it can show a value or a unit (see [Animation](04-animation.md)).
- The name "layer" is provisional. A layer can be the target of an animation or of an interaction (see [Animation](04-animation.md) and [Interactions](05-interactions.md)).
- Colours (fill, stroke) and the options of a shape (corner radius, for example) are neither tools nor modes. They are in the right-hand panel, which shows the options that fit the selected shape.

## Moving around the drawing

- Mouse: the scroll wheel, and the middle button held down, which shows the hand while it is held.
- Trackpad: the usual gestures, to scroll and to zoom.
- The [Hand tool](drawing/tool-hand.md) does the same from the tool bar.
- The zoom is shown as a percentage, in one place of the editor, and the user can type a value in it. At 100%, the symbol is shown at its real size.
- Simulating the size of the symbol on another screen is not done here but in the Run mode (see [Testing](06-testing.md)).

## Map of the pages

| Kind | Pages |
| --- | --- |
| Modes | [Modes](drawing/modes.md) (the list), [Point editing](drawing/mode-point-editing.md), [Alignment](drawing/mode-alignment.md). The Interaction, Animation and Run modes are in [Interactions](05-interactions.md), [Animation](04-animation.md) and [Testing](06-testing.md). |
| Tools | [Select](drawing/tool-select.md), [Hand](drawing/tool-hand.md), [Rectangle](drawing/tool-rectangle.md), [Ellipse](drawing/tool-ellipse.md), [Polygon](drawing/tool-polygon.md), [Text](drawing/tool-text.md), [Pen](drawing/tool-pen.md) |
| Neither tool nor mode | [Groups](drawing/groups.md) |
| Expert menu | [Expert menu](drawing/expert-menu.md), [Boolean operations](drawing/expert-boolean-operations.md), [Placement and duplication](drawing/expert-placement-and-duplication.md) |

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Paths, text, groups, layers | Symbol editor | Symbol drawing, animation and interaction targets | Draw, edit | No |

## Open questions

The open questions of the drawing are on the pages they concern, and listed in [Open questions](07-open-questions.md).
