# Text tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Text

Status: draft. Not validated.

## Rules

### Content

A text is one of three things:

- a text the user writes;
- a text linked to a signal: it shows the value of the signal;
- a text linked to the unit of a signal: it shows only the unit, in the display unit.

The last two are set in the [Animation mode](../08-animation-mode/README.md).

### Editing

- A text is edited like in a word processor: the user can format a part of it.
- Resizing the box of a text enlarges the text zone only, never the size of the text (see [Select](../03-editor/select.md)).

### Panel of a text

In this order, each section compact (Product Owner, 2026-11-25: "plus lisibles, plus compactes et moins fouillis"):

1. **Geometry**: the box and its place (see below and [Geometry](geometry.md)).
2. **Font**: family, then size and style on one line.
3. **Colour**: the text colour, then its border.
4. **Paragraph**: alignment, spacing, wrapping, lines.
5. **Effects**, as every shape.

### Size of the box

- **W** and **H** of the box, with the [size fields](../../controls/size-fields.md): each **Fixed** (the size typed) or **Hug** (the box fits its text) (Product Owner, 2026-11-25: "définir le width et le height de la box, ou alors mettre fit").
- **Fit mode**, shown when a field is in Hug: what the box fits, in a select.
  - **Fit to the glyphs**: the box wraps the text as drawn.
  - **Fit to the line**: the box follows the line of the text, its baseline. A "g" has a tail that goes below the line, an "a" starts on the line. In this mode the box does not change because of such letters. The goal is to align texts of different font sizes on the same line, for a better look.

### Font

| Option | What it does |
| --- | --- |
| Family | The font, chosen among the fonts of the software (see below). |
| Size | The font size, on the line of the style. |
| Style | One select with every weight the font has and, for each, its italic when the font has a real one, as Figma does: Regular, Italic, Medium, Medium Italic, SemiBold, SemiBold Italic, Bold... The editor reads what the font offers. No bold button and no italic button (Product Owner, 2026-11-25: a font is chosen once, "on n'est pas sur Word"). |

### Colour and border

- **Text colour**: one [colour field](../../controls/colour-field.md).
- **No background colour**: the background of a text is not coloured, for now (Product Owner, 2026-11-25: "jamais vu une utilisation").
- **Text border**: a true SVG stroke of the letters, never a path made from them nor a simulated border (Product Owner, 2026-11-25: useful on desks, a white text with a dark border stays readable on any background). A + on the title "Border" adds it: a colour field and a size; a − removes it. One colour, no dashes, no position: the stroke is drawn under the letters (`paint-order: stroke`).

### Paragraph

- **Alignment**: a 9-point [anchor](../03-editor/anchors.md) grid, the place of the text in its box: left, centre or right, and top, middle or bottom, in one click (Product Owner, 2026-11-25: "un truc d'ancre... plus simple visuellement").
- **Spacing**: letter spacing, word spacing and line height, on one line; Auto for the line height and 0 for the others by default (Product Owner, 2026-11-25: "parfait").
- **Wrapping** of the lines in the box: a toggle.
- **Lines**: underline, strikethrough and line above, at the bottom, in the middle and at the top of the text, three toggle icon buttons on one line, each can be on with the others; once one is on, the colour of the lines shows under them, one colour field for all.

### Fonts of the software

- Only the fonts of the software are offered. They are chosen among the fonts free to be put in SVG files (licence).
- **Embedding** the fonts in the exported document is not set in the symbol editor: it is an option of the export of the views (Product Owner, 2026-11-25; see [Outputs](../../synoptics/10-outputs.md)).

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.21, 3.23). "Opinion" is the report's.

| Subject | Sources | Opinion of the report | Confidence |
| --- | --- | --- | --- |
| Licence | A font under the **OFL** can be shipped with any software and embedded in a document, whole or in part, without the document becoming OFL. Subsetting or converting the font is a modification: the reserved name can then no longer be used. The FAQ says nothing about SVG or base64. | Pick OFL fonts with no reserved name, or embed the whole file. | medium |
| Weights, italic | Weight goes from 100 (Thin) to 900 (Black); any value from 1 to 1000 is valid. | List weights and italics from an inventory of the bundled fonts; italic only if the family has a real one. | medium |
| Box fit to the line | CSS has `text-box-trim` and `text-box-edge` (cap height, baseline), available everywhere since August 2026. Nothing equivalent was read for SVG text. | "Fit to the line": from the cap height to the baseline, computed from the metrics of the font. | low |
| Text border | A stroke applies to text; `paint-order: stroke` paints it under the fill; available everywhere since January 2020. | **Offer the text border**: native and simple. | high |
| Text along a path, vertical text | No source read. | Refuse first. | — |
| Translatable texts | No source read. | Out of the first version, keeping a stable identifier per text. | — |

For a text that shows a value (number format, missing value, text that becomes an input), see [Animation mode](../08-animation-mode/README.md).

## To decide by the Product Owner

1. OFL fonts only, embedded whole?
