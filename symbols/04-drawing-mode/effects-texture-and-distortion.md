# Effects: texture and distortion

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › [Effects](effects-and-masks.md) › Texture and distortion

Status: draft. Proposals of the assistant for the POC (2026-11-25). The research report thought them too costly; the POC measures them (2026-11-25). Not validated.

Effects that change the pixels of a shape. Each effect follows the [section "Effects"](effects-and-masks.md#the-section-effects).

## Thicken, thin

|  |  |
| --- | --- |
| What it does | Grows or shrinks the shape by a few pixels, text included. Thickening a copy under the shape makes an outline around anything, a text for instance. |
| Feature | SVG `feMorphology`, operator dilate or erode. |
| Line | "Thicken" or "Thin", the operation chosen, with a settings button. |
| Popup | **Operation**: Thicken or Thin. **Radius**, in pixels. |
| On the drawing | Nothing. |
| Status | POC. |

## Noise, texture

|  |  |
| --- | --- |
| What it does | A noise over the shape: paper, metal, concrete, grain. |
| Feature | SVG `feTurbulence` (type fractal noise or turbulence), then `feComposite` (in) on the shape and `feBlend`. |
| Line | "Noise", with a settings button. |
| Popup | **Kind**: Fractal noise or Turbulence. **Scale** (the size of the grain), **Detail** (the number of octaves), **Seed** (another draw of the same noise), **Opacity**, **Colour**: Mono or Colour. |
| On the drawing | Nothing. |
| Status | POC. |

## Distortion

|  |  |
| --- | --- |
| What it does | Moves the pixels of the shape: waves, heat, glass. Moving the noise over time (animation mode) makes the shape ripple. |
| Feature | SVG `feDisplacementMap`, fed by an `feTurbulence`. |
| Line | "Distortion", with a settings button. |
| Popup | **Strength** (how far the pixels move), **Scale**, **Detail**, **Seed** of the noise that moves them. |
| On the drawing | Nothing. |
| Status | POC. |

## Where it is used

| Screen | Element |
| --- | --- |
| [Figma](../../design-system/04-figma-file.md#effects-screens) | The id of each screen |
| [SY-04](../../screens/symbols.md#effects-one-by-one) | SY-04.60 (thicken, thin), SY-04.61 (noise), SY-04.62 (distortion) |
