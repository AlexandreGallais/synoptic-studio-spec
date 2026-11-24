# Preview

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Preview

Status: draft. Not validated.

When the user edits the base pipe style or a pipe style in a Symbol Lib (body, border, fills, junctions, crossings), the **Preview** shows it on every case a pipe can meet. It lets the user understand what an edit does without drawing a synoptic.

## Rules

- The Preview is part of the editor of the Symbol Lib: it is always visible next to the style being edited, and it redraws at each change.
- It is **exactly the same** for the base pipe style and for every pipe style: the same cases, at the same places (Product Owner, 2026-11-24).
- It holds a fixed set of cases, made of pipes drawn with the style being edited:

| Case | What it shows |
| --- | --- |
| Straight pipe | The body fill, the width, the border, the dash sequences. |
| Right angle | The corner radius. |
| Other angles | An angle other than 90 degrees, a very short segment. |
| Junction | One junction of the style, centred on the point where the branch leaves the pipe. |
| Several junctions | A 3-way and a 4-way junction. |
| Crossing | The style being edited passes over a pipe of the **base style**, with its crossing kind: the user sees the style next to the base (Product Owner, 2026-11-24). |
| Free ends | A pipe whose two ends are connected to nothing (proposed). |
| Connected to a symbol | A pipe that arrives on a connection point. |

- The cases are not editable by the user.

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Preview | Computed from the style being edited | Pipes page of a Symbol Lib ([PI-05](../../screens/pipes.md#pi-05--preview)) | No | No |

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, section 3.15).

- The archived Figma page calls it "Pipe style preview"; the report advised **Preview**, the name kept.
- Cases to add if the corresponding rules are kept: a crossing on a corner and near a junction.
- Case to add, since a symbol can be connected to a pipe: a symbol connected to a straight segment and to a bend (proposed by the assistant).

## Open questions

- Is the list of cases fixed or can the user add their own?
- Does the Preview also show several styles together (water and oil crossing, steam meeting water)?
- Is it also available in the Run mode, with the flow dashes moving?
