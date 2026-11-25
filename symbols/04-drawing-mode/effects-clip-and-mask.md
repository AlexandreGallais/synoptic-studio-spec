# Effects: clip, mask, fade

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › [Effects](effects-and-masks.md) › Clip, mask, fade

Status: draft. The clip: asked and kept by the Product Owner on 2026-11-25, then made a mode of the modes menu the same day. The mask and the fade: set aside, not in this version (Product Owner, 2026-11-25), kept as a record. Not validated.

What hides part of a shape. The mask and the fade would follow the [section "Effects"](effects-and-masks.md#the-section-effects) and its [editing modes](effects-and-masks.md#editing-modes).

## Clip

|  |  |
| --- | --- |
| What it does | Only the part of the shape inside the **clip shapes** is shown; whatever goes beyond is hidden. Example: a liquid level that rises inside a tank, cut by the outline of the tank; it allows many animations (Product Owner, 2026-11-25). |
| Where | Since 2026-11-25, the [Clip mode](clip-mode.md), in the modes menu: no longer a line of a section "Effects". The screens SY-04.13 and SY-04.39 of the effect stay as a record. |
| Status | Decided (2026-11-25); its limits measured by P7. |

## Mask

|  |  |
| --- | --- |
| What it does | The same as the clip, with a soft edge: the mask shapes give the transparency of the shape. |
| Feature | SVG `mask`, with `mask-type` alpha (the opacity of the mask shapes counts) or luminance (their brightness counts: white shown, black hidden). It costs more than a clip (an image computed per pixel). |
| Line | "Mask · 1 shape", with a settings button. |
| Popup | **Mode**: Alpha or Luminance, two tabs. **Shapes**: their number and an **Edit on the drawing** button. A hard edge is always a clip: the popup says so. |
| On the drawing | **Mask editing**, the same as the clip editing; the bar says "Mask of Casing". The mask shapes have fills (a gradient from opaque to transparent makes a soft edge) and no border. |
| Status | Set aside (2026-11-25). |

## Fade

|  |  |
| --- | --- |
| What it does | The shape fades out along a line or from a centre, with no shape to draw: the common use of a mask, made quicker. |
| Feature | CSS `mask-image` with a linear or radial gradient, or an SVG `mask` holding one rectangle filled with that gradient. Which one: the POC. |
| Line | "Fade", with a settings button. |
| Popup | **Kind**: Linear or Radial, two tabs. **Angle** (linear). **From** and **To**: where the shape starts to fade and where it is gone, in percent of its size. **Edit on the drawing**. |
| On the drawing | **Fade editing**: a line across the shape with two handles, From (opaque) and To (transparent); dragging them changes the angle and the two percents. The bar says "Fade of Casing". |
| Status | Set aside (2026-11-25). |

## Where it is used

| Screen | Element |
| --- | --- |
| [Figma](../../design-system/04-figma-file.md#effects-screens) | The id of each screen |
| [SY-04](../../screens/symbols.md#effects-one-by-one) | SY-04.13 and SY-04.39 (clip), SY-04.40 and SY-04.41 (mask), SY-04.42 and SY-04.43 (fade) |
