# Effects and masks of a shape

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Effects and masks

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

Effects and masks are set from the right-hand panel, like the [fill and border](fill-and-border.md). The Product Owner does not know SVG filters well: the editor offers them in a menu, and the user writes nothing.

## Rules

- **Only what SVG does natively.** Every effect and every mask comes from the SVG itself: its filters, its `clipPath` and its `mask`. Nothing is simulated with copies or tricks. An effect that SVG does not do natively is not offered. This is why there is no "blur of what is behind the shape".
- **Effects menu**: each shape has an "Effects" menu in the right-hand panel, to add, edit and remove effects.
- **Mask**: a shape can be shown only through another shape. Example: a big circle, of which only the part inside a triangle is shown. The shape that cuts is chosen by the user.
- **Performance comes first**: an effect is offered only if it keeps the performance objective (see the project criteria on gestures and 120 Hz). Filters are expensive in SVG, especially on large areas or over an animated content. The goal: never offer something that lags, so the final result stays smooth.
- If an effect or a setting makes the performance fall too much, it is not offered. The answer is "not possible", and the limit goes in the research report.

## Proposed effects, to confirm

Proposed by the assistant, all native in SVG. Which ones are kept depends on the research and the performance POC.

| Effect | SVG feature | Notes |
| --- | --- | --- |
| Drop shadow | Filter |  |
| Inner shadow | Filter |  |
| Blur of the shape | Filter |  |
| Colour changes | Filter | Saturation, hue, grey levels. |
| Cut by a shape | `clipPath` | Hard edge. The cheapest. |
| Mask by a shape | `mask` | Soft edge: the mask gives the transparency. |

## Open questions

- None kept here. Which effects are kept is in the [research brief](../research-brief.md): a documentary research, launched at the end, then the performance POC.
