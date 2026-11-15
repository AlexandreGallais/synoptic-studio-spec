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

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.1, 3.3, 3.7, 3.15, 3.17).

- A connection point carries a **position and a direction** in Visio (inward, outward, both) and in libavoid (the visible sides of a "pin"). The assumption of the assistant is confirmed. Confidence: high.
- A link can be **fixed** to a point or **floating** around the shape (draw.io). In draw.io a fixed link follows its symbol; in Ignition a pipe does not follow a moved component. The project wants the pipe to follow: the convention of diagram software.
- In libavoid, the connection points follow a rotation by quarter turns and a mirror of the shape.
- The inline symbols of the archived Figma page (valves, reducers, flow arrows) have two connection points. Opinion of the report: **a symbol without animation can have connection points** (a tank outline, an arrow), with names and search, no categories. Since 2026-11-15 every symbol is of the same kind, with or without a type: any symbol can have connection points.
- Name: keep **Connection point**; "anchor" is already the word for the nine anchors of a box.

## Open questions

- Which mode or tool places the points (the Connection mode is still an assumption).
- Whether a point carries a name (inlet, outlet, port A, port B), and whether the name is linked to Metadata (for example a signal "flow through port A").
- The size of the zone where a pipe snaps.
- What happens to a pipe when a symbol changes its connection points. Rotation by quarter turns and mirror in a synoptic: the points and their directions follow (opinion of the report), to confirm in part 3.
