# Figma file

> [Home](../README.md) › [Design system](README.md) › Figma file

What the Figma file of the design system holds, and the ways of Figma a later session needs to go on. Kept up to date at each session that draws in it. File: [Synoptic Studio · Design System](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL).

The id of each icon, component and screen is in its sheet: [Icons](icons/README.md), [Atoms](atoms/README.md), [Molecules](molecules/README.md), [Organisms](organisms/README.md), [Templates](templates/README.md), [Screens of Metadata](metadata/README.md).

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
| `primitives` | `VariableCollectionId:630:111` | `value` | 43: 23 colours (`sand/25` and `sand/30` added on 2026-11-22 for the hover) (`sand/`, `white`, `black`, accents), `black/a60`, the veils `black/a00`, `black/a07`, `black/a13`, `black/a17` (aliased by `layer-transparent`, `layer-hover`, `layer-pressed`, `layer-active`), 15 steps of `scale/` |
| `semantic` | `VariableCollectionId:630:149` | `sand` (`630:1`) | 51: the roles, spacing, sizes, radii and widths of [Foundations](02-foundations.md) |

The effect style `focus-ring` does not show behind its node (`showShadowBehindNode` false): behind a transparent veil, its light line made the whole control look light. With this setting, Figma draws it only on a frame that clips its content: `open-focus` of `select-trigger` clips, as `focus` does (2026-11-22).

A colour bound to a variable takes its opacity from the variable: a fill bound to `layer-hover` set to 0 % still shows at 7 %. A transparent start needs its own variable (`layer-transparent`).

## Styles

| Kind | Styles |
| --- | --- |
| Text | `caption`, `body`, `body-strong`, `heading`, `title` (IBM Plex Sans), `code` (IBM Plex Mono) |
| Effect | `shadow-raised`, `shadow-overlay`, `focus-ring`, `focus-ring-inset` |

## How a page shows its components

Since 2026-11-22 (Product Owner: "un tableau d'états et de types [...] plutôt que plein de texte"), each component is shown as a table, with no text to read around it:

- one frame `table/<component>`, its title the name of the component;
- one column per state (`default`, `hover`, `pressed`, `focus`, `disabled`, then the states the component adds), its header the name of the state;
- one line per variant (`kind`, `size`, `checked`…), the name of each property at the head of its column of labels, its value on each line;
- the component set itself is the body of the table: its variants are laid out on the grid of the table, so the table is never out of step with the component;
- a component with no `state` shows its widest property as columns when it is narrow, else one column `preview`; a component with no variant, one cell `default`.

The tables of a page are grouped by family, one Figma section each. The frame `playground/…` of each page has its own section, `Playground`. A section holds all its tables, 48 from its edges, and the next section starts 160 below it: a table that grows makes its section grow and pushes the ones below.

A tooltip is centred on the icon it names, whatever the length of its text: its frame keeps a centre constraint on the axis of its arrow.

| Page | Sections, in order |
| --- | --- |
| Icons | `Icons`: one table per family (Parts and window, Metadata, Actions, Formatting, Signals and faceplate, Status), each icon with its name; every table six cells wide with a border on its four sides, three tables a row |
| Atoms | `Actions`, `Selection`, `Inputs`, `Support`, `Playground` |
| Molecules | `Forms`, `Lists and navigation`, `Table cells`, `Toolbars and window`, `Playground` |
| Organisms | `App frame`, `Lists`, `Data table`, `Editors`, `Pickers`, `Dialogs`, `Playground` |
| Templates | `Templates` |

