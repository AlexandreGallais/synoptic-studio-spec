# Pipe styles

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Pipe styles

Status: draft (base style and pipe styles reviewed on the test screens on 2026-11-24, decision 0096). Not validated.

How a pipe looks. A Symbol Lib has **one base pipe style**, the shape shared by all its pipes, and **pipe styles** (water, oil, steam...) that give the fills, the movement of the dashes and, when needed, their own width.

## Rules

### The same sections everywhere

The base pipe style and each pipe style are shown with the **same sections, in the same order**: Body, Border, Corners, Junctions, Crossings. A pipe style adds its own: Linked type at the top, Movement at the end.

| Section | Base pipe style | Pipe style |
| --- | --- | --- |
| Linked type | — | Type of Metadata, optional |
| Body | Width | Width (the base's, or its own); body fill |
| Border | Border on or off; width; position | Border width (open); border fill |
| Corners | Corner radius | Shown, set by the base |
| Junctions | Kind; size | Shown, set by the base |
| Crossings | Kind | Shown, set by the base |
| Movement | — | Direction signal; speed |

- Proposed by the assistant: in a pipe style, an option set by the base is shown read-only with the base's value, so that the user sees the whole pipe without going back to the base.

### The base pipe style

- Each Symbol Lib has exactly one base pipe style. It is the global shape of all the pipes of the library. It holds **no colour and no dash**: the fills belong to the pipe styles.

| Section | Option | What it does |
| --- | --- | --- |
| Body | Width | The width of the body of the pipe, in pixels. |
| Border | Border | On or off. When it is on, it is on **both sides** of the pipe, the same on each side. |
| Border | Width | The width of the border, in pixels. |
| Border | Position | **Inside**, **in the middle** or **outside** the edge of the body, as for the border of a shape (see [Fill and border](../04-drawing-mode/fill-and-border.md)). Inside, the border eats into the width of the body; outside, it adds to it. |
| Corners | Corner radius | Rounds the angles of the pipe (see below). The same for every pipe style. |
| Junctions | Kind and size | How a branch looks: flat, circle or square, with its size; its fill and border are those of the pipe (see [Junctions](junctions.md)). |
| Crossings | Kind | What happens where a pipe passes over another: bridge, gap or none. Its size is computed from the body width (see [Crossings](crossings.md)). |

- Junctions and crossings are parts of the style, not separate lists of the Symbol Lib. They are computed from the style; the user never draws them on each pipe.
- The base pipe style has no start and end shapes: they have a list of their own on the Pipes page (see [Pipe ends](ends.md)).

### Pipe styles

- A pipe style has a **name** (free text: "Water", "Oil", "Steam", "Electricity").

| Section | Option | What it does |
| --- | --- | --- |
| Linked type | Type | A type of Metadata, optional (see [A pipe style linked to a type](#a-pipe-style-linked-to-a-type)). |
| Body | Width | The width of the base, or a width of its own (see below). |
| Body | Body fill | A plain colour, or a **dash sequence** that follows the pipe from its start to its end (see [Dash sequences](#dash-sequences)). |
| Border | Border fill | A plain colour or a dash sequence, like the body. Shown when the base style has a border. |
| Movement | Direction | A signal of the linked type that says whether the dashes move, and which way (see [Moving dashes](#moving-dashes)). |
| Movement | Speed | A signal of the linked type, or a fixed value. |

- **A pipe style can have its own body width**: in the plant, gas pipes are small pipes, so the "Gas" style is drawn thinner. Without a width of its own, the style takes the base's, and follows it when the base changes.
- Open: whether a pipe style can also have its own border width, for the same small pipes.
- **No other option of the base can be changed in a pipe style**: there is no list of overridden options. Corners, junctions, crossings, border on or off and border position are the base's for every pipe style.
- The content ("what the pipe contains") only names and groups the styles. The editor does not know what a fluid is.
- A pipe has one pipe style, chosen in the synoptic; its branches have the same (a pipe is one tree, see [Junctions](junctions.md)). The base style has no colour, so a pipe always has a pipe style (assumption of the assistant, to confirm).
- A pipe style is stored in the Symbol Lib and used by identifier, as a symbol is linked to its type (the rules of broken links are to be written like for symbols).

```mermaid
flowchart TD
    B["Base pipe style of the Symbol Lib: width, border, corner radius, junctions, crossings; no colour, no dash"]
    B --> W["Water: blue body, grey border"]
    B --> S["Steam: white body, dashed border"]
    B --> G["Gas: yellow body, its own width (small pipe)"]
    W --> P1["Pipes of the synoptic"]
    S --> P1
    G --> P1
```

### Dash sequences

The rule, for pipes and for **every border** of the software (the borders of shapes too, see [Fill and border](../04-drawing-mode/fill-and-border.md)):

- Dashes are not "a dash length and a gap". They are a **sequence of segments**, each with a **length** and a **colour**, repeated along the line.
- A gap is simply a segment with a **transparent** colour. Classic dashes: black 4 px, transparent 4 px. Two-colour dashes: red 4 px, black 4 px, repeated.
- The sequence can be as long as the user wants (red, black, red, transparent...). Each segment can be deleted (see [PI-04](../../screens/pipes.md#pi-04--dash-sequence-editor)).
- A body filled with a dash sequence shows dashes that run along the pipe from its start to its end.

Example:

| Sequence | Result |
| --- | --- |
| Black 4, transparent 4 | Classic dashes |
| Red 6, black 6 | Red and black stripes |
| Black 8, transparent 2, black 2, transparent 2 | Dash and dot |
| Black 10, transparent 20, red 2 | A long black dash, a long gap, a short red mark, then again black, gap, red |

```mermaid
block-beta
    columns 7
    a["Black 10"] b["Transparent 20"]:2 c["Red 2"] d["Black 10"] e["Transparent 20"] f["..."]
```

### Computing the dashes

- Everything about a pipe is computed, the dashes too: they are computed from the drawn pipe, so that they follow it, corners and arcs included.
- The computation aims for the cleanest result: dashes that run continuously along the pipe, with no odd piece where it can be avoided.
- It is not a hard requirement: where a dash cuts a little oddly in a corner, it is accepted as it is.

### Moving dashes

- The dashes of a pipe style **move** to show the flow. There is **no on or off option**: the movement comes from a **signal of the linked type**.
- **Direction**: the user picks a signal of the linked type that says whether the dashes move and which way: stopped, from the start of the pipe to its end, or from the end to its start. Its values come from the built-in enum **pipe direction** of Metadata (see [Built-in enums](../../metadata/draft.md#built-in-enums)).
- **Speed**: either a signal of the linked type, or a fixed value. The fixed value can always be typed: it is never greyed out behind an option.
- Without a linked type, or without a direction signal, the dashes do not move (assistant's reading, to confirm).
- **Propagation**: where a branch leaves the pipe (a junction), the movement goes on into the branch, following the flow: the whole tree is one flow. The pipe is no longer a plain drawing: it behaves half like a symbol.
- The unit of the speed is open.
- Assumption of the assistant, to confirm: the movement can be stopped by a global setting and by the system setting "reduce motion" (advised by the research).

```mermaid
flowchart LR
    T["Linked type"] -->|"signal, enum pipe direction"| D{"Direction"}
    D -- "Stopped" --> X["Dashes still"]
    D -- "Start to end" --> F["Dashes move forward"]
    D -- "End to start" --> R["Dashes move backward"]
    V["Speed: a signal of the type, or a fixed value"] --> F
    V --> R
```

### A pipe style linked to a type

- A pipe style **can** be linked to a type of Metadata, in its first section. A style with no type is a drawing, whose dashes do not move.
- Linked to a type, the style is animated by the model, like a symbol with a type (see [Animation mode](../08-animation-mode/README.md)):
  - the **direction** and the **speed** of the moving dashes, through the signals picked in the section Movement (above);
  - the **colours** (body, border) change with what happens;
  - and other properties of the style, "plenty of things like that".
- The type is chosen among all the types of Metadata, as for a symbol: there are no libraries of types.
- Assumption of the assistant, to confirm: only output signals animate, with the same shapes of mapping as for symbols (bounded linear, by ranges, two values for a boolean, state table for an enum).
- Each pipe of the synoptic then gets its own values from the model, as a placed symbol does (to write in part 3).

```mermaid
flowchart LR
    T["Type of Metadata (optional)"] -->|"output signals"| S["Pipe style"]
    S --> D["Dashes: direction, speed"]
    S --> C["Colours of body and border"]
    D -->|"propagation at junctions"| B["Branches"]
```

### Corner radius

- The user draws a pipe with straight segments only: click, click, click.
- The corner radius rounds each angle of the pipe. A right angle then gets a curve, which makes the pipe a little more stylised.
- With a radius of 0, the angles stay sharp.
- It is set once, in the base style, and is the same for every pipe style: different radii side by side would look odd.
- The radius also decides the look of the bridges at crossings (see [Crossings](crossings.md)).
- It is the only setting of the angles: there is no path kind (straight, right angles, rounded) to choose on each pipe.

## Example

Base style of the library "Plant A": width 6 px; border on, 1 px, outside; corner radius 8 px; junction circle 12 px; crossing bridge.

| Pipe style | Linked type | Fills | Movement | Own width |
| --- | --- | --- | --- | --- |
| Water | — | Body blue; border dark grey. | None: no type | — |
| Steam | `steam_line` | Body white; border dashes: grey 4, transparent 4. | Direction: `flow_direction`; speed fixed | — |
| Oil | `oil_line` | Body dashes: black 10, transparent 20, red 2; border dark grey. | Direction: `flow_direction`; speed: `flow_speed` | — |
| Gas | `gas_line` | Body yellow; border dashes: black 10, transparent 20, red 2. | Direction: `flow_direction`; speed fixed, 40 | 3 px (small pipes) |
| Electricity | — | Body yellow; border yellow. | None: no type | 2 px |

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.2, 3.4, 3.5, 3.6, 3.7). Written before the base style and dash sequences above: what they settle is said under each point.

### Name of the content

- Words found: service, fluid, appearance, line variation, content. Opinion of the report: keep **Content**, as a simple group label ("fluid" excludes electricity; "service" is the trade word, to quote in the documentation).

### Body and borders: two ways

| Way | Principle | For | Against |
| --- | --- | --- | --- |
| A · Two strokes on top of each other | A wide stroke (the border) under a narrower one (the body), on the same centre line. It is what the archived Figma page does ("Pipe — outline", "Pipe — core"). | Native, no outline to compute, native dashes possible. | These are SVG strokes; native dashes have one colour only. |
| B · Computed outlines | The engine computes the polygons of the body and of each border by offset. | Follows "a border is a fill"; inside, middle and outside borders; dash sequences of several colours. | Computed at each move of a point. |

- The rules (border inside, in the middle or outside; dash sequences of several colours; everything computed) match **way B**. Inference of the assistant, to confirm with the POC P9 (cost of the computation).

### Flow dashes

- Native dashes (`stroke-dasharray`, moved by `stroke-dashoffset`) exist only on a stroke and have **one colour**. A sequence of several colours is therefore computed.
- The report advised a separate native stroke for the flow dashes. **Superseded**: the dashes are now a fill of the body or of the border, computed.
- Animating dashes redraws the pipe at every frame; a WebKit bug reports a high load with a single `stroke-dashoffset` animation. An animation that lasts more than five seconds must be possible to pause (WCAG), and the system setting "reduce motion" can be read by the browser.
- The cost follows the number of dashes: the POC P8 (number of dashes) and P10 (animated dashes on 10 to 500 pipes) still apply, now on computed dashes.

### What can drive the look of a pipe

| Option | Principle | Opinion of the report |
| --- | --- | --- |
| A · Nothing | The pipe is a drawing; its dashes are fixed. | The simplest; poor compared with SCADA tools (ThingsBoard: fluid present, flow present, direction, speed, leak). |
| B · The pipe has a type of Metadata | A "dynamic" pipe style is linked to a type (signals: flow present, direction, state), like a dynamic symbol. | **Advised**, limited to three signals: a boolean "flow present" (dashes moving or still), a direction (forward, backward), an enum of state that changes the style (hot, cold). A speed proportional to the flow is refused first: the eye cannot read it. Confidence: low (one tool source). **Chosen, without the limit to three signals: the speed can follow the model.** |
| C · The pipe borrows a signal of a neighbouring symbol | In the synoptic, a signal of a connected symbol is picked. | Quick, but links a drawing to another in a fragile way. |

## Open questions

- Can a pipe style have its own border width, besides its own body width?
- Does the direction signal hold "stopped" itself (one enum of three values), or does a second signal say whether the dashes move?
- Which properties of a style a signal can drive, beyond the speed, the direction and the colours?
- Can the base pipe style be linked to a type, or only the pipe styles?
- In which unit is the speed of the moving dashes set (pixels per second)?
- A pipe linked to a type is one tree, one flow: do its branches share its values (assistant's reading), or can a branch have its own (a closed valve on one branch, stopping the movement downstream)?
- Can a style hold several layers (the body, then a border, then a second line), or just the options above?
