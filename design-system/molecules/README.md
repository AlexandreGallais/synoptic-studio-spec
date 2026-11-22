# Molecules

> [Home](../../README.md) › [Design system](../README.md) › Molecules

Components made of atoms only, for one job. One folder per molecule, with its sheet (`README.md`) and the table of its variants and states exported from Figma (`table.svg`). Only the molecules the screens of Metadata use are here (Product Owner, 2026-11-22).

Figma: page Molecules (`630:106`). The rules every component follows are in [Components](../04-components.md).

## Sheets

| Molecule | What it is | Section of the page |
| --- | --- | --- |
| [field](field/README.md) | A label, an input and a help text. | Forms |
| [menu-item](menu-item/README.md) | One item of a menu. | Forms |
| [menu](menu/README.md) | The list a select opens. | Forms |
| [menu-group-title](menu-group-title/README.md) | The small title of a group of items. | Forms |
| [menu-grouped](menu-grouped/README.md) | A menu whose items are grouped under small titles. | Forms |
| [segmented-control](segmented-control/README.md) | Two or three buttons side by side, one selected. | Forms |
| [radio-group](radio-group/README.md) | Radios and their labels, one checked. | Forms |
| [list-title](list-title/README.md) | The title of a list or a table, with its buttons. | Lists and navigation |
| [nav-rail-item](nav-rail-item/README.md) | An icon of the rail or of the top bar. | Lists and navigation |
| [tree-row](tree-row/README.md) | A line of the type tree. | Lists and navigation |
| [list-row](list-row/README.md) | A line of a list. | Lists and navigation |
| [part-item](part-item/README.md) | One part of a type, under the tree. | Lists and navigation |
| [link-cell](link-cell/README.md) | A cell with a path or a URL. | Table cells |
| [toolbar-group](toolbar-group/README.md) | Icon buttons grouped in a tool bar. | Toolbars and window |
| [table-size-picker](table-size-picker/README.md) | The grid to choose the size of a table. | Toolbars and window |
| [window-controls](window-controls/README.md) | Minimise, maximise, close. | Toolbars and window |

## Left out

Drawn in Figma but not used by the screens of Metadata, so without a sheet for now: `select` (`637:206`; the screens place a [select-trigger](../atoms/select-trigger/README.md) and its [menu](menu/README.md) apart), and the deprecated `quantity-cell` (`638:871`) and `direction-cell` (`638:884`), replaced by a select-trigger with its icon.
