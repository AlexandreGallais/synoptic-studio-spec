# Annotations

> [Home](../README.md) › [Synoptics](README.md) › Annotations · Previous: [Pipes](05-pipes.md) · Next: [Navigation links](07-navigation-links.md)

Status: extrapolated by the assistant on 2026-11-20. Not validated.

An **annotation** is what is drawn in a synoptic and is not a symbol: a title, the outline of a building, a legend. It has no type, no signal, no identity.

## Rules

- Annotations are drawn in the **Annotate** mode, with the drawing tools of the symbol editor: rectangle, ellipse, polygon, pen, text, with the same fill and border panel (see [Drawing mode](../symbols/04-drawing-mode/README.md)). Proposed: one way to draw in the whole application.
- They take their place in the **Objects** panel and in the stack like any object. A new **area** goes behind the symbols by default. Proposed.
- They are never animated and never react to a gesture, except the two kinds below that read a value, and the link zones (see [Navigation links](07-navigation-links.md)). Proposed.

### Kinds of annotation

| Kind | What it is | Status |
| --- | --- | --- |
| Text | A title, a label, a note for the operators. | Proposed |
| Area | A rectangle with a title at its top left: "Building A", "Filtration". Moving it can move what it holds, with a toggle. | Proposed |
| Shape | Any drawing of the symbol editor's tools: a wall, a floor line. | Proposed |
| Legend | A box computed by the editor: the pipe styles used in this synoptic, each with a short pipe and its name. It updates by itself. | Proposed |
| Value label | A text that shows the value of one signal of one placed symbol, in its display unit: `P-101 · 1450 rpm`. For a view that needs a value without placing a symbol. | Proposed |
| Image | A logo or a photograph. Open: the application draws in SVG; a raster image weighs on the runtime. | Open |

### Value labels

- A value label points to **a placed symbol and one of its output signals**. It shows the value as the faceplate shows it: display unit and decimals of the preset of that placed symbol, an enum by the display text of its item (same reading as the text elements of the faceplate, see [Identifiers](../metadata/draft.md#identifiers)). Proposed.
- It follows the placed symbol when the symbol is deleted: the label is broken and listed in the faults. Proposed.
- Its format (prefix, suffix, font) is set in its panel; the symbol editor's rules for texts that show a value apply (see [Animation mode](../symbols/08-animation-mode/README.md)). Proposed.

## Example

The view "Pumping station" has an area "Building A" behind the three pumps, a title "Pumping station" at the top, a legend at the bottom right (water, gas, steam), and a value label `T-1 level · 72 %` next to the small tank drawn in the overview.

## Where it is used

| Thing | Created and changed in | In a symbol | In a synoptic |
| --- | --- | --- | --- |
| Text, area, shape | Annotate mode | The same tools draw the symbol | Draw, edit |
| Legend | Annotate mode | No | Place; content computed |
| Value label | Annotate mode | Texts of a symbol can show a value too | Place, point to a signal |

## Open questions

- Are images allowed in a synoptic, and in which format?
- Does moving an area move what it holds by default?
- Is the value label needed, or should the user make a small symbol instead?
