# list-panel

> [Home](../../README.md) › [Design system](../README.md) › [Organisms](README.md) › list-panel

A titled list with its +: a [list-title](../molecules/list-title.md) and [list-row](../molecules/list-row.md) lines.

## Figma

| Node | Id |
| --- | --- |
| Component set | [`640:651`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=640-651) |

## Variants and states

![Table of the variants and states of list-panel](images/table-list-panel.svg)

## Inputs

| Input | Type | Default | Figma |
| --- | --- | --- | --- |
| `title` | text | — | its list-title |
| `items` | list of rows | — | slot `rows`, filled with list-row |
| `selected` | the selected item | none | the list-row in `state=selected` |
| `empty` | — | — | `state=empty`: a message |

## Outputs

| Output | When | Value |
| --- | --- | --- |
| `select` | A line is chosen. | the item |
| `add` | The + of the title. | — |
| `delete` | The delete of a line. | the item |

## Made of

| Component | Role |
| --- | --- |
| [list-title](../molecules/list-title.md) | Its title and its +. |
| [list-row](../molecules/list-row.md) | Each item, in the slot rows. |
