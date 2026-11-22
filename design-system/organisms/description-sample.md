# description-sample

> [Home](../../README.md) › [Design system](../README.md) › [Organisms](README.md) › description-sample

Sample content of a description, to show how the visual editor draws what a user writes: Heading 1 to 6, a paragraph with a bold word, and a table under the mouse. Not a control: the content of the [markdown-editor](markdown-editor.md) when its property `sample` is on.

## Figma

| Node | Id |
| --- | --- |
| Component | [`732:2755`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=732-2755) |

## Variants and states

![Table of description-sample](images/table-description-sample.svg)

## Behaviour

- Each heading uses its text style `content-h1` to `content-h6`; the paragraph `body`, its bold `body-strong` ([Foundations](../02-foundations.md#styles-of-a-description)).
- Every heading is larger than the paragraph, down to Heading 6 (Product Owner, 2026-11-23).
- Shown by the screen [MD-03 · Documentation · headings and table](../metadata/02-documentation.md#md-03--documentation--headings-and-table).

## Made of

| Component | Role |
| --- | --- |
| [content-table](../molecules/content-table.md) | The table, in `state=hover`. |
