# Pipe styles

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Pipe styles

Status: draft (base style and pipe styles reviewed on the test screens on 2026-11-24, decisions 0096, 0097 and 0099). Not validated.

How a pipe looks. A Symbol Lib has **one base pipe style**, the shape shared by all its pipes, and **pipe styles**, one for each item of the built-in enum `pipe_style` (water, oil, steam...), that give the fills and can override a few values of the base: the linked type, the movement of the dashes, the body and border widths.

## Rules

### The same sections everywhere

The base pipe style and each pipe style are shown with the **same sections, in the same order**: Linked type, Body, Border, Corners, Junctions, Crossings, Movement.

| Section | Base pipe style | Pipe style |
| --- | --- | --- |
| Linked type | Type of Metadata, optional | The base's type, or its own |
| Body | Width | Width (the base's, or its own); body fill |
| Border | Width (0: no border); position | Width (the base's, or its own); border fill |
| Corners | Corner radius | Shown, set by the base |
| Junctions | Kind; size | Shown, set by the base |
| Crossings | Kind | Shown, set by the base |
| Movement | Direction; speed | The base's, or its own |

- In a pipe style, an option set by the base is shown **read-only** with the base's value, its section tagged "Base", so that the user sees the whole pipe without going back to the base (accepted on 2026-11-24).
- The base holds the movement too, with its linked type: its signals belong to that type (Product Owner, 2026-11-24).
- A pipe style also shows, above these sections, the **item of `pipe_style`** it draws; the base has none (assistant's reading, decision 0099).

### The base pipe style

- Each Symbol Lib has exactly one base pipe style. It is the global shape of all the pipes of the library. It holds **no colour and no dash**: the fills belong to the pipe styles.
- It is the **first item** of the left column of the Pipes page, above the title of the pipe styles (accepted on 2026-11-24).

| Section | Option | What it does |
| --- | --- | --- |
| Linked type | Type | A type of Metadata, optional, taken by every pipe style that does not choose its own (see [Linked type](#linked-type)). |
| Body | Width | The width of the body of the pipe, in pixels. |
| Border | Width | The width of the border, in pixels, on **both sides** of the pipe, the same on each side. **0: no border**; there is no on or off option. |
| Border | Position | **Inside**, **in the middle** or **outside** the edge of the body, as for the border of a shape (see [Fill and border](../04-drawing-mode/fill-and-border.md)). Inside, the border eats into the width of the body; outside, it adds to it. Greyed out when the width is 0 (assistant's reading). |
| Corners | Corner radius | Rounds the angles of the pipe (see below). The same for every pipe style. |
| Junctions | Kind and size | How a branch looks: flat (the pipes join in one clean outline), circle or square; a circle or a square has a size. Its fill and border are those of the pipe (see [Junctions](junctions.md)). |
| Crossings | Kind | What happens where a pipe passes over another: bridge, gap or none. Its size is computed from the body width (see [Crossings](crossings.md)). |
| Movement | Direction, speed | Each a value, or a signal of the linked type picked with the icon inside its field (see [Moving dashes](#moving-dashes)). Always shown, even without a type (Product Owner, 2026-11-24). |

- Junctions and crossings are parts of the style, not separate lists of the Symbol Lib. They are computed from the style; the user never draws them on each pipe.

### Pipe styles

- A pipe style is **the look this Symbol Lib gives to one item of the enum `pipe_style`** (see [The enum pipe_style](#the-enum-pipe_style)). It has no name of its own: the **key, the display name and the description are those of the item**, in the enum, not in the style (Product Owner, 2026-11-24).

| Section | Option | What it does |
| --- | --- | --- |
| Item | Key, display name, description | Those of the item of `pipe_style`, shown at the top of the style (see [The enum pipe_style](#the-enum-pipe_style)). |
| Linked type | Type | The base's type, or a type of its own (see [Linked type](#linked-type)). |
| Body | Width | The width of the base, or a width of its own. |
| Body | Body fill | A plain colour, or a **dash sequence** that follows the pipe from its start to its end (see [Dash sequences](#dash-sequences)). |
| Border | Width | The border width of the base, or a width of its own. |
| Border | Border fill | A plain colour or a dash sequence, like the body. Greyed out when the border width is 0 (assistant's reading). |
| Movement | Direction | The base's direction, or its own: stopped, start to end or end to start, chosen in the list or given by a signal of its type (see [Moving dashes](#moving-dashes)). |
| Movement | Speed | The base's speed, or its own: a fixed value, or a signal of the linked type. |

- The item says what the pipe contains; it only names and groups. The editor does not know what a fluid is: **each Symbol Lib draws each item as it wants** (Product Owner, 2026-11-24: "chaque lib interprète comme elle veut l'enum").
- A pipe has one pipe style, chosen in the synoptic; its branches have the same (a pipe is one tree, see [Junctions](junctions.md)). The base style has no colour, so a pipe always has a pipe style (assumption of the assistant, to confirm).
- A pipe style is stored in the Symbol Lib, tied to its item of `pipe_style`, and used by identifier, as a symbol is linked to its type (the rules of broken links are to be written like for symbols).

### Overriding a value of the base

- A pipe style takes four things from the base and can **override** each of them: the **linked type**, the **movement**, the **body width** and the **border width**. Example: in the plant, gas pipes are small pipes, so the "Gas" style has its own, thinner widths.
- A value that is not overridden shows the base's value in its field, and follows the base when it changes.
- Typing or choosing another value in the style overrides it, for this style only. Each value is overridden on its own.
- An overridden value has a **reset** button next to its field: a click gives back the base's value. So it is always clear which values come from the base (Product Owner, 2026-11-24).
- Overriding the linked type overrides the movement too, since its signals belong to the type: the style then picks its own signals. Resetting the type brings back the base's movement (Product Owner, 2026-11-24).
- **Nothing else can be overridden**: corners, junctions, crossings and the border position are the base's for every pipe style.

```mermaid
flowchart TD
    B["Base pipe style of the Symbol Lib: linked type, width, border, corner radius, junctions, crossings, movement; no colour, no dash"]
    B --> W["Water: blue body, grey border"]
    B --> S["Steam: white body, dashed border"]
    B --> G["Gas: yellow body, its own widths (small pipe), each with a reset"]
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

- The dashes of a pipe style **move** to show the flow. There is **no on or off option**: the direction says whether they move, set in the section Movement of the base or of the pipe style (see [Overriding a value of the base](#overriding-a-value-of-the-base)).
- **Direction**: a list of the three items of the built-in enum **pipe direction** of Metadata (see [Built-in enums](../../metadata/draft.md#built-in-enums)): stopped, from the start of the pipe to its end, or from the end to its start. A **small icon inside the field** picks instead **one signal** of the linked type, of that enum, as for the speed (Product Owner, 2026-11-24). There is no second signal "moving or not".
- **Speed**: a number field where a fixed value is typed, with a **small icon inside the field** that picks a signal of the linked type instead, as for the bounds of a signal in Metadata (decision 0041). There is no choice "fixed or signal" beside the field. The fixed value can always be typed (Product Owner, 2026-11-24).
- The section Movement is **always shown**, even without a linked type: a fixed direction and a fixed speed move the dashes of a plain pipe. Without a type, the signal icons of the two fields are greyed (Product Owner, 2026-11-24).
- **Propagation**: where a branch leaves the pipe (a junction), the movement goes on into the branch, following the flow: the whole tree is one flow. The pipe is no longer a plain drawing: it behaves half like a symbol.
- The unit of the speed is open.
- Assumption of the assistant, to confirm: the movement can be stopped by a global setting and by the system setting "reduce motion" (advised by the research).

```mermaid
flowchart LR
    L["Value chosen in the list"] --> D{"Direction"}
    T["Linked type"] -->|"or a signal, enum pipe direction"| D
    D -- "Stopped" --> X["Dashes still"]
    D -- "Start to end" --> F["Dashes move forward"]
    D -- "End to start" --> R["Dashes move backward"]
    V["Speed: a fixed value, or a signal of the type picked in the field"] --> F
    V --> R
```

### Linked type

- The base pipe style and each pipe style **can** be linked to a type of Metadata, in their first section. Putting the type on the base or on each style is the user's choice (Product Owner, 2026-11-24): a pipe style takes the base's type unless it overrides it, with a reset to go back to it (see [Overriding a value of the base](#overriding-a-value-of-the-base)).
- A style with no type, neither its own nor the base's, is a drawing: its dashes move only by the fixed values of the section Movement, and nothing else changes with the model.
- Linked to a type, the style is animated by the model, like a symbol with a type (see [Animation mode](../08-animation-mode/README.md)):
  - the **direction** and the **speed** of the moving dashes, through the signals picked in the section Movement (above);
  - the **colours** (body, border) change with what happens; the fills are those of each pipe style, even when the type is the base's;
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

### The enum pipe_style

Decision 0099 (Product Owner, 2026-11-24: "faut juste dire que les pipe style, ça suit un truc d'enum global").

- **The kinds of pipe follow a built-in enum of Metadata, `pipe_style`**: a **global** enum, one list for the whole application, never a template (see [Built-in enums](../../metadata/draft.md#built-in-enums)).
- **Each item is a kind of content**: a key, a display name and a description, written in the enum, not in the pipe style.
- **Each Symbol Lib gives each item its own look**: its pipe style for that item (fills, overridden widths, type, movement). Two Symbol Libs can draw "Oil" differently.
- **It ships with no base item** (Product Owner, 2026-11-24). At its very first start, the software writes in the user's configuration a copy of `pipe_style` holding **Water** alone, never written again: Water is the user's item, which they change or delete as they want (see [The default copy of pipe_style](../../metadata/draft.md#the-default-copy-of-pipe_style)).
- **It can never be deleted**; the user **adds items** to it from the interface, as to every built-in enum (see [Overriding a built-in enum](../../metadata/draft.md#overriding-a-built-in-enum)).
- **A signal of a type can point to it**, like any enum: a signal "content" says which kind of fluid a symbol or a pipe holds.
- What for (Product Owner): a symbol of the library can have pipe inlets and outlets of its own, drawn with the look of the chosen item: "ça sera tel signal, qui sera le type de fluide [...] et j'utilise telle propriété de l'enum, en fonction de ce qui a été choisi."

On the Pipes page (Product Owner, 2026-11-24):

- **The list of pipe styles shows every item** of `pipe_style`, in the order of their keys (assistant's reading).
- **No + on the list**: items are never added from the Pipes page. In its place, a **small link opens the enum `pipe_style` on the Enums page of Metadata**, where items are added, so that it is clear where they come from.
- **The key, the display name and the description of the item are read-only in the pipe style**: they are changed in Metadata only. There is no name field.

The assistant's reading, to confirm:

- **An animation of a symbol** can pick a signal of the enum `pipe_style`, then a property of the pipe style of this library for the chosen item (body fill, border fill), as it picks a column of an enum (see [Enums of a Symbol Lib](../11-enums-of-a-symbol-lib.md#used-by-an-animation)).

```mermaid
flowchart LR
    E["Built-in enum pipe_style, global: no base item, the items of the user (Water by default)"] --> P1["Symbol Lib Plant A: its look for each item"]
    E --> P2["Symbol Lib Plant B: another look for the same items"]
    S["Signal of a type, of the enum pipe_style: the content"] --> A["Animation of a symbol: a property of the pipe style of the chosen item"]
    P1 --> A
```

### Corner radius

- The user draws a pipe with straight segments only: click, click, click.
- The corner radius rounds each angle of the pipe. A right angle then gets a curve, which makes the pipe a little more stylised.
- With a radius of 0, the angles stay sharp.
- It is set once, in the base style, and is the same for every pipe style: different radii side by side would look odd.
- The radius also decides the look of the bridges at crossings (see [Crossings](crossings.md)).
- It is the only setting of the angles: there is no path kind (straight, right angles, rounded) to choose on each pipe.

## Example

Base style of the library "Plant A": linked type `fluid_line`; width 6 px; border 1 px, outside; corner radius 8 px; junction circle 12 px; crossing bridge; direction `flow_direction`, speed 40 (fixed).

Each line is the look "Plant A" gives to an item of `pipe_style`, items the user added (keys of the example).

| Item of pipe_style | Linked type | Fills | Movement | Own widths |
| --- | --- | --- | --- | --- |
| 0: Water | Base's | Body blue; border dark grey. | Base's (a plain fill: nothing moves) | — |
| 1: Steam | Base's | Body white; border dashes: grey 4, transparent 4. | Base's | — |
| 2: Oil | Own: `oil_line` | Body dashes: black 10, transparent 20, red 2; border dark grey. | Own: direction `flow_direction`, speed `flow_speed` | — |
| 3: Gas | Base's | Body yellow; border dashes: black 10, transparent 20, red 2. | Base's | Body 3 px, border 0.5 px (small pipes), each with its reset |
| 5: Electricity | Own: `power_line` | Body yellow; border yellow. | Own: direction `current_direction`, speed 20 (fixed) | Body 2 px |

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

- Which properties of a style a signal can drive, beyond the speed, the direction and the colours?
- In which unit is the speed of the moving dashes set (pixels per second)?
- A pipe linked to a type is one tree, one flow: do its branches share its values (assistant's reading), or can a branch have its own (a closed valve on one branch, stopping the movement downstream)?
- Can a style hold several layers (the body, then a border, then a second line), or just the options above?
- [The enum pipe_style](#the-enum-pipe_style):
  - An item that a Symbol Lib has not styled yet (just added, or added from another library): how is a pipe of that item drawn?
  - Which properties of a pipe style an animation of a symbol can take (body fill, border fill, widths)?
  - Can a signal of the model choose the pipe style of a pipe in the synoptic?
