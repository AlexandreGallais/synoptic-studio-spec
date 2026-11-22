# formatting-toolbar

> [Home](../../../README.md) › [Design system](../../README.md) › [Organisms](../README.md) › formatting-toolbar

The tool bar of the documentation editor: the heading [select-trigger](../../atoms/select-trigger/README.md), the [toolbar-group](../../molecules/toolbar-group/README.md) of formatting, the [segmented-control](../../molecules/segmented-control/README.md) Visual or Markdown, and the full page [icon-button](../../atoms/icon-button/README.md). The same groups in both modes.

## Figma

| Node | Id |
| --- | --- |
| Component set | [`642:1302`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=642-1302) |

## Variants and states

![Table of the variants and states of formatting-toolbar](table.svg)

## Inputs

| Input | Type | Default | Figma |
| --- | --- | --- | --- |
| `mode` | `visual`, `markdown` | `visual` | variant `mode` |
| `heading` | Paragraph, Heading 1 to 6 | Paragraph | the value of its select-trigger |
| `bold`, `italic` | boolean | `false` | its [toggle-button](../../atoms/toggle-button/README.md): the state of the selected text |
| `fullPage` | boolean | `false` | the icon `full-page` or `exit-full-page` |

## Outputs

| Output | When | Value |
| --- | --- | --- |
| `format` | A formatting button: bold, italic, lists, code, quote. | the format |
| `headingChange` | A level chosen in its list. | the level |
| `insertTable` | A size chosen in the [table-size-picker](../../molecules/table-size-picker/README.md). | columns and rows |
| `modeChange` | Visual or Markdown. | the mode |
| `fullPageChange` | The full page button. | `true` or `false` |

## Behaviour

- Bold and italic are `spacing-02` after the heading select; the other groups are `spacing-03` apart, with a divider.
- The heading list opens right under its select; the table button opens its grid right under it and stays `selected` while it is open.

## Made of

| Component | Role |
| --- | --- |
| [select-trigger](../../atoms/select-trigger/README.md) | Paragraph, Heading 1 to 6. |
| [menu](../../molecules/menu/README.md) | The list of the heading levels. |
| [toolbar-group](../../molecules/toolbar-group/README.md) | Each group of formatting buttons. |
| [toggle-button](../../atoms/toggle-button/README.md) | Bold, italic. |
| [table-size-picker](../../molecules/table-size-picker/README.md) | The grid of the table button. |
| [divider](../../atoms/divider/README.md) | Between the groups. |
| [segmented-control](../../molecules/segmented-control/README.md) | Visual, Markdown. |
| [icon-button](../../atoms/icon-button/README.md) | Full page. |
