# Crossings

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Crossings

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

A crossing is a place where a pipe passes over another one without being connected to it.

## Rules

- The user chooses the **type of crossing** in a crossing style of the Symbol Lib:

| Type | What happens |
| --- | --- |
| Bridge | The pipe that passes over makes a bridge (an arch) above the other one. |
| Gap | The pipe underneath is interrupted where the other one passes. |
| None | Nothing special: one pipe is drawn on top of the other. |

- Bridges and gaps are always computed.
- The look of a bridge follows the **corner radius** of the pipe: the bigger the radius, the rounder the bridge, to follow the style of the pipe. With a radius of 0, the bridge is rather square.
- A gap is always the same: the interruption, nothing more.
- In a synoptic, the user can choose which of the two pipes passes over the other (see [Pipes in the synoptic](in-the-synoptic.md)).

## Example

| Crossing style | Type | Radius of the pipe | Result |
| --- | --- | --- | --- |
| Rounded bridge | Bridge | 8 px | Round arch |
| Square bridge | Bridge | 0 | Square arch |
| Cut | Gap | any | Interruption |
| Overlap | None | any | One over the other |

## Open questions

- Size of a bridge or of a gap: fixed, a multiple of the width, set in the style?
- Several pipes crossing at one point, or two pipes crossing at a corner: what does the computation do?
- Does a bridge keep the borders of the pipe (the border follows the arch)?
- Which pipe is on top by default (the last drawn, the first)?
