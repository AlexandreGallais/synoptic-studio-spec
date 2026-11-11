# Effects and masks of a shape

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Effects and masks

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

Effects (SVG filters) and masks are set from the right-hand panel, like the [fill and border](fill-and-border.md). The Product Owner does not know SVG filters well: the editor must offer them in a menu, not ask the user to write anything.

## Rules

- **Effects menu**: each shape has an "Effects" menu in the right-hand panel, to add, edit and remove effects.
- **Mask**: a shape can be shown only through another shape. Example: a big circle, of which only the part inside a triangle is shown. The shape that cuts is chosen by the user.
- **Performance comes first**: an effect is offered only if it keeps the performance objective (see the project criteria on gestures and 120 Hz). Filters are expensive in SVG, especially on large areas or over an animated content.
- If an effect or a setting makes the performance fall too much, it is not offered. The answer is "not possible", and the limit goes in the research report of the performance POC.

## Proposed effects, to confirm

Proposed by the assistant. Which ones are kept depends on the performance POC.

| Effect | Notes |
| --- | --- |
| Drop shadow |  |
| Inner shadow |  |
| Blur of the shape |  |
| Blur of what is behind the shape | Not native in SVG. Simulated: a blurred copy of what is below, cut to the shape. The most expensive one. |
| Colour changes | Saturation, hue, grey levels. |
| Mask by a shape | Hard edge (cut) or soft edge (the mask gives the transparency). |

## Open questions

- Which effects are kept: to decide with the performance POC. See [Open questions](../10-open-questions.md).
