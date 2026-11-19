# Animation mode

> [Home](../../README.md) › [Symbols](../README.md) › Animation mode · Previous: [Interaction mode](../07-interaction-mode/README.md) · Next: [Run mode](../09-run-mode/README.md)

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

The mode of the [editor](../03-editor/README.md) in which the signals are linked to the drawing. Animating a symbol means that the value of a signal changes a part of the drawing. The change of scale or of range (0 to 1 turned into 0 to 90 degrees) is done here, not in Metadata: Metadata only states the contract with the model (see [Signals](../../metadata/draft.md#signals)).

## Rules

- Tool bar: [Select](../03-editor/select.md) and [Hand](../03-editor/hand.md). Right-hand panel: the animations of the selected part.
- The user selects a signal, then says what it animates: a shape, a layer, a text.
- Only the output signals of the type are offered for an animation. An output is what the model sends, and the model computes what the symbol shows. An input is what the model receives and is never animated; it can only serve as the minimum or the maximum of a bounded linear animation (Product Owner, 2026-11-17, see [below](#the-input-range-of-a-bounded-linear-animation)).
- A value ordered and a value obtained are two signals for the model. Example: `opening_order` (input, what the user asks) and `opening` (output, what the model computes). The symbol animates `opening`. The faceplate can show both (see [Presets](../../metadata/draft.md#presets-and-their-faceplate)).
- Only a symbol with a type has animations. A symbol without a type has no signal to animate (see [Libraries and symbols](../01-libraries-and-symbols.md)).

```mermaid
flowchart LR
    M["Model"] -->|"output signal"| S["Symbol"]
    S -->|"animation"| D["Part of the drawing"]
    U["User order"] -->|"input signal, via a command"| M
```

## What an animation can do

| Signal type | Example | What it does |
| --- | --- | --- |
| Real or integer | `opening` from 0 to 1 | A range of values becomes a range of a property of the drawing: 0 to 1 becomes a rotation of 0 to 90 degrees. |
| Boolean | `running` | A value gives a state: when `true`, an element blinks. |
| Enum | `mode` | A property of the drawing takes the value of a column added to the enum in the Symbol Lib, for the current item: `mode` = 1 gives the colour of the column `color` for item 1 (Product Owner, 2026-11-17; see [Enums of a Symbol Lib](../11-enums-of-a-symbol-lib.md#used-by-an-animation)). |

The properties of a part of the drawing that an animation can drive (rotation, position, size, colour, opacity, visibility, blinking...) are to list.

## Texts: value and unit

A text of the symbol can be linked to a signal that has a quantity (a volume, a flow...).

- The text shows the signal's value, converted to the display unit and rounded to the decimal places set in the preset (see [Units](../../metadata/draft.md#units)).
- The user chooses whether the text shows the unit or not.
- Another text can hold only the unit of the signal, in the display unit. This lets the user put the value in one place and the unit in another, and the unit follows the display unit.

```mermaid
flowchart LR
    S["Signal: flow, model unit L/s"] --> V["Text 1: the value, in the display unit"]
    S --> U["Text 2: the unit only, in the display unit"]
```

### A text that becomes an input

Decided by the Product Owner (2026-11-11). A text can be set at the size the user needs, and it can turn into an input when the user clicks it, if an input signal is linked to it. It makes quick entries: no separate panel is opened.

- Since commands always send a fixed value (2026-11-16, see [Commands](../../metadata/draft.md#the-value-is-always-fixed)), this text **writes an input signal of the type directly**, with the same checks as a write entry of the faceplate: conversion from the display unit, enum item, and the bounds of the number field, typed by hand or taken from a signal (see [Presets](../../metadata/draft.md#bounds-of-a-number-field), decision 0041) (Product Owner, 2026-11-16, accepting the assistant's proposal). No command is used.
- Only an input signal can be linked: an output is computed by the model.

| What the text shows | What a click does |
| --- | --- |
| A number | The text turns into a **number input**, right there. This is the main case. |
| An enum | A **selection menu** opens, with the whole list of the enum, and the user picks one item. |

- The user chooses, in the editor, which of these a text does: number input or selection menu.
- **No text input** (Product Owner, 2026-11-18): a signal is never a text (see [Signals](../../metadata/draft.md#no-text-signal)).
- An enum is shown by the display text of its item, never by its key (see [Enums](../../metadata/draft.md#enums)). A click on it opens the menu of the display texts; the input signal receives the key of the item picked.
- What the user picks or types is checked, converted to the model unit, then written to the input signal.

```mermaid
flowchart LR
    T["Text shown"] -->|"number: click"| N["Number input"]
    T -->|"enum: click"| M["Menu with the whole list"]
    N --> K["Checked and converted, as in the faceplate"]
    M --> K
    K --> S["Input signal written, sent to the model"]
```

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Animation (signal, target, mapping) | Symbol editor | Symbol | Create, edit | No |
| Text linked to a value or to a unit | Symbol editor | Symbol | Create, edit | No |

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.11 to 3.16, 3.21). Nothing measured; "Opinion" is the report's.

### Properties a signal can drive

Transform and opacity, animated by CSS or by the animation interface of the browser, go through the graphics card; animating a position or a radius by attribute, deforming a path or moving dashes triggers a repaint, whose cost follows the area.

| Property | SVG mechanism | Expected cost | Opinion of the report |
| --- | --- | --- | --- |
| Rotation | Transform | Low | Offer |
| Position | Transform | Low | Offer |
| Opacity | Opacity | Low | Offer |
| Visibility (show, hide) | Display | Low | Offer |
| Fill or border colour | Repaint | Medium, but rare (a change of state) | Offer |
| Fill level (tank, gauge) | Cut by a rectangle that moves | Low if the cut is simple | Offer, as a dedicated animation |
| Blinking | Opacity animation | Low | Offer, bounded (below) |
| Dash travel | `stroke-dashoffset` | Repaint at each frame | Pipes and lines only, subject to POC P10 |
| Gradient stop or colour | Repaint | To measure | Subject to a POC |
| Size by scale | Transform | Low, but makes the borders grow | Not first: against "never a scale" |
| Point deformation, filter parameters, `viewBox` | Repaint or filter | High | Refuse |

### Shapes of mapping

| Shape | For | Opinion of the report |
| --- | --- | --- |
| Bounded linear: an input range becomes an output range; outside it, the output stays at its bound | Integer, real | Offer; the input range is chosen by the user (below) |
| By ranges (thresholds): a table of non-overlapping ranges, each with a value (as in WinCC Unified, which flags overlaps) | Integer, real | Offer |
| Two values | Boolean | Offer |
| State table | Enum | Offer (below) |
| Table of points (piecewise linear) | Integer, real | Later |
| Curve, expression, script | — | Refuse: against "for everyone" |

Confidence: low (one tool read).

### The input range of a bounded linear animation

Decided by the Product Owner on 2026-11-17 (decision 0027, accepted on 2026-11-17), since a signal has no bounds of its own (a bound is a plain signal, see [Signals](../../metadata/draft.md#rules-3)).

- The user chooses the **minimum** and the **maximum** of the input range.
- Each of the two can be **a signal of the type**, an input or an output (Product Owner: "pour les bornes, on pourra choisir soit un in, soit un out"). Example: the maximum taken from `speed_setpoint_max`, an input.
- Each can also be a **number typed** by the user. Assistant's reading of "on va pouvoir choisir le min et le max", to confirm.
- The minimum and the maximum are chosen separately: one can be a number and the other a signal.
- **The value that drives the animation is always an output** of the model (Product Owner: "il n'y a que la valeur qui change qui devrait être obligatoirement out"), as for every animation.
- The output range (for example 0 to 360 degrees) is typed, as before.

```mermaid
flowchart LR
    V["Value: an output signal"] --> A["Bounded linear"]
    MIN["Minimum: a number, or a signal in or out"] --> A
    MAX["Maximum: a number, or a signal in or out"] --> A
    A --> P["Property of the drawing, within the output range"]
```

### Enum: a state table

For each value of the enum, the values of a few properties (colour, visible layers, text), plus a default row for an unknown value. No state machine: the enum already carries the state, and transitions are the model's business. Code a state by brightness and a word, never by colour alone. Keep the word "Animation" ("dynamization" at Siemens). Confidence: low.

Decided by the Product Owner on 2026-11-17 (decision 0036, accepted on 2026-11-17): the table is not written in each animation but **once per Symbol Lib**, as columns added to the enum on the [Enums page of the Symbol Lib](../11-enums-of-a-symbol-lib.md). An animation picks the column it uses. The default row for an unknown value is still open there.

### Transition, pivot, conflicts, blinking

| Subject | Opinion of the report | Confidence |
| --- | --- | --- |
| Jump or smooth | An option per animation: no transition, or a short linear duration; none by default for a change of state. | low |
| Pivot | One of the nine anchors of the box (centre by default) or a point set by the user. In CSS, an SVG element turns around the origin of the `viewBox` unless `transform-box: fill-box` is set. | medium |
| Two animations on one property | Forbid it and flag it in the editor; transforms of different kinds compose in a fixed order: move, then rotate. | very low |
| Blinking | A "Blink" animation at a fixed rate, under three flashes per second (WCAG level A), by opacity; a reminder in the editor ("keep it for the abnormal"); a global stop; follow the system's "reduce motion". A blink lasting more than five seconds must be possible to stop. | medium |
| Many animated symbols | POC **P11**: 50, 200, 1 000 symbols animated by signals at 10 updates per second. | — |

### Quality of a value

Ignition classes quality as Good, Uncertain, Bad, Error, and shows an overlay on the component (pending, unknown, error). Opinion of the report: show it **by default** on every symbol animated by a signal whose quality is not good, with a mark that is not only a colour; not an animation to configure. The signals of Metadata have no quality: it is a question for the contract with the model.

### Texts that show a value

- The browser formats a number by language (decimal comma), with or without thousand separators, leading zeros, decimals or significant digits, standard, scientific or engineering notation, sign always or never.
- Opinion of the report: no free format string. In the preset: the decimals (already). Per text: thousand separator (off by default), sign, leading zeros, notation. The language of the application sets the decimal comma.
- Missing value: a long dash and the quality mark. Out of range: the value as it is (a signal has no bounds of its own since 2026-11-17). Too long for a fixed box: "####", never truncated digits. Confidence: very low.

### A text that becomes an input: a gap with a validated page

- `foreignObject` is supported everywhere since 2015, but **WebKit misplaces HTML content inside it** as soon as it gets a layer (opacity, transform, relative or absolute position): bug opened in 2009, still open (changed 2026-09-11). An `<input>` in it is badly scaled and the buttons of a number field are shifted.
- Opinion of the report: do not put the input in the SVG. On click, lay an HTML field over the text, outside the SVG. Decision 0014 (accepted) makes the text write an input signal of the type directly, without a command; decision 0006 (proposed) carries the HTML field instead of an SVG `foreignObject`, in two forms only, a number or an enum item (no text, decision 0043), and waits for POC P12. POC **P12**: an input in a `foreignObject` against an HTML field laid over it, in Chromium, Firefox and WebKit, with zoom and rotation of the symbol. Confidence: high.
- Pitfalls of the input: Enter validates, Escape cancels, losing the focus cancels; the value shown is frozen while typing; decimal comma by language; checks and conversion follow the faceplate rules of Metadata.

## To decide by the Product Owner

1. The list of animatable properties and the shapes of mapping above?
2. The state table for an enum: settled on 2026-11-17, as columns of the Symbol Lib (see above).
3. Blinking bounded under three flashes per second, with a global stop?
4. Quality of a value shown by default: needs a quality in the contract with the model.
5. Text that becomes an input: an HTML field laid over the text instead of a `foreignObject`? Proposed in decision 0006, settled after the POC P12.

## Open questions

- See [Open questions](../10-open-questions.md).
