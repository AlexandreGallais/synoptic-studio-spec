# Text tool

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Text

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

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

### Size of the box

- The editor computes the size of the box from the font.
- **Fit mode**: when the box fits its text, the user chooses what it fits.
  - **Fit to the glyphs**: the box wraps the text as drawn.
  - **Fit to the line**: the box follows the line of the text, its baseline. A "g" has a tail that goes below the line, an "a" starts on the line. In this mode the box does not change because of such letters. The goal is to align texts of different font sizes on the same line, for a better look.

### Font

| Option | What it does |
| --- | --- |
| Family | The font, chosen among the fonts of the software (see below). |
| Size | The font size. |
| Weight | All the weights the font has, not only bold. The editor reads what the font offers. |
| Bold button | A button, there by default, to make it simple to understand. The list of all the weights is next to it. |
| Italic | Offered when the font has an italic. To check whether every font does. |

### Colours and lines

- **Text colour** and **background colour** (highlight).
- **Text border**: wanted if SVG does it natively, with the SVG stroke of the text, never a path made from the letters. Example: a white text with a white border stays readable on any background colour. Not a priority; dropped if it is not simple.
- **Lines**: underline, strikethrough and line above, at the bottom, in the middle and at the top of the text. The colour of the line can be edited.

### Placement and spacing

- **Alignment**: left, centre, right, and top, middle, bottom, in the box.
- **Spacing**: letter spacing, word spacing, line height.
- **Wrapping** of the lines in the box.

### Fonts of the software

- Only the fonts of the software are offered. They are chosen among the fonts free to be put in SVG files (licence).
- **Embedding**: an option puts the fonts directly into the exported SVG document, so that no font is needed next to it. The user chooses whether to embed or not.
