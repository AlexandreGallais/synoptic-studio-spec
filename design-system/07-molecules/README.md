# Molecules

> [Home](../../README.md) › [Design system](../README.md) › Molecules

Components made of atoms only, for one job. One sheet per molecule (`<molecule>.md`); the table of its variants and states, exported from Figma, is in [images](images) (`table-<molecule>.svg`). Only the molecules the screens of Metadata and of Symbols use are here.

Figma: page [Molecules](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=630-106) (`630:106`). The rules every component follows are in [Components](../03-components.md).

## Sheets

| Molecule | What it is | Section of the page |
| --- | --- | --- |
| [field](field.md) | A label, an input and a help text. | Forms |
| [menu-item](menu-item.md) | One item of a menu. | Forms |
| [menu](menu.md) | The list a select opens. | Forms |
| [menu-group-title](menu-group-title.md) | The small title of a group of items. | Forms |
| [menu-grouped](menu-grouped.md) | A menu whose items are grouped under small titles. | Forms |
| [segmented-control](segmented-control.md) | Two or three buttons side by side, one selected. | Forms |
| [radio-group](radio-group.md) | Radios and their labels, one checked. | Forms |
| [list-title](list-title.md) | The title of a list or a table, with its buttons. | Lists and navigation |
| [nav-rail-item](nav-rail-item.md) | An icon of the rail or of the top bar. | Lists and navigation |
| [nav-rail-library](nav-rail-library.md) | A Symbol Lib in the rail of the symbol mode. | Lists and navigation |
| [tree-row](tree-row.md) | A line of the type tree. | Lists and navigation |
| [list-row](list-row.md) | A line of a list. | Lists and navigation |
| [part-item](part-item.md) | One part of a type, under the tree. | Lists and navigation |
| [link-cell](link-cell.md) | A cell with a path or a URL. | Table cells |
| [content-table](content-table.md) | A table of a description, with its + on hover. | Table cells |
| [toolbar-group](toolbar-group.md) | Icon buttons grouped in a tool bar. | Toolbars and window |
| [table-size-picker](table-size-picker.md) | The grid to choose the size of a table. | Toolbars and window |
| [window-controls](window-controls.md) | Minimise, maximise, close. | Toolbars and window |

## Left out

Drawn in Figma but not used by the screens of Metadata, so without a sheet for now: `select` (`637:206`; the screens place a [select-trigger](../06-atoms/select-trigger.md) and its [menu](menu.md) apart), and the deprecated `quantity-cell` (`638:871`) and `direction-cell` (`638:884`), replaced by a select-trigger with its icon.
