# Junctions

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Junctions

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

A junction is a place where a pipe splits in two (or where several pipes meet).

## Rules

- A junction is made in the synoptic: the user draws a pipe, clicks inside another pipe, and draws a new pipe from there. The editor computes the junction and splits the pipe in two (see [Pipes in the synoptic](in-the-synoptic.md)).
- The look of a junction comes from a **junction style**, created in the Symbol Lib.
- A junction style is one of:

| Kind | What it looks like |
| --- | --- |
| Flat | No effect: the pipes simply meet. |
| Circle | A circle at the junction, bigger than the pipe, to show that it is a junction. |
| Square | A square at the junction, bigger than the pipe. |

- A circle or a square has its own size, a fill and a border (size, colour...), as the shapes of the [drawing mode](../04-drawing-mode/README.md) do.
- The junction shape follows the colour of the pipe or has its own colour (to settle, see the questions).

## Example

| Junction style | Kind | Size | Fill | Border |
| --- | --- | --- | --- | --- |
| Flat | Flat | - | - | - |
| Round marker | Circle | 12 px | Pipe colour | 2 px, dark grey |
| Square marker | Square | 12 px | Pipe colour | 2 px, dark grey |

## Open questions

- Where several pipes of different styles meet, which style gives the colour of the junction?
- Is the junction size a fixed value or a multiple of the pipe width?
- Can the junction style be something else than a circle or a square (a free shape, like the ends of a pipe)?
- How are 3-way, 4-way and more junctions, and a junction on a corner, handled by the computation?
