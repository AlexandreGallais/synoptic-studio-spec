# Effects: shadows and light

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › [Effects](effects-and-masks.md) › Shadows and light

Status: draft. Proposals of the assistant for the POC (2026-11-25). Not validated.

Shadows, halos and light on a shape. Each effect follows the [section "Effects"](effects-and-masks.md#the-section-effects) and its [editing modes](effects-and-masks.md#editing-modes). Every colour is a [colour field](../../controls/colour-field.md), colour and opacity.

## Drop shadow

|  |  |
| --- | --- |
| What it does | A blurred, offset copy of the shape behind it. On a text, it is the text shadow. |
| Feature | SVG `feDropShadow`; CSS `drop-shadow()`. A spread (a bigger shadow) needs `feMorphology` before it: for the POC. |
| Line | "Drop shadow", with a settings button. |
| Popup | **X** and **Y** (offset), **Blur**, **Spread**, **Colour**. **Edit on the drawing**. |
| On the drawing | **Shadow editing**: a handle in the middle of the shadow, linked to the middle of the shape by a dashed line, drags the offset; a ring around the shadow drags the blur. The bar says "Shadow of Casing". |
| Status | POC (P2). |

## Outer glow

|  |  |
| --- | --- |
| What it does | A coloured halo around the shape, without offset. |
| Feature | `feGaussianBlur`, `feFlood`, `feComposite`, `feMerge`; or a drop shadow at offset 0. |
| Line | "Outer glow", with a settings button. |
| Popup | **Size**, **Colour**. |
| On the drawing | Nothing. |
| Status | POC. |

## Inner shadow

|  |  |
| --- | --- |
| What it does | A shadow inside the edge, as if the shape were hollow. |
| Feature | `feOffset`, `feGaussianBlur`, `feComposite`. |
| Line | "Inner shadow", with a settings button. |
| Popup | **X** and **Y**, **Blur**, **Colour**. **Edit on the drawing**. |
| On the drawing | **Inner shadow editing**: the same handles as the drop shadow, inside the shape. The bar says "Inner shadow of Casing". |
| Status | POC (P5). |

## Inner glow

|  |  |
| --- | --- |
| What it does | A coloured halo inside the edge. |
| Feature | `feGaussianBlur`, `feFlood`, `feComposite`. |
| Line | "Inner glow", with a settings button. |
| Popup | **Size**, **Colour**. |
| On the drawing | Nothing. |
| Status | POC. |

## Lighting

|  |  |
| --- | --- |
| What it does | A light on a relief made from the shape: a bevel, a relief, a shine. |
| Feature | `feDiffuseLighting` (relief) and `feSpecularLighting` (shine), lit by `feDistantLight` (far, like the sun), `fePointLight` (a bulb) or `feSpotLight` (a cone). |
| Line | "Lighting", with a settings button. |
| Popup | **Kind**: Relief or Shine. **Light**: Far, Point or Spot. **Azimuth** and **Elevation** (far light), or the position of the light (point, spot). **Depth** of the relief. **Shine** (shine only). **Colour** of the light. **Edit on the drawing**. |
| On the drawing | **Light editing**: the light is a handle on the drawing, a bulb for a point, a bulb with its cone for a spot, an arrow for a far light; dragging it lights the shape again. The bar says "Light of Casing". |
| Status | POC. |

## Where it is used

| Screen | Element |
| --- | --- |
| [Figma](../../design-system/04-figma-file.md#effects-screens) | The id of each screen |
| [SY-04](../../screens/symbols.md#effects-one-by-one) | SY-04.47 and SY-04.48 (drop shadow), SY-04.49 (outer glow), SY-04.50 and SY-04.51 (inner shadow), SY-04.52 (inner glow), SY-04.53 and SY-04.54 (lighting) |
