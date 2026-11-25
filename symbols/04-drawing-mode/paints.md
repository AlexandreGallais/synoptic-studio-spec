# Paints

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › [Effects](effects-and-masks.md) › Paints

Status: draft. Linear and radial: kinds of fill decided, kept with their editing on the drawing (2026-11-25). The conic gradient, the pattern and the image: set aside, not in this version (Product Owner, 2026-11-25), kept as a record. Not validated.

What a fill or a border line can be painted with, beyond a plain colour. The kind is chosen in the tabs of the paint popup that the swatch of a [colour field](../../controls/colour-field.md#the-paint-popup) opens ([Fill and border](fill-and-border.md#what-a-fill-can-be)). A paint that is better set by hand has an editing mode, as an [effect](effects-and-masks.md#editing-modes).

## Linear gradient

|  |  |
| --- | --- |
| What it does | Colours along a line. |
| Feature | SVG `linearGradient`; `spreadMethod` pad, reflect or repeat beyond its ends. |
| Popup | Tab **Linear**: the **stops bar** above the colour area, one dot per stop; a click on the bar adds a stop, a stop dragged off the bar is removed; the stop selected takes the colour of the area and has its **position** in percent. **Repeat**: Pad, Reflect or Repeat. **Edit on the drawing**. |
| On the drawing | **Gradient editing**: the gradient line over the shape, a handle at each end and a dot per stop on it; dragging the ends sets the angle and the length, dragging a dot its position. The bar says "Gradient of Casing". |
| Status | Decided (kind of fill); kept with its editing (2026-11-25); the stops bar, Repeat and the editing measured in the POC (P8, P13). |

## Radial gradient

|  |  |
| --- | --- |
| What it does | Colours around a centre. |
| Feature | SVG `radialGradient`, with a focal point (`fx`, `fy`, `fr`) that can differ from the centre. |
| Popup | Tab **Radial**: the stops bar, **Repeat**, **Edit on the drawing**. |
| On the drawing | **Gradient editing**: a handle at the centre, a handle on the circle for the radius (two for an ellipse), and the **focal point**, a small handle that starts on the centre and can be dragged away from it. |
| Status | Decided (kind of fill); kept with its editing (2026-11-25); the focal point and the editing measured in the POC (P13). |

## Conic gradient

|  |  |
| --- | --- |
| What it does | Colours turning around a centre, like a colour wheel or a gauge. |
| Feature | CSS `conic-gradient()`. SVG has no conic paint: it would be drawn through a CSS `mask-image` over a flood, or not at all. |
| Popup | Tab **Conic**: the stops bar, **Start angle**, **Edit on the drawing**. |
| On the drawing | **Gradient editing**: a handle at the centre and a handle that turns the start angle. |
| Status | Set aside (2026-11-25): CSS, not SVG. |

## Pattern

|  |  |
| --- | --- |
| What it does | A small drawing, the **tile**, repeated to fill the shape: dots, lines, hatching, grid, or a tile drawn by the user. |
| Feature | SVG `pattern`. |
| Popup | Tab **Pattern**: **Tile**: Dots, Lines, Hatching, Grid or Custom; **Size** of the tile, **Angle**, **Colour** of the tile; **Edit the tile** for a custom one. |
| On the drawing | **Tile editing**: the tile is shown big in the middle of the drawing area, with its frame; the user draws in it with the shape tools; around it, the shape shows the tile repeated, live. The bar says "Pattern of Casing". |
| Status | Set aside (2026-11-25). |

## Image

|  |  |
| --- | --- |
| What it does | A picture fills the shape. |
| Feature | SVG `image` in a `pattern`. The picture is read through the server, as every file of the application. |
| Popup | Tab **Image**: **Choose an image**, **Fit**: Fill, Fit or Tile; **Opacity**. |
| On the drawing | Nothing. |
| Status | Set aside (2026-11-25). |

## Not possible

| Paint | Why |
| --- | --- |
| Mesh gradient | The SVG 2 draft `meshgradient` was removed; no engine draws it. |
| Hatch | The SVG 2 draft `hatch` was removed; the pattern does it. |

## Where it is used

| Screen | Element |
| --- | --- |
| [Figma](../../design-system/04-figma-file.md#effects-screens) | The id of each screen |
| [SY-04](../../screens/symbols.md#effects-one-by-one) | SY-04.65 and SY-04.66 (linear), SY-04.67 and SY-04.68 (radial), SY-04.69 and SY-04.70 (conic), SY-04.71 and SY-04.72 (pattern), SY-04.73 (image) |
| [Colour field](../../controls/colour-field.md) | The tabs of the paint popup |
