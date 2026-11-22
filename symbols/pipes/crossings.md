# Crossings

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Crossings

Status: draft. Not validated.

A crossing is a place where a pipe passes over another one without being connected to it.

## Rules

- The user chooses the **type of crossing** in the **base pipe style**, and a pipe style can override it (see [Pipe styles](pipe-styles.md)); it is not a separate list of the Symbol Lib:

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

| Pipe style | Crossing type | Corner radius of the style | Result |
| --- | --- | --- | --- |
| Water | Bridge | 8 px | Round arch |
| Cooling water | Bridge | 0 | Square arch |
| Oil | Gap | any | Interruption |
| Electricity | None | any | One over the other |

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.1, 3.3, 3.4, 3.5, 3.7).

- Everywhere, a crossing is an arc, a gap, a square or nothing, **with a size**: draw.io (none, arc, gap, sharp; one size), Visio (smooth arc, gap, square, multi-sided arc; horizontal and vertical size), JointJS (arc, cubic, gap; size 5 by default), yFiles (gap, arc, rectangle, two sides), Plant 3D (gap or loop, with a width), Ignition (a gap of 4 by default, 0 removes it). Confidence: high.
- Which pipe passes over: the stacking order (draw.io: the link on top jumps), the orientation (yFiles), or a page setting (Visio). No software read offers the click of the project. The archived Figma page has it: hover a crossing, click to swap; the panel of the pipe lists all its crossings and offers "swap all".
- Ignition hit the limit of the number of masks of the browser with its gaps, and added a setting that removes them "for a possible performance gain". GoJS warns that jumps need considerable computation with many links.

### Opinion of the report

| Point | Proposal |
| --- | --- |
| Size | Set in the pipe style: size of a bridge; for a gap, the width of the pipe on top plus a fixed clearance on each side. |
| Default rule | The **last drawn pipe passes over**; the click in the synoptic is the exception, kept per crossing. |
| Drawing | Never with a mask: the pipe underneath is really cut, the one on top really deviated. |
| Bridge and corner radius | Radius of the bridge equal to the corner radius, bounded by the size of the bridge; at radius 0, a square bridge (shapes that exist in Visio and yFiles). |
| Crossing on a rounded corner, or too close to a corner, a junction or another crossing | Fall back to a gap, or draw nothing. |
| Two parallel pipes laid on each other | Not a crossing: draw nothing. |
| Three pipes or more at one point | An order between the pipes, then each pair; neighbouring bridges merge. |
| Name | **Crossing**, of type **Bridge**, **Gap** or **None**. |

## Open questions

- Size of a bridge or of a gap, default rule "last drawn on top": proposed by the report, to confirm.
- Does a bridge keep the borders of the pipe (the border follows the arch)?
