# Documentary research of the symbols part: brief

> [Home](../README.md) › [Symbols](README.md) › Research brief

Status: draft. This file gathers everything the symbols part leaves to a documentary research. It will be sent when the Product Owner says so, once the whole part is discussed. No task is created before that.

Which questions go in the research: for now only questions 1 to 4 (the drawing tools discussed with the Product Owner). Question 5 and the questions of the pages not discussed yet are not sent.

## Questions

### 1. Which SVG effects keep the performance

- Context: effects and masks come only from native SVG (filters, `clipPath`, `mask`). See [Effects and masks](04-drawing-mode/effects-and-masks.md).
- Question: among drop shadow, inner shadow, blur of the shape, colour changes, cut and mask by a shape, gradients and dashes, which ones can be offered without lag, including when the shape or what is below is animated? Which ones must be refused?
- For each effect and each setting (blur radius, size of the filter area, number of filtered elements): the cost, what makes it vary (surface, radius, animated content, caching of the result), the differences between browsers and engines (Chromium, Firefox, WebKit, the window of a desktop application), and a recommendation labelled "Avis :": offer, offer with a limit, or refuse.
- Cheaper alternatives for the same look (pre-rendered shadow, gradient instead of blur, cut instead of mask).
- A plan of small POC to measure what the sources do not settle: what to measure, with which shapes and animations, and the decision threshold against 8.3 ms per frame (120 Hz). The measures themselves are done in the `synoptic-studio-poc` repository.

### 2. How a polygon is placed in its box

- Context: see [Polygon tool](04-drawing-mode/polygon.md). The Product Owner wants two modes (filled, equilateral) and does not understand how Figma places its polygon: a triangle does not fill the box, and Figma is neither equilateral nor filling.
- Question: why does Figma do it that way, and is there a logic behind it? How do Figma and other drawing software (Inkscape, Illustrator, Sketch, Affinity, Penpot) place a regular polygon in the box that is dragged? Which variants exist (fill the box, equal sides, corners touching the box)?
- The exact geometry of each variant (how the box and the vertices match, by number of sides), with the source, and a recommendation labelled "Avis :" on a third mode "like Figma".

### 3. Handle mirroring: names and list

- Context: see [Points and handles](05-point-editing-mode/points-and-handles.md). The Product Owner wants: no mirroring, mirror angle, mirror angle and length.
- Question: which names and which modes do drawing software use for the mirroring of the two handles of a point? Is the list complete?

### 4. Modifier keys (short, only if the sources allow it)

- Context: the keys are not defined for now. Every key must have a visible equivalent in the interface.
- Question: what are the conventions of drawing software for the modifier keys of: a square or a circle while drawing (Shift or Ctrl), a selection rectangle that touches or fully encloses (Shift or Alt), and a pen that chains straight segments (which key, one segment or a switch)? See [Select](03-editor/select.md), [Rectangle](04-drawing-mode/rectangle.md) and [Pen](04-drawing-mode/pen.md).

### 5. Fonts: licences, weights, italic, baseline fit

- Context: see [Text tool](04-drawing-mode/text.md). Only fonts bundled with the software are offered, chosen among fonts free to be put in SVG files, with an option to embed them in the exported SVG.
- Question: which open fonts can be bundled and embedded in an SVG under their licence? How can the weights and the italic that a font really offers be read? How do software and browsers compute a text box that fits the baseline (ascent, descent, "trim") rather than the glyphs? Can SVG text carry a native stroke in every engine?

## What stays out of the research

The code, the performance measures (they come from the POC), the geometric engine and the intersection calculations (another research), the SaaS, phones and tablets, and the final choice of effects (the Product Owner decides, on the report and the POC).

## Files to read first

- `symbols/04-drawing-mode/effects-and-masks.md`, `fill-and-border.md`, `polygon.md`, `pen.md`
- `symbols/03-editor/select.md`
- `symbols/05-point-editing-mode/points-and-handles.md`
- `symbols/10-open-questions.md`
