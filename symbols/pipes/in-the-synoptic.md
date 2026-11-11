# Pipes in the synoptic

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Pipes in the synoptic

Status: draft, from the Product Owner's description of 2026-11-11. Not validated. This page belongs to part 3 (the synoptic), which is not written yet. It only records what the Product Owner said about pipes, so that it is not lost.

## Rules

- In the synoptic mode, a **pipe tool** draws pipes between the connection points of symbols (see [Connection points](connection-points.md)).
- The user clicks point after point. The segments are straight. Everything else is computed (see [Pipes](README.md)).
- **Junction**: the user clicks inside an existing pipe, then draws another one. The editor computes the junction and splits the pipe in two. The junction takes the junction style (see [Junctions](junctions.md)).
- **Crossing**: where a pipe passes over another, the editor computes a bridge, a gap or nothing, according to the crossing style (see [Crossings](crossings.md)).
- **Which pipe is on top**: when the mouse is over a crossing, the editor highlights it. A click changes which of the two pipes passes over the other.
- The user chooses the style of each pipe among those of the Symbol Lib, and its start and end shapes (see [Pipe ends](ends.md)).

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.1, 3.3, 3.5). To use when part 3 is written.

- Drawing: Ignition draws orthogonal segments by default (Alt: steps of 15 degrees, Shift: free). Opinion: an **orthogonal lock** while drawing, like the angle lock of the pen.
- The archived Figma page gives a pipe a panel: style (with "edit this style"), path kind (Straight, Right angles, Rounded), start and end, inline symbols with their position in percent, crossings (with "swap all").
- **Inline symbol** (archived page, Plant 3D): right click on the pipe, pick a symbol with two connection points; it slides along the pipe, bends included, without leaving it; removed, the pipe keeps its place and points. Advised by the report.
- A branch leaves one pipe as a tree in the archived page and in Ignition (see [Junctions](junctions.md)).
- Automatic routing (libavoid): not in the first version, the user draws by clicks.

## Open questions

- Which Symbol Lib do the pipe styles come from when a synoptic uses several libraries?
- How is a pipe attached when it is moved, split, joined or deleted, and what happens to the junctions?
- Are pipes linked to the model (a pipe has a signal, a flow direction)? See the questions on the flow dashes in [Pipe styles](pipe-styles.md).
- How is a pipe drawn between two points that are not at right angles, and how does the editor route it (automatic routing or only the user's clicks)?
