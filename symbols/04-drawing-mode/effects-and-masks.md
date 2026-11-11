# Effects and masks of a shape

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Effects and masks

Status: draft, from the Product Owner's description of 2026-11-11 and the research report of 2026-11-11. Not validated.

Effects and masks are set from the right-hand panel, like the [fill and border](fill-and-border.md). The Product Owner does not know SVG filters well: the editor offers them in a menu, and the user writes nothing.

## Rules

- **Only what SVG does natively.** Every effect and every mask comes from the SVG itself: its filters, its `clipPath` and its `mask`. Nothing is simulated with copies or tricks. An effect that SVG does not do natively is not offered. This is why there is no "blur of what is behind the shape".
- **Effects menu**: each shape has an "Effects" menu in the right-hand panel, to add, edit and remove effects.
- **Mask**: a shape can be shown only through another shape. Example: a big circle, of which only the part inside a triangle is shown. The shape that cuts is chosen by the user.
- **Performance comes first**: an effect is offered only if it keeps the performance objective (see the project criteria on gestures and 120 Hz). The goal: never offer something that lags.
- If an effect or a setting makes the performance fall too much, it is not offered. The answer is "not possible".

## What the research found

Source: the research report (`research/t1-…/rapport.md`, in the project, not committed). It measured nothing: everything below is read from sources, and the performance POC will settle it. The "Opinion" column is the report's provisional opinion, not a decision.

### Why the engine matters

| Window | Engine | SVG filters on the graphics card |
| --- | --- | --- |
| Chrome, Edge, Electron (Windows, macOS, Linux), Tauri on Windows | Chromium | Yes |
| Firefox 132 or later | Gecko | Yes, for 9 primitives (blend, colour matrix, component transfer, composite, drop shadow, flood, Gaussian blur, merge, offset) |
| Safari, Tauri on macOS (WKWebView) and Linux (WebKitGTK) | WebKit | No (open WebKit bug since 2023) |

- WebKit renders at 60 frames per second by default. The embedded view (WKWebView) has no public way to ask for 120. With a WebKit window, the 120 Hz objective cannot be reached by default, with or without effects.
- The choice of the desktop window (embedded Chromium or the system view) weighs more than any effect setting. It is the Product Owner's, not made yet.

### What makes the cost vary

- The cost follows the number of pixels of the filter area, which grows with the size of the shape, the zoom and the screen density. A big blur radius costs mainly because it forces a bigger filter area.
- Moving a filtered shape can reuse the image already computed. Resizing it, editing a point or changing its colour recomputes the filter at every frame.
- The default colour space of SVG filters (linear RGB) costs more than sRGB.
- A cut by one simple path takes the fast path; a text, a nested cut or too many shapes make the engine switch to a mask.
- No source gives the cost of a gradient, nor of the number of filtered shapes.

### Effect by effect

| Effect | SVG feature | Opinion of the report | Limit to measure |
| --- | --- | --- | --- |
| Cut by a shape | `clipPath` | Offer. Confidence: medium. | The shape that cuts is one simple shape, no text, no nested cut. |
| Gradients | Linear or radial gradient | Offer, subject to a short POC. Confidence: low. | Number of colour stops. |
| Dashes | See [fill and border](fill-and-border.md) | Offer with a limit. Confidence: low. | Maximum number of dashes per shape. |
| Colour changes | Filter | Offer with a limit, or without a filter (recomputed colours). Confidence: medium. | Filtered area and number of shapes. |
| Drop shadow | Filter | Offer with a limit. Confidence: medium. | Maximum radius and maximum filter area, in screen pixels. |
| Blur of the shape | Filter | Offer with a limit stricter than the drop shadow. Confidence: medium. | Radius, filter area. |
| Mask by a shape | `mask` | Offer with a limit. Replace by a cut when the edge is hard. Confidence: low. | Filtered area. |
| Inner shadow | Chain of filter primitives | Offer with a limit if the POC holds, else refuse. Confidence: low. | Radius, area. |
| Noise, lighting, convolution, displacement, morphology | Other filter primitives | Refuse (not in the project's list anyway). | — |

### Cheaper alternatives for the same look

- Filters declared in sRGB instead of linear RGB: a coloured blur changes a little.
- A cut instead of a mask when the edge is hard: no progressive transparency.
- Recomputed fill colours instead of a colour filter: the effect is then no longer a filter, and this must be written in the specs.
- CSS filter functions on the SVG element: support to check engine by engine, and no inner shadow.
- A tight filter area around the shape: too tight, it cuts the effect.
- Moving by transform during the gesture: only for moving, not for resizing.
- A radial gradient that imitates a shadow is against the rule above ("nothing simulated"): not retained.

### POC plan proposed (to be done in `synoptic-studio-poc`)

| POC | Question |
| --- | --- |
| P0 | Does each engine deliver 120 frames per second with no effect? (also window: desktop or browser) |
| P1 | Base cost of the gestures: 1, 50, 200 shapes without effect; move, resize, edit a point. |
| P2 | How far do blur and drop shadow hold? Radius 1 to 32, shape 50 to 800 px, zoom 100 % and 400 %, single and double density, linear RGB or sRGB. |
| P3 | How many filtered shapes? 1, 10, 50, 200, all animated. |
| P4 | Cost of an animation near an effect (below, above, the filtered shape itself animated). |
| P5 | Does the inner shadow hold? |
| P6 | Colour filter or recomputed colours? |
| P7 | Cut or mask? Simple cut, multi-shape cut, hard mask, progressive mask. |
| P8 | How many dashes, how many gradient stops? 10 to 10 000 dashes, native stroke or computed dashes, 2, 8, 32 stops. |

- Engines to cover: Chromium, Firefox 132 or later, WebKit (Safari, then the desktop window if it is WebKit).
- What is measured: the work time of each frame during the gesture, in milliseconds, read in the browser profiler (the time between two frames is not enough: a 60 Hz engine lengthens it without being slow). P0 and P2 first.
- Decision threshold proposed: 95 % of the frames at 8.3 ms or less and none above 16.7 ms at the most demanding setting offered, in each engine aimed at: offer. The rule holds up to a setting, then breaks: offer with that limit. It breaks at the smallest useful setting: refuse. The maximum stays the one the Product Owner sets.

## To decide by the Product Owner

The report's questions that the specs cannot answer alone:

1. Which desktop window: embedded Chromium or the system view? It fixes the engine to measure first. **Postponed by the Product Owner (2026-11-11), not decided.** He wants the lightest and simplest to maintain for an open source application, so possibly Tauri, possibly Electron. Chromium is probably the best for effects and 120 Hz; he wonders whether Chromium can be used without Electron. To think about later.
2. Which browsers must the front hold at 8.3 ms when plugged into a browser: Chromium only, or Firefox and Safari too?
3. Is an effect suspended during the gesture and restored at release an acceptable concession (if the drop shadow does not hold in WebKit)?
4. Can a colour filter be replaced by recomputed colours, or must it stay a filter in the exported SVG?
5. Which effects go in the specs now: all of them and measure afterwards, two lots (a safe lot, a lot "subject to the POC"), or only the safe lot? The report advises two lots.
