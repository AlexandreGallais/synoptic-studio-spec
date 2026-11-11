# Pipe styles

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Pipe styles

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

A pipe style says how a pipe looks according to what it contains. The user creates several of them in a Symbol Lib, one per content.

## Rules

### What a style holds

| Option | What it does |
| --- | --- |
| Name | Free text. Example: "Water", "Oil", "Steam", "Electricity". |
| Fill | The colour of the inside of the pipe (the "background colour"). |
| Width | The thickness of the pipe line, in pixels. |
| Border | Optional. A border on each side of the pipe, with its own size and colour, like the [border of a shape](../04-drawing-mode/fill-and-border.md) (never an SVG stroke). |
| Corner radius | Rounds the right angles of the pipe (see below). |
| Flow dashes | Optional. Dashes that go from the start of the pipe to its end (see below). |
| Junctions | How a branch looks: flat, circle or square (see [Junctions](junctions.md)). |
| Crossings | What happens where a pipe of this style passes over another: bridge, gap, none (see [Crossings](crossings.md)). |
| Start and end shapes | The shapes a pipe of this style can have at its start and at its end (see [Pipe ends](ends.md)). |

- Junctions, crossings and end shapes are **parts of the pipe style**, not separate lists of the Symbol Lib (decided by the Product Owner, 2026-11-11). They are computed from the style; the user never draws them on each pipe.

- The content ("what the pipe contains") only names and groups the styles: electricity, water, oil, steam... The editor does not know what a fluid is.
- A pipe has one style, chosen in the synoptic.
- A style is stored in the Symbol Lib and used by name or identifier, as a symbol is linked to its type (the rules of broken links are to be written like for symbols).

### Corner radius

- The user draws a pipe with straight segments only: click, click, click.
- The corner radius, set in the style, rounds each angle of the pipe. A right angle then gets a curve, which makes the pipe a little more stylised.
- With a radius of 0, the angles stay sharp.
- The radius also decides the look of the bridges at crossings (see [Crossings](crossings.md)).

### Flow dashes

- Dashes run along the pipe, from its start to its end.
- The user sets the length of a dash, the gap between two dashes and the colour.
- It shows the direction of the flow.
- Not decided: whether they move (animated), and whether the pipe's own signals drive them (see the questions).

## Example

| Style | Fill | Width | Border | Corner radius | Flow dashes |
| --- | --- | --- | --- | --- | --- |
| Water | Blue | 6 px | Grey, 1 px | 8 px | None |
| Steam | White | 6 px | Grey, 1 px | 8 px | White, 4 px, gap 4 px |
| Electricity | Yellow | 2 px | None | 0 | None |

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.2, 3.4, 3.5, 3.6, 3.7).

### Name of the content

- Words found: service, fluid, appearance, line variation, content. Opinion of the report: keep **Content**, as a simple group label ("fluid" excludes electricity; "service" is the trade word, to quote in the documentation).

### Body and borders: two ways

| Way | Principle | For | Against |
| --- | --- | --- | --- |
| A · Two strokes on top of each other | A wide stroke (the border) under a narrower one (the body), on the same centre line. It is what the archived Figma page does ("Pipe — outline", "Pipe — core"). | Native, no outline to compute, native dashes possible. | These are SVG strokes, which the rule above excludes for the border. |
| B · Computed outlines | The engine computes the polygons of the body and of each border by offset. | Follows "a border is a fill"; a gradient across the pipe is possible. | Computed at each move of a point; native dashes do not exist on a fill. |

The report advises deciding on the POC P9 (see [Pipes](README.md)).

### Flow dashes

- Native dashes (`stroke-dasharray`, moved by `stroke-dashoffset`) exist only on a **stroke**; SVG 2 has no inner or outer stroke. Native dashes therefore mean a stroke centred on the line of the pipe.
- Animating them redraws the path at every frame, on the main thread (only transforms and opacity are animated off it). A user reported in 2022 that a single `stroke-dashoffset` animation raised the load of Safari (WebKit bug open). No source says that an engine refuses it.
- An animation that lasts more than five seconds must be possible to pause (WCAG), and the system setting "reduce motion" can be read by the browser.
- Opinion of the report:
  1. The flow dashes are a **separate stroke**, centred on the line of the pipe, above the body: the only exception to "a border is a fill", written as such. Confidence: medium.
  2. Animated only when a flow is present; one CSS animation shared by all the pipes of the same step; stopped by a global setting and by the system's "reduce motion".
  3. POC **P10**: 10, 100, 500 animated pipes; `stroke-dashoffset` by CSS, by SMIL, and by steps in JavaScript; Chromium, Firefox, WebKit.

### What can drive the look of a pipe

| Option | Principle | Opinion of the report |
| --- | --- | --- |
| A · Nothing | The pipe is a drawing; its dashes are fixed. | The simplest; poor compared with SCADA tools (ThingsBoard: fluid present, flow present, direction, speed, leak). |
| B · The pipe has a type of Metadata | A "dynamic" pipe style is linked to a type (signals: flow present, direction, state), like a dynamic symbol. | **Advised**, limited to three signals: a boolean "flow present" (dashes moving or still), a direction (forward, backward: sign of the offset), an enum of state that changes the style (hot, cold). A speed proportional to the flow is refused first: the eye cannot read it. Confidence: low (one tool source). |
| C · The pipe borrows a signal of a neighbouring symbol | In the synoptic, a signal of a connected symbol is picked. | Quick, but links a drawing to another in a fragile way. |

## To decide by the Product Owner

1. Body and borders: two strokes (way A) or computed outlines (way B)? After the POC P9.
2. Flow dashes: a native stroke as the only exception to the border rule (advised), computed dashes, or no animated dashes?
3. What drives a pipe: nothing, a type of Metadata with three signals (advised), or a signal of a neighbour?

## Open questions

- Is the corner radius a property of the style or of each pipe or each corner? The archived Figma page keeps it in the style and chooses the path kind (straight, right angles, rounded) per pipe.
- Can a style hold several layers (the fill, then a border, then a second line), or just the options above?
