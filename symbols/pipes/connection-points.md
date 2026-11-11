# Connection points

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Connection points

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

A connection point is a place of a symbol where a pipe can be attached.

## Rules

- A symbol has as many connection points as it has pipe connections. A two-way valve has 2, a three-way valve has 3. A symbol with none cannot be connected.
- The user places them in the symbol editor, on the drawing, while creating the symbol.
- Each point has a position, and a direction in which the pipe leaves it (assumed by the assistant: a pipe arrives straight at a symbol, see the questions).
- A connection point is not a shape: it is not drawn in the exported SVG of the symbol and it has no fill or border.
- In a synoptic, a pipe snaps to the connection points of the symbols and follows them when a symbol is moved.

## Where it is made in the editor

Provisional, by the assistant: a **Connection point** tool, in a mode of its own ("Connection" mode) with the Select and Hand tools, like the Interaction mode has its zone tool. The Product Owner did not say where the tool lives: it is a question (see [Open questions](../10-open-questions.md)).

## Open questions

- Which mode or tool places the points, and whether they are also for static symbols (a tank outline has connections, but no type).
- Whether a point carries a name (inlet, outlet, port A, port B), and whether the name is linked to Metadata (for example a signal "flow through port A").
- The direction of the pipe at the point (any, or fixed by the symbol), and the size of the zone where a pipe snaps.
- What happens to a pipe when a symbol changes its connection points, or when a symbol is rotated or mirrored in a synoptic.