No documentation frame in Figma: what a table cannot show is written in the Markdown sheet of the component ([Skill rules R9](skill-rules.md#r9--components-shown-as-tables-and-described-in-sheets)).

## Exports to the specification

How the files of the sheets are made (2026-11-22), to make them again after a change:

- **Icons**: each icon is cloned off the canvas, its lines turned into outlines (`outlineStroke`), joined (`union`, then `flatten`), filled black, exported as SVG, the black replaced by `currentColor`, then the clone removed. Figma keeps its lines.
- **Tables and screens**: the frame `table/<component>`, or the screen, exported as SVG, the texts turned into outlines, so that the files show the same without the fonts.
- A table or a screen changed in Figma is exported again in the same session.

## Components

Every component is prototyped (hover, press, click): try them from the frame `playground/…` of its page, a flow starting point.

| Page | Not in a sheet | Id |
| --- | --- | --- |
| Foundations | specimen board | `630:203` |
| Atoms | `playground/atoms` | `643:2164` |
| Atoms | `toggle`, not used by Metadata | `633:191` |
| Molecules | `playground/molecules` | `643:2262` |
| Molecules | `select`, not used by Metadata | `637:206` |
| Molecules | `quantity-cell`, `direction-cell`, deprecated: their description says what replaces them | `638:871`, `638:884` |
| Organisms | `playground/organisms` | `643:2487` |
| Templates | `example/editor`, an instance of the template with its slots filled | `657:155` |

## Ways of Figma to keep in mind

- **Hidden layers**: a script that looks for a hidden layer inside an instance sets `figma.skipInvisibleInstanceChildren = false` first: the plugin API hides them by default.
- **Drawing order**: `template/editor` and its `body` draw their first child on top (`itemReverseZIndex`), so that the rail and the top bar show their tooltips over the columns.
- **Clipping**: no frame or slot without a fill clips its content, in the components and on the screens; only the surfaces with a fill clip (a table, a panel, a screen, an overlay).
- **Strokes**: no component counts its stroke in its layout (`strokesIncludedInLayout` false, 2026-11-22, 183 variants of 12 components): a thicker line in a state never moves the content.
- **Scrolling**: a frame that scrolls puts its items in a frame `content` that carries the padding of the top and the bottom; on the frame that scrolls itself, Figma drops the padding of the end once scrolled (2026-11-22: `menu`, `menu-grouped`).
- **A click of its own**: an instance given a click of its own (open an overlay, go to a screen) loses the hover of its component unless it is set again with it: any new click is set next to the hover, never in its place.
- **A click that changes the component in place** is set on the component, never as an override on a screen: Figma keeps an overridden reaction, and the hover state of the moment, on the layer of the same name after the change, so the selected item kept its hover. On a screen, a switch leads to the screen of its other state instead (2026-11-22: the segmented controls of Units, Enums, Presets and Documentation).
- **Icons swapped**: an icon swapped into a `button` or an `icon-button` keeps only the colour overrides of the lines its default icon has (`icon/add` has two): every line of the new icon gets the colour of its variant by hand.
- **Nested sizes**: an instance nested in another one keeps the size of its main component: in a screen, a column gets its width only as the content of a slot. After a script fills a slot, Figma may draw a cell that fills its line at its old width: setting it to a fixed width, then back to fill, draws it right.
- **Structure changes**: after a change of structure in a component, an instance may draw the old positions until its main component's frame is touched again (a padding set then reset).
- **Overlays**: the plugin API cannot set the place of an overlay, and a centred overlay shows in the middle of the page: a list that opens is drawn as a transparent frame of the size of the screen, its content right under its button, closed by a click anywhere. The dimmed background behind the delete warning is set by hand.

## Screens of Metadata

The page Metadata holds one Figma section per screen of [Screens of Metadata](../screens/metadata.md), from top to bottom in the order of the type and of the rail: General (with the type tree), Documentation, Signals, Commands, Flags, Presets, Units, Enums, Designations, then the overlays (Delete warning, Add a link, Formatting). The frames and their ids: [Screens of Metadata](metadata/README.md).

The prototype has one starting point per screen: General, Documentation, Signals, Commands, Flags, Presets, Units, Enums, Designations. On every screen, the rail and the list of the parts lead to their screen, with their hover kept. From General: the modes of the documentation and of a preset lead to their screen; the two add icons of Links open their overlay; the button "Delete the preset" opens the warning; the delete button of General and of each own signal opens the warning, whose two buttons close it.

## Left to draw

- The screens of the other parts: Symbols, Pipes, Synoptic.
