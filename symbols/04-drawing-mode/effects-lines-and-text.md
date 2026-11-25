# Effects: lines and text

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › [Effects](effects-and-masks.md) › Lines and text

Status: draft. The border that keeps its width: kept by the Product Owner (2026-11-25). The arrow heads, the crisp edges and the text along a path: set aside, not in this version (Product Owner, 2026-11-25), kept as a record. Not validated.

What SVG offers for lines, borders and texts, beyond the [border](fill-and-border.md) and the [text](text.md).

## Arrow heads

|  |  |
| --- | --- |
| What it does | A shape at the start, at the corners or at the end of a line: an arrow, a dot, a bar. |
| Feature | SVG `marker`, with `marker-start`, `marker-mid` and `marker-end`; the marker follows the direction of the line and the size of its border. |
| Line | In the section "Border" of a path, a line **Ends**: a select **Start** and a select **End**, each opening the list of the heads. |
| The list | None, Arrow, Open arrow, Circle, Square, Diamond, Bar, then **Custom** and the custom heads of the Symbol Lib. A **Size**, in times the width of the border, under the list. |
| On the drawing | **Head editing**, for a custom head: the head is shown big in the middle of the drawing area, with the end of the line as a guide, and drawn with the shape tools. The bar says "End of Flow arrow". |
| Status | Set aside (2026-11-25). |

## Border that keeps its width

|  |  |
| --- | --- |
| What it does | The border keeps its width on screen when the symbol is scaled in a synoptic: a pump drawn twice as big keeps borders of 2 px, so that symbols can be rescaled without growing thick (Product Owner, 2026-11-25). |
| Feature | Computed, as the border itself (outside, middle, inside, dashes): the outline of the border is computed again at the scale of the symbol in the synoptic (Product Owner, 2026-11-25: "ça sera calculé"). SVG `vector-effect: non-scaling-stroke` applies to a native stroke only, so it is not used. |
| Line | In the section "Border", a switch **Keep the width when scaled**, under the size and position. |
| On the drawing | Nothing in the editor; the effect shows in a synoptic. |
| Status | Kept (2026-11-25); its cost measured in the POC (P13). |

## Crisp edges

|  |  |
| --- | --- |
| What it does | Draws the edges on whole pixels, without smoothing: sharp horizontal and vertical lines, stairs on curves. |
| Feature | SVG `shape-rendering`: crispEdges; geometricPrecision is the smooth default. |
| Line | "Crisp edges" in the section "Effects", with no button: on or off by its eye. |
| On the drawing | Nothing more than the effect. |
| Status | Set aside (2026-11-25). |

## Text along a path

|  |  |
| --- | --- |
| What it does | The letters of a text follow a curve: a name around a tank. |
| Feature | SVG `textPath`. |
| Line | In the panel of a [text](text.md), a line **Along a path**: a select of the shapes of the symbol, and an **Edit** button. |
| Popup | **Path**: the shape followed. **Start**, in percent of its length. **Side**: Outside or Inside. |
| On the drawing | **Path editing**: the path followed is shown with its points, a handle marks where the text starts; dragging it moves the text along the path. The bar says "Path of Tag". |
| Status | Set aside (2026-11-25). |

## Where it is used

| Screen | Element |
| --- | --- |
| [Figma](../../design-system/04-figma-file.md#effects-screens) | The id of each screen |
| [SY-04](../../screens/symbols.md#effects-one-by-one) | SY-04.74 and SY-04.75 (arrow heads), SY-04.76 (border that keeps its width), SY-04.77 (crisp edges), SY-04.78 and SY-04.79 (text along a path) |
