# Components

> [Home](../README.md) › [Design system](README.md) › Components

Status: first draft, written by the assistant on 2026-11-22 from the [kinds of control](../screens/README.md#kinds-of-control), the [layout rules](../screens/README.md#layout-rules) and the [screens of Metadata](../screens/metadata.md). Not validated.

Every component is named after its structure, never after a screen; the same name in Figma and in code (`text-input` is `atoms/text-input/` in `synoptic-studio-design-system`). Variants are written `property=value`.

## The levels

How the levels build on each other, with an example per level.

```mermaid
flowchart LR
    T["Tokens"] --> A["Atoms: button, text-input"]
    A --> M["Molecules: list-title, tree-row"]
    M --> O["Organisms: tree, data-table, dialog"]
    O --> S["Screens of the page Metadata: MD-04 Signals"]
```

## States every interactive component has

| State | When |
| --- | --- |
| `default` | At rest. |
| `hover` | The mouse is over it. |
| `pressed` | The mouse button is down on it. |
| `focus` | Reached with the keyboard: the double focus line (`focus-ring`, or `focus-ring-inset` on a line), on the hover background when the component has none. |
| `disabled` | Cannot be used. |

A line of a list, a tree or a table (`tree-row`, `list-row`, `part-item`, `menu-item`, `data-table-row`) has rounded corners, `radius-sm`, like every control (Product Owner, 2026-11-22: "si on met un border radius, j'aimerais bien qu'il soit partout"). Its list (`tree`, `part-list`, `list-panel`, `data-table`) leaves `spacing-03` on each side and `spacing-01` between lines, so a line in `hover` or `selected` never touches the edges.

The tables below add the states each component needs on top of these. A field (`text-input`, `number-input`, `text-area`) has no `pressed`: a click puts it in `focus`.

Every component is shown in the Figma file as a table of its variants and its states, grouped by family: see [Figma file](05-figma-file.md#how-a-page-shows-its-components) and [Skill rules R9](skill-rules.md#r9--components-shown-as-tables-of-variants-and-states).

Every interactive component is prototyped in its component set: `hover` while the mouse is over it, `pressed` while its button is down, and a click to the next state (checked, on, open, selected, expanded). See [Skill rules R8](skill-rules.md#r8--components-prototyped-on-their-own).

## Atoms

| Component | Variants | States added | Screens |
| --- | --- | --- | --- |
| `icon` | One component per icon of [Icons](03-icons.md), `icon/<name>`; the size is set on the instance, `size-icon-sm` (16) or `size-icon-md` (20), never a variant | — | Everywhere |
| `button` | `kind=primary, secondary, ghost, danger`; `size=md, lg`; leading icon on or off | — | Dialogs: Cancel, Delete |
| `icon-button` | `kind=ghost, quiet` (quiet: `icon-secondary`, the + on hover); `size=sm, md` | `selected` | Every + of a title, delete, reset, search, full page |
| `text-input` | `size=sm, md` (sm in a table cell); with or without a trailing icon | `filled`, `read-only`, `error` | MD-02.1, MD-03.8, every ID |
| `number-input` | `size=sm, md`; with or without a unit; with or without the `variable` icon | `filled`, `read-only`, `error`, `variable` (the value comes from a signal) | MD-07.13, MD-07.22, MD-08.13, MD-09.6 |
| `text-area` | — | `filled`, `read-only`, `error` | MD-09.11, the description element |
| `select-trigger` | `size=sm, md`; with or without a leading icon | `open`, `filled`, `read-only`, `error` | MD-04.7 to MD-04.12, MD-05.4, MD-07.12 |
| `checkbox` | `checked=false, true, mixed` | — | MD-13.8 |
| `radio` | `checked=false, true` | — | MD-07.11 |
| `toggle` | `on=false, true` | — | Boolean input of a faceplate (MD-07.10) |
| `drag-handle` | — | `dragging` | Every ordered table |
| `label` | `required=false, true` | — | Every field outside a table |
| `tooltip` | `placement=top, right, bottom, left` | — | Every icon alone |
| `colour-swatch` | `size=sm, md` | `selected` | MD-02.6 |
| `divider` | `direction=horizontal, vertical` | — | Rail, panels |

## Molecules

| Component | Made of | Variants | States added | Screens |
| --- | --- | --- | --- | --- |
| `field` | `label` + one input atom + help text | `layout=stacked, inline` | `error` (help in `danger`) | General, Units |
| `menu-item` | `icon` + text + check | with or without icon | `selected` | Every select |
| `menu` | `menu-item` × n | — | — | Every select |
| `select` | `select-trigger` + `menu` | — | `open` | Every select |
| `segmented-control` | two or three `button` side by side | `items=2, 3`; `selected=1, 2, 3` (the item selected) | — | MD-07.2b Values / Faceplate, MD-03.4b Read only / Visual / Markdown |
| `radio-group` | `radio` × n + labels | `orientation=horizontal, vertical` | — | MD-07.11, enum input of a faceplate |
| `list-title` | text `body-strong` + `icon-button` × n (one + per kind, search) | `actions=add, search-add, several-add` | `searching` (the title becomes a `text-input`, the + a `dismiss`) | Every list and table: Type tree, Signals, Links, Elements |
| `nav-rail-item` | `icon-button` + `tooltip` | — | `selected` | MD-00 |
| `tree-row` | `icon` chevron + type `icon` in its colour + name + quiet `add` | `depth=0…n`; `has-children=false, true` | `selected`, `expanded` | MD-01.1, MD-01.3 |
| `list-row` | name + `icon-button` delete | with or without delete | `selected` | Presets, Enums, Unit systems |
| `part-item` | text of a part | — | `selected` | MD-01.5 |
| `link-cell` | `folder` or `link` icon + path or URL | `kind=path, url` | — | MD-03.9 |
| `quantity-cell` | `quantity` or `difference` icon + name | `kind=quantity, difference` | — | MD-04.9 |
| `direction-cell` | `signal-input` or `signal-output` icon + text; the icon in `icon-primary`, the same colour for both directions | `direction=input, output` | — | MD-04.12, MD-07.9 |
| `toolbar-group` | `icon-button` × n | — | — | MD-03.4d |
| `window-controls` | minimise, maximise or restore, close | `platform=windows, macos` | — | Top bar |

## Organisms

| Component | Made of | Variants | States added | Screens |
| --- | --- | --- | --- | --- |
| `top-bar` | `app-mark` + `nav-rail-item` × 3 (the parts) + `window-controls` | `platform=windows, macos, browser` | one part `selected` | Every screen |
| `nav-rail` | `nav-rail-item` × n + `divider` | — | one item `selected` | MD-00, SY-00 |
| `tree` | `list-title` + `tree-row` × n | — | `searching`, `empty` | MD-01 |
| `part-list` | `part-item` × n | — | one part `selected` | MD-01.5 |
| `data-table` | `list-title` + `data-table-header` + `data-table-row` × n (`drag-handle`, inputs, cell molecules, delete) | — | table `empty` | MD-03.5, MD-04, MD-05, MD-07.7, MD-08.7, MD-09.5, MD-12, MD-13 |
| `data-table-header` | the name of each column, `caption` | — | — | Every data-table |
| `data-table-row` | the cells of one line, drawn with the columns of Signals | `kind=default, inherited, error`; no background per direction (Product Owner, 2026-11-22: the direction is told by the icon of `direction-cell` only) | `hover`, `selected`; `inherited`: read only, no handle nor delete, the name of its parent | Every data-table |
| `list-panel` | `list-title` + `list-row` × n | — | `empty` | MD-07.1, MD-08.1, MD-09.1 |
| `dialog` | `heading` + text + `button` × 2 | `kind=warning, danger` | — | Every delete |
| `formatting-toolbar` | `toolbar-group` × n + `segmented-control` + full-page `icon-button` | `mode=visual, markdown` | — | MD-03.4d |
| `markdown-editor` | `formatting-toolbar` + editing area | `mode=read-only, visual, markdown` | `full-page` | MD-03.1 to MD-03.4c |
| `faceplate-element` | `drag-handle` + kind `icon` + fields of its kind + delete | `kind=signal, command, title, paragraph, group` | `selected` | MD-07.18 to MD-07.20 |
| `palette-picker` | `colour-swatch` × n + `reset` | — | — | MD-02.6, MD-02.7 |
| `icon-picker` | `icon-button` × n + `reset` | — | — | MD-02.5, MD-02.7 |

## Content states drawn on the page Metadata

Each screen of Metadata is drawn with real content, then once for each state it can show.

| State | Example |
| --- | --- |
| Empty | A type with no signal; no enum yet. |
| One item | One signal. |
| Many items | A deep tree, 40 signals, a table that scrolls. |
| Long text | A long ID, a long description. |
| Error | A line in error (decision 0082); an ID already taken refused when typed (decision 0083). |
| Inherited | A sub-type with inherited signals and commands. |

## Where it is used

| Where | What it uses |
| --- | --- |
| [Screens](../screens/README.md) | Every control of every screen is one of these components. |
| [Number and text fields](../controls/number-and-text-fields.md) | `number-input`, `text-input`. |
| Repository `synoptic-studio-design-system` | The same components, presentational, with the same names. |
