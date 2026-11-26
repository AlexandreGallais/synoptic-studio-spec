# Fill and border of a shape

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Fill and border

Status: draft. Not validated.

What every shape has in common: the [rectangle](rectangle.md), the [ellipse](ellipse.md), the [polygon](polygon.md) and the path drawn with the [pen](pen.md). They are set in the right-hand panel, after the [geometry](geometry.md).

## Rules

- A shape has **fills** (its background) and can have a **border**.
- The border is not an SVG stroke. It is a fill, so that it can be placed **outside**, **in the middle** or **inside** the shape.
- The border is simulated. In the layer tree, the user sees one shape only. In the exported SVG, it is two different shapes: the shape and its border.
- A [group](group.md) has no fill and no border: a group does not do that, it only gives a structure. A shape keeps them, which keeps a little of the logic of SVG.

### Several fills

- A shape can have **several fills**, stacked: a **+** on the right of the title "Fill" adds one, a **−** at the end of its line removes it (Product Owner, 2026-11-25: "un moins, c'est qu'on peut en ajouter plusieurs").
- The **line at the top is drawn on top**, as in Figma. Example: a plain background on the last line, a linear gradient over it on the first line, partly transparent.
- No fill: no line; there is no kind "None" (Product Owner, 2026-11-24).
- Like the border, several fills are simulated: one shape in the layer tree, one path per fill in the exported SVG, the same geometry stacked.

### What a fill can be

| Kind | Notes | Status |
| --- | --- | --- |
| Plain colour | With opacity. | Decided (2026-11-25) |
| Linear gradient | Several colour stops, an angle. | Decided (2026-11-25) |
| Radial gradient | Several colour stops, a centre. | Decided (2026-11-25) |
| Conic gradient | Colours turning around a centre (CSS only). | Set aside (2026-11-25) |
| Pattern | A small drawing repeated (SVG `pattern`). | Set aside (2026-11-25) |
| Image | A picture fills the shape. | Set aside (2026-11-25) |

The border can be given the same kinds of fill as the background. The stops and the editing of a gradient on the drawing: [Paints](paints.md).

### How a fill is set

- One line, the [colour field](../../controls/colour-field.md): a swatch, then the colour │ the opacity, two inputs split by a separator (Product Owner, 2026-11-24: "la même façon de faire que Figma").
- The kind is chosen in the popup the swatch opens, not in a select of the panel; the popup also has the eyedropper, the hue and opacity sliders, and the formats Hex, HSL, HSB (see [Colour field](../../controls/colour-field.md#the-paint-popup)).

### Border options

The border is a [segment list](../../controls/segment-list.md) (Product Owner, 2026-11-24):

- **Lines**: a small + on the right of the title "Border" adds a line; each line is a segment, with its [colour field](../../controls/colour-field.md) (colour and opacity) and its **length**; a − removes it.
  - **One line**: a plain border.
  - **Several lines**: a **dash sequence** (the same rule as for pipes, see [Pipe styles](../pipes/pipe-styles.md#dash-sequences)): the segments follow each other along the border and repeat; a gap is a segment at **0 %** opacity: "black 100 % 2, black 0 % 2" gives classic dashes; "red 4, black 4" gives red and black dashes; as many lines as the user wants.
  - **No line**: no border; there is no toggle "Border" (Product Owner, 2026-11-24).
- **Size** and **position**, on one line under the lines: the width of the border in pixels, written without unit (example: 2), then a **segmented control** Inside, Middle, Outside, changed in one click (Product Owner, 2026-11-26, replacing the select of 2026-11-24; see [the layout rule](../../screens/README.md#a-segmented-control-for-two-to-four-short-options)).
- The dashes are computed along the border, as cleanly as possible; an odd cut in a corner is accepted.

### Border of an open path

- A line drawn with the [pen](pen.md) has the same three positions: **Middle**, **Inside** and **Outside** (Product Owner, 2026-11-25: "ça peut être super utile").
- On an open path, Inside and Outside put the whole border on one side of the line or on the other, computed, instead of centred on it. Which side is "inside": the left of the line, in the direction it was drawn (assistant's proposal).
- No line caps and no line joins to choose (butt, round, square; miter, round, bevel): not offered (Product Owner, 2026-11-25). The ends and the corners of a border are those the computation gives; a rounded corner comes from the corner radius of the path, which the border follows (Product Owner, 2026-11-25).

### Dashes: what the research says

- Native SVG dashes (`stroke-dasharray`) exist only for a stroke, and have **one colour**. The border of the project is a fill, and a dash sequence can have several colours: the dashes are therefore computed, each dash as a small shape, as for pipes. It is a geometric calculation redone at each resize, for the geometry research. Confirmed for shape borders (Product Owner, 2026-11-25: "ça va être calculé").
- The cost follows the number of dashes (the perimeter divided by dash plus space). The editor needs a maximum number of dashes per shape, set by the POC (P8).
- No source gives the cost of a gradient or of its number of colour stops: a short POC (P8) is planned.

## What the second research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.18, 3.20). "Opinion" is the report's, not a decision.

### Open paths

- SVG 2 has no inner or outer stroke: the inside and outside borders of an open path are computed (decided above).
- A border "in the middle" looks exactly like a native stroke. Opinion: allowing a native stroke under the hood **in this case only** would settle at once its dashes. Since then, dashes are sequences of several colours (2026-11-11), which a native stroke cannot draw in one piece: the native stroke would only help plain borders.
- Arrows on a line: SVG markers exist (start, middle, end). Opinion: one single concept, the end shape of the Symbol Lib, for lines and pipes. The end shapes of pipes were removed (decision 0098), and the arrow heads are set aside in this version (2026-11-25).

### Gradients

- The part of SVG 2 read defines linear and radial gradients, `spreadMethod` (pad, reflect, repeat) and a focal circle. Opinion: linear and radial; neither `spreadMethod` nor focal point in the first version. The absence of a conic gradient was not confirmed by the part read.

### Colours

| Subject | Sources | Opinion of the report |
| --- | --- | --- |
| HMI guides ("high-performance", ISA-101, known through secondary sources) | Grey background and muted colours; bright colours for the abnormal; never colour alone; alarm colours reserved; about seven colours safely told apart; some vendors defend realistic graphics. | Help without imposing: a "high-performance" palette by default; a contrast check; a warning when a colour reserved to alarms is used elsewhere. |
| Named colours | The archived Figma page gives each style its own colour value; Figma variables and Ignition style classes were not read. | A flat list "Colours" in the Symbol Lib; symbols, pipe styles and state tables point to it by identifier. Confidence: low. |
| Colour blindness | Colour cannot be the only way to carry information (WCAG level A). | In a state table, offer a second cue (shape, text); a colour-blind preview later. |
| Colour picker | The `EyeDropper` interface is experimental, not in every engine, secure contexts only. | An eyedropper of the editor itself, reading the colour of a shape of the drawing (kept, see [Colour field](../../controls/colour-field.md#the-paint-popup)). |

## To decide by the Product Owner

1. A native stroke allowed under the hood for a plain "middle" border, or every border computed?
2. Named colours in the Symbol Lib, and a "high-performance" palette by default?
