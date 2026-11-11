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

## Open questions

- Is the corner radius a property of the style or of each pipe or each corner?
- Do flow dashes move, and what drives them (a signal of a symbol, a state of the pipe)? Is there a direction reversal?
- Can a style hold several layers (the fill, then a border, then a second line), or just the options above?
- Can a pipe style be animated like a symbol (a colour that depends on a signal: hot water, cold water)?
- A name for the concept "what a pipe contains" (content, fluid, medium, service, line type): see question 11 of the [research brief](../research-brief.md).
