# Effects: opacity and blend

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › [Effects](effects-and-masks.md) › Opacity and blend

Status: draft. The opacity: kept by the Product Owner (2026-11-25). The blend mode and the background blur: set aside, not in this version (Product Owner, 2026-11-25), kept as a record. Not validated.

How a shape lets through what is under it. The opacity is a line of the right-hand panel; the effects set aside would follow the [section "Effects"](effects-and-masks.md#the-section-effects).

## Opacity

|  |  |
| --- | --- |
| What it does | The whole object, fills, border and effects together, more or less transparent (Product Owner, 2026-11-25: "l'opacité entière de l'objet"). The opacity of a fill or of a line of the border only is in its [colour field](../../controls/colour-field.md). |
| Feature | SVG `opacity`. |
| Line | A line of the right-hand panel, after the border: "Opacity", then its value on the line itself, a percent field (100 % by default). No popup, no section "Effects" (2026-11-25; its place: assistant's proposal). |
| On the drawing | Nothing. |
| Status | Kept (2026-11-25); its cost measured in the POC (P13), expected cheap. |

## Blend mode

|  |  |
| --- | --- |
| What it does | Mixes the colours of the shape with what is under it in the symbol. |
| Feature | CSS `mix-blend-mode`. On a [group](group.md), CSS `isolation: isolate` keeps the mix inside the group. |
| Line | "Blend", then a select on the line itself, which opens the list of the modes. No popup. |
| The list | Grouped as in drawing software: Normal · Darken, Multiply, Colour burn · Lighten, Screen, Colour dodge, Plus lighter · Overlay, Soft light, Hard light · Difference, Exclusion · Hue, Saturation, Colour, Luminosity. |
| On the drawing | Nothing; the drawing shows the mix while the pointer moves over the list. |
| Status | Set aside (2026-11-25). |

## Background blur

|  |  |
| --- | --- |
| What it does | Blurs what is behind the shape, as frosted glass. |
| Feature | CSS `backdrop-filter`. Its drawing on an SVG shape differs between engines: to check in the POC. If no engine draws it, it is not possible. |
| Line | "Background blur", with a settings button. |
| Popup | **Radius**. |
| On the drawing | Nothing. |
| Status | Set aside (2026-11-25). |

## Where it is used

| Screen | Element |
| --- | --- |
| [Figma](../../design-system/04-figma-file.md#effects-screens) | The id of each screen |
| [SY-04](../../screens/symbols.md#effects-one-by-one) | SY-04.44 (opacity), SY-04.45 (blend mode), SY-04.46 (background blur) |
