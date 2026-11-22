# content-table

> [Home](../../README.md) › [Design system](../README.md) › [Molecules](README.md) › content-table

A table of a description, as the visual editor shows it: a header line, then its lines, each cell a text. Under the mouse, a small + inserts a line or a column where it sits ([MD-03.13](../../screens/metadata.md#md-03--documentation)).

## Figma

| Node | Id |
| --- | --- |
| Component set | [`732:892`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=732-892) |

## Variants and states

![Table of the states of content-table](images/table-content-table.svg)

## Inputs

| Input | Type | Default | Figma |
| --- | --- | --- | --- |
| `rows` | the lines of the Markdown table, the first one its header | — | the texts of its cells (a sample of 3 columns and 3 lines) |

## Outputs

| Output | When | Value |
| --- | --- | --- |
| `insertRow` | A + between two lines, on the left edge. | the index of the new line |
| `insertColumn` | A + between two columns, on the top edge. | the index of the new column |
| `addRow` | The + under the table. | — |
| `addColumn` | The + on the right of the table. | — |

## Behaviour

- Header line on `layer-02` in `body-strong`, the other lines in `body`; lines of `border-subtle` between cells and around the table, radius `radius-sm`.
- Under the mouse, two + show: the one of the line limit nearest to the mouse (between two lines, or under the table near the bottom edge) and the one of the column limit nearest to it (between two columns, or on the right near the right edge). `state=hover` shows the mouse in the middle of the table, `state=hover-edge` near its bottom right corner.
- A + sits half outside the table, so the component keeps 8 px on its left and top and 24 px on its right and bottom in every state: the table never moves.
- Each + is an [insert-button](../06-atoms/insert-button.md).
- No hover per cell: a cell is edited as text, as in a word processor.

## Made of

| Component | Role |
| --- | --- |
| [insert-button](../06-atoms/insert-button.md) | Each +. |
