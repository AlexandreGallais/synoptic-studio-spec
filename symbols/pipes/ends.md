# Pipe ends

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Pipe ends

Status: draft. Not validated.

A start shape and an end shape can be set on a pipe. They are made in a list of the Symbol Lib and chosen in the synoptic.

## Rules

- End shapes are **not** in the base pipe style. They have **a list of their own** on the Pipes page of the Symbol Lib, after the pipe styles: the user adds a shape there and sets it up (see [Screens of the pipes](../../screens/pipes.md#layout-of-the-page-pipes)).
- The same list holds the shapes for the start and for the end of a pipe (assistant's reading: one shape can serve at either end).
- In the synoptic, each end of a pipe offers a shape, or none (as in the archived Figma page).

- An end shape is drawn in a small editor of its own: a **box** of the size the user wants, with an **anchor** at each side and each corner of the box (see [Anchors](../03-editor/anchors.md)).
- The user draws the shape freely inside the box, with the tools of the [drawing mode](../04-drawing-mode/README.md).
- The anchor says where the pipe is attached to the shape, and so how the shape is placed on the end of the pipe.
- The fill of the shape follows the colour of the pipe: when the pipe changes style, the end changes colour with it.
- A pipe can have a start shape, an end shape, both, or none. The start and the end can be different shapes.

## Example

| End shape | Drawn as | Anchor |
| --- | --- | --- |
| Arrow | A triangle | Middle of the back side |
| Flange | A thin rectangle across the pipe | Middle of the box |
| Cap | A half circle | Middle of the flat side |

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.5, 3.7, 3.18).

- The archived Figma page draws a start or end "part" in a W × H box with **four anchors, at the middle of the sides**: the user picks the side where the pipe attaches; the drawing may go outside the box; nothing is scaled; each end of a pipe offers the parts of its style, or none; a part can be copied from another style. The specs say nine anchors: to decide.
- SVG has start, middle and end markers; a marker can take the paint of the line that uses it (`context-stroke`, support per engine not read). draw.io and GoJS have arrowheads.
- Opinion of the report: **one single concept of end shape**, for the lines drawn in symbols (see [Fill and border](../04-drawing-mode/fill-and-border.md)) and for the pipes. Since end shapes now live in the pipe style, how a line of a symbol would reach them is open (below).
- Names: **Start**, **End**, and **End shape** for the shape; avoid "cap", which is the end of a stroke in SVG.

## Open questions

- Four anchors on the sides (archived Figma page) or nine (current specs)?
- Can every pipe style use every end shape of the list, or does a style restrict them?
- The arrows of a line drawn in a symbol: their own shapes, or the end shapes of a pipe style?
- Is the whole shape filled with the pipe colour, or only the parts the user marks (so that a border stays its own colour)?
- Does the end shape rotate with the last segment of the pipe, and can it be mirrored?
- Is the end shape a symbol of the lib (a symbol without a type, with a connection point) or a separate kind of object?
- Does the end shape change the length of the pipe, or does it sit on top of the end?
