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

## Open questions

- Which Symbol Lib do the pipe styles come from when a synoptic uses several libraries?
- How is a pipe attached when it is moved, split, joined or deleted, and what happens to the junctions?
- Are pipes linked to the model (a pipe has a signal, a flow direction)? See the questions on the flow dashes in [Pipe styles](pipe-styles.md).
- How is a pipe drawn between two points that are not at right angles, and how does the editor route it (automatic routing or only the user's clicks)?
