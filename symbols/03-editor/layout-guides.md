# Layout guides

> [Home](../../README.md) › [Symbols](../README.md) › [Editor](README.md) › Layout guides

Status: draft. Asked by the Product Owner on 2026-11-25 ("comme sur Figma... je te laisse gérer"); the form is the assistant's proposal, reviewed by the Product Owner the same day (the eye kept, the placement from the list, the grid in width × height linked by a chain). Not validated.

Lines and grids drawn over the view of a symbol, to place and align shapes. They belong to the view, never to a layer: nothing of them goes into the SVG of the symbol.

## Rules

- **Where**: a **Guides** button in a small floating bar **under the modes menu**, at the top left of the drawing area; it opens the **guides popup** (Product Owner, 2026-11-25: "un menu en dessous des modes").
- **Three kinds**, added with three buttons at the top of the popup:

| Kind | What it draws | Its settings, on its line |
| --- | --- | --- |
| Column | A vertical line. | X, in pixels from the left of the symbol. |
| Row | A horizontal line. | Y, in pixels from the top of the symbol. |
| Grid | Cells over the whole symbol. | The width and the height of a cell, in pixels, linked by a chain: linked by default, square cells (8 × 8); unlinked, cells of any size (8 × 2) (Product Owner, 2026-11-25). |

- **The list**: one line per guide, in the popup: its kind, its value, a **place** button, a **−** that removes it. Removing or adding a guide is one click (Product Owner, 2026-11-25: "simple à enlever, à ajouter").
- **Placing by hand**: the place button of a column or a row starts the **placement**: the guide follows the mouse over the drawing and its value follows; a click puts it there and ends the placement; Escape ends it and puts the guide back. A guide is never dragged on the drawing itself: it is moved from its line (Product Owner, 2026-11-25: "pas en cliquant dessus sur la vue, mais un truc dans la liste").
- **Show or hide all**: an eye on the Guides button hides every guide without removing them; Ctrl+' does the same (visible equivalent: the eye). Kept by the Product Owner (2026-11-25).
- **Snapping**: while a shape, a point or a handle is dragged, it snaps to the guides near it, as to the other shapes (see [Editor](README.md#geometry-of-a-symbol)).
- **Kept with the symbol**: the guides are saved in the file of the symbol, in the data of the editor, outside the drawing; they are the same in every mode.
- **Colour**: one colour for every guide, from the design system, never a colour of the drawing.

```mermaid
block-beta
    columns 3
    modes["Modes menu"]:3
    guides["Guides button and its eye"] space:2
    popup["Popup: + Column, + Row, + Grid, then one line per guide with its value, its place button and its −"]:3
```

```mermaid
stateDiagram-v2
    [*] --> Placed
    Placed --> Placing: place button of its line
    Placing --> Placed: click on the drawing, the guide stays there
    Placing --> Placed: Escape, the guide goes back
    Placing: The guide follows the mouse
```

## Example

| Line of the popup | On the drawing |
| --- | --- |
| Column · 100 | A vertical line at 100 px, the middle of a symbol 200 wide. |
| Row · 36 | A horizontal line at 36 px, the top of the casing. |
| Grid · 8 × 8 | Squares of 8 px over the whole symbol. |
| Grid · 8 × 2 | Cells 8 px wide and 2 px high, the chain unlinked. |

## Where it is used

| Screen | Control |
| --- | --- |
| [SY-03](../../screens/symbols.md#sy-03--symbol-editor-what-every-mode-shares) | Guides button and popup (SY-03.17) |

## Open questions

- A grid with columns and gutters (as Figma's layout grids)?
- Guides placed in percent of the symbol, so that they follow a resize of its frame?
