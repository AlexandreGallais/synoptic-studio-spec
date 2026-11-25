# Effects: opacity and blend

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › [Effects](effects-and-masks.md) › Opacity and blend

Status: draft. Proposals of the assistant for the POC (2026-11-25). Not validated.

How a shape lets through what is under it. Each effect follows the [section "Effects"](effects-and-masks.md#the-section-effects).

## Opacity

|  |  |
| --- | --- |
| What it does | The whole shape, fills, border and effects together, more or less transparent. The opacity of a fill only is in its [colour field](../../controls/colour-field.md). |
| Feature | SVG `opacity`. |
| Line | "Opacity", then its value on the line itself, a percent field (60 %). No popup. |
| On the drawing | Nothing. |
| Status | POC (expected cheap). |

## Blend mode

|  |  |
| --- | --- |
| What it does | Mixes the colours of the shape with what is under it in the symbol. |
| Feature | CSS `mix-blend-mode`. On a [group](group.md), CSS `isolation: isolate` keeps the mix inside the group. |
| Line | "Blend", then a select on the line itself, which opens the list of the modes. No popup. |
| The list | Grouped as in drawing software: Normal · Darken, Multiply, Colour burn · Lighten, Screen, Colour dodge, Plus lighter · Overlay, Soft light, Hard light · Difference, Exclusion · Hue, Saturation, Colour, Luminosity. |
| On the drawing | Nothing; the drawing shows the mix while the pointer moves over the list. |
| Status | POC. |

## Background blur

|  |  |
| --- | --- |
| What it does | Blurs what is behind the shape, as frosted glass. |
| Feature | CSS `backdrop-filter`. Its drawing on an SVG shape differs between engines: to check in the POC. If no engine draws it, it is not possible. |
| Line | "Background blur", with a settings button. |
| Popup | **Radius**. |
| On the drawing | Nothing. |
| Status | POC, support to check. |

## Where it is used

| Screen | Element |
| --- | --- |
| [Figma](../../design-system/04-figma-file.md#effects-screens) | The id of each screen |
| [SY-04](../../screens/symbols.md#effects-one-by-one) | SY-04.44 (opacity), SY-04.45 (blend mode), SY-04.46 (background blur) |
