# Boolean operations

> [Home](../../../README.md) › [Symbols](../../README.md) › [Editor](../README.md) › [Advanced tools](README.md) › Boolean operations

Status: draft. Not validated.

## Rules

- Since 2026-11-25, the [Intersection mode](../../04-drawing-mode/intersection-mode.md) of the modes menu builds a new shape from chosen regions: each of the four operations below is one choice of regions in it. This page stays as a record of the advanced tools, set aside.
- The user selects shapes, then picks a boolean operation in the bar of the [advanced tools](README.md).
- The editor goes into a mode where the user picks the kind of operation (intersection and the like).
- The result is a new shape made from the selected shapes.

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, section 3.19). Illustrator and Inkscape were not read.

- Figma offers four operations: **Union**, **Subtract**, **Intersect**, **Exclude**. They destroy nothing: a "boolean group" keeps its shapes editable. The result takes the fill, stroke and effects of the top shape (the bottom one for Subtract).
- Opinion of the report: these four operations, under these four names. The result is a new free form (as written above), with the look of the **first selected shape**, for consistency with the alignment mode. A non-destructive version later. Confidence: medium.

## Open questions

- The four operations, and the look taken from the first selected shape: to confirm. See [Open questions](../../10-open-questions.md).
