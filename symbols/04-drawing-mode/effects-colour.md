# Effects: colour

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › [Effects](effects-and-masks.md) › Colour

Status: draft. Proposals of the assistant for the POC (2026-11-25). Not validated.

Effects that change the colours of a shape, fills, border and effects above them together. Each effect follows the [section "Effects"](effects-and-masks.md#the-section-effects). Whether a colour effect stays a filter or becomes recomputed colours in the exported SVG: P6 and a question of [Effects](effects-and-masks.md#to-decide-by-the-product-owner).

## Colour adjustments

|  |  |
| --- | --- |
| What it does | Brightness, contrast, saturation, hue, greyscale, sepia, invert, on one line. Example: a symbol greyed when its equipment is out of service. |
| Feature | SVG `feColorMatrix` (saturate, hue turn, matrix) and `feComponentTransfer` (linear, gamma); CSS `brightness()`, `contrast()`, `saturate()`, `grayscale()`, `sepia()`, `hue-rotate()`, `invert()`. |
| Line | "Colour adjustments", with a settings button. |
| Popup | One slider per setting, each with its value: **Brightness**, **Contrast**, **Saturation** (100 % by default), **Hue** (0° by default), **Greyscale**, **Sepia**, **Invert** (0 % by default). A **Reset** at the bottom. |
| On the drawing | Nothing. |
| Status | POC (P6). |

## Colour overlay

|  |  |
| --- | --- |
| What it does | Paints one colour over the shape, keeping its outline and its transparency. |
| Feature | `feFlood`, then `feComposite` (in) on the shape, then `feBlend`. |
| Line | "Colour overlay", with a settings button. |
| Popup | **Colour**, **Blend** (the modes of the [blend mode](effects-opacity-and-blend.md#blend-mode)). |
| On the drawing | Nothing. |
| Status | POC. |

## Colour map

|  |  |
| --- | --- |
| What it does | Remaps the colours: **duotone** (dark tones to one colour, light ones to another), **posterize** (a few levels per channel), **threshold** (black or white only). |
| Feature | SVG `feComponentTransfer`, type table or discrete, after an `feColorMatrix` to grey. |
| Line | "Colour map", with a settings button. |
| Popup | **Kind**: Duotone, Posterize or Threshold. Duotone: **Dark** and **Light** colours. Posterize: **Levels**. Threshold: **Level**. |
| On the drawing | Nothing. |
| Status | POC. |

## Where it is used

| Screen | Element |
| --- | --- |
| [Figma](../../design-system/04-figma-file.md#effects-screens) | The id of each screen |
| [SY-04](../../screens/symbols.md#effects-one-by-one) | SY-04.57 (colour adjustments), SY-04.58 (colour overlay), SY-04.59 (colour map) |
