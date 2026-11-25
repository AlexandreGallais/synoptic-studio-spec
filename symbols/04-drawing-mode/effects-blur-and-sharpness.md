# Effects: blur and sharpness

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › [Effects](effects-and-masks.md) › Blur and sharpness

Status: draft. Proposals of the assistant for the POC (2026-11-25). Not validated.

How sharp a shape looks. Each effect follows the [section "Effects"](effects-and-masks.md#the-section-effects).

## Blur

|  |  |
| --- | --- |
| What it does | Blurs the shape itself, the same in both directions, or in one direction only (a motion blur). |
| Feature | SVG `feGaussianBlur`, one radius per axis; CSS `blur()` has one radius only. |
| Line | "Blur", with a settings button. |
| Popup | **Radius X** and **Radius Y**, linked by a chain as W and H: linked, one radius; unlinked, a blur in one direction. |
| On the drawing | Nothing. |
| Status | POC (P2, stricter than the drop shadow). |

## Sharpen, edges, emboss

|  |  |
| --- | --- |
| What it does | Sharpens the shape, keeps only its edges, or embosses it. |
| Feature | SVG `feConvolveMatrix`: a 3 × 3 matrix applied to the pixels; the popup chooses the matrix. |
| Line | "Sharpen", with a settings button; the line takes the name of the kind chosen. |
| Popup | **Kind**: Sharpen, Edges or Emboss. **Strength**, a slider. |
| On the drawing | Nothing. |
| Status | POC. |

## Where it is used

| Screen | Element |
| --- | --- |
| [Figma](../../design-system/04-figma-file.md#effects-screens) | The id of each screen |
| [SY-04](../../screens/symbols.md#effects-one-by-one) | SY-04.55 (blur), SY-04.56 (sharpen, edges, emboss) |
