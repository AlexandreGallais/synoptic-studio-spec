# Test display

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Test display

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

When the user edits a pipe style in a Symbol Lib (its body, junctions, crossings and end shapes), a test display shows it on every case a pipe can meet. It lets the user understand what an edit does without drawing a synoptic.

## Rules

- The test display is part of the editor of the Symbol Lib: it is always visible next to the style being edited, and it redraws at each change.
- It holds a fixed set of cases, made of pipes drawn with the style being edited:

| Case | What it shows |
| --- | --- |
| Straight pipe | The fill, the width, the border, the flow dashes. |
| Right angle | The corner radius. |
| Other angles | An angle other than 90 degrees, a very short segment. |
| Junction | One junction of the style. |
| Several junctions | A 3-way and a 4-way junction. |
| Crossing | One crossing of the style, both ways. |
| Start and end | The start and end shapes of the style. |
| Connected to a symbol | A pipe that arrives on a connection point. |

- The cases are not editable by the user.

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, section 3.15).

- The archived Figma page calls it "Pipe style preview". Opinion of the report: rename "Test display" to **Preview**.
- Cases to add if the corresponding rules are kept: an inline symbol on a pipe, a crossing on a corner and near a junction, a branch (see [Pipes](README.md)).

## Open questions

- Name: Preview, to confirm.
- Is the list of cases fixed or can the user add their own?
- Does the test display also show several styles together (water and oil crossing, steam meeting water)?
- Is it also available in the Run mode, with the flow dashes moving?
