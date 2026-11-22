# Figma file

> [Home](../README.md) › [Design system](README.md) › Figma file

What the Figma file of the design system holds, with the ids a later session needs to go on. Kept up to date at each session that draws in it. File: [Synoptic Studio · Design System](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL).

## Pages

| Page | Id | Holds |
| --- | --- | --- |
| Foundations | `630:103` | The variables and styles, shown with their names. |
| Icons | `630:104` | One component per icon. |
| Atoms | `630:105` | The atoms. |
| Molecules | `630:106` | The molecules. |
| Organisms | `630:107` | The organisms. |
| Templates | `630:108` | The layout of the screens. |
| Metadata | `630:109` | The screens of Metadata. |
| Spec | `466:5` | Wireframes of the specs, drawn before the design system. Not part of the library. |
| POC · … | `5:119` and after | The old design system, for inspiration only; never changed. |

## Variables

| Collection | Id | Modes | Variables |
| --- | --- | --- | --- |
| `primitives` | `VariableCollectionId:630:111` | `value` | 37: 21 colours (`sand/`, `white`, `black`, accents), `black/a60`, 15 steps of `scale/` |
| `semantic` | `VariableCollectionId:630:149` | `sand` (`630:1`) | 49: the roles, spacing, sizes, radii and widths of [Foundations](02-foundations.md) |

The tints `blue/05` and `green/05`, and the roles `signal-input` and `signal-output`, were removed on 2026-11-22 with the background of the signal lines.

## Styles

| Kind | Styles |
| --- | --- |
| Text | `caption`, `body`, `body-strong`, `heading`, `title` (IBM Plex Sans), `code` (IBM Plex Mono) |
| Effect | `shadow-raised`, `shadow-overlay`, `focus-ring`, `focus-ring-inset` |

## Components

The id of each component set (or component), to go on from it. Every one is prototyped (hover, press, click): try them from the frame `playground/…` of its page, a flow starting point.

| Page | Component | Id |
| --- | --- | --- |
| Foundations | specimen board | `630:203` |
| Foundations | documentation kit `docs/kit`: `docs/header`, `docs/section`, `docs/caption`, `docs/do-dont` | `646:2` |
| Icons | 44 icons `icon/<name>`, in the frame `icons/components` | `631:2` |
| Atoms | `button` | `632:209` |
| Atoms | `icon-button` | `633:98` |
| Atoms | `checkbox` | `633:144` |
| Atoms | `radio` | `633:170` |
| Atoms | `toggle` | `633:191` |
| Atoms | `text-input` | `634:127` |
| Atoms | `number-input` | `634:288` |
| Atoms | `text-area` | `634:303` |
| Atoms | `select-trigger` | `634:430` |
| Atoms | `drag-handle` | `635:135` |
| Atoms | `label` | `635:141` |
| Atoms | `tooltip` | `635:158` |
| Atoms | `colour-swatch` | `635:167` |
| Atoms | `divider` | `635:170` |
| Atoms | `playground/atoms` | `643:2164` |
| Molecules | `field` | `637:53` |
| Molecules | `menu-item` | `637:102` |
| Molecules | `menu` | `637:103` |
| Molecules | `select` | `637:206` |
| Molecules | `segmented-control` | `637:250` |
| Molecules | `radio-group` | `637:281` |
| Molecules | `list-title` | `638:143` |
| Molecules | `nav-rail-item` | `638:205` |
| Molecules | `tree-row` | `638:784` |
| Molecules | `list-row` | `638:841` |
| Molecules | `part-item` | `638:850` |
| Molecules | `link-cell` | `638:860` |
| Molecules | `quantity-cell` | `638:871` |
| Molecules | `direction-cell` | `638:884` |
| Molecules | `toolbar-group` | `638:885` |
| Molecules | `window-controls` | `638:936` |
| Molecules | `playground/molecules` | `643:2262` |
| Organisms | `top-bar` | `640:200` |
| Organisms | `nav-rail` | `640:201` |
| Organisms | `tree` | `640:573` |
| Organisms | `part-list` | `640:574` |
| Organisms | `list-panel` | `640:651` |
| Organisms | `dialog` | `640:706` |
| Organisms | `data-table-header` | `641:352` |
| Organisms | `data-table-row` | `641:1229` |
| Organisms | `data-table` | `641:1470` |
| Organisms | `palette-picker` | `641:1471` |
| Organisms | `icon-picker` | `641:1489` |
| Organisms | `formatting-toolbar` | `642:1302` |
| Organisms | `markdown-editor` | `642:1487` |
| Organisms | `faceplate-element` | `642:1828` |
| Organisms | `playground/organisms` | `643:2487` |

`data-table-row` and `data-table-header` have the columns of Signals since 2026-11-22: handle, Direction, ID, Type, Enum, Quantity / Difference, Description, delete, on lines 1120 wide. `direction-cell` has no text property: its word follows its direction.

## Documentation

Each component has a frame `Docs/<component>` on its page, under the components, built from instances of the documentation kit ([Skill rules R9](skill-rules.md#r9--the-documentation-of-the-components-lives-in-figma)). The twelve sections, in order: overview, when to use, variants, anatomy, sizes and spacing, states, behaviours, content, interactions, accessibility, do and don't, code. Variants, anatomy, sizes and states are read from the component itself; the other sections are written. The overview and the use are also in the description of the component.

| Page | Frames |
| --- | --- |
| Icons | `Docs/icon` (`650:2`), for the 44 icons |
| Atoms | 14, `Docs/button` (`647:159`) to `Docs/divider` (`647:2140`) |
| Molecules | 16, `Docs/field` (`648:556`) to `Docs/window-controls` (`648:2567`) |
| Organisms | 14, `Docs/top-bar` (`649:1838`) to `Docs/faceplate-element` (`649:4668`) |

The contrasts the frames give are computed from the values of the variables, not measured on screen.

## Left to draw

- The page Templates and the page Metadata.
