# Animation mode

> [Home](../../README.md) › [Symbols](../README.md) › Animation mode · Previous: [Interaction mode](../07-interaction-mode/README.md) · Next: [Run mode](../09-run-mode/README.md)

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

The mode of the [editor](../03-editor/README.md) in which the signals are linked to the drawing. Animating a symbol means that the value of a signal changes a part of the drawing. The change of scale or of range (0 to 1 turned into 0 to 90 degrees) is done here, not in Metadata: Metadata only states the contract with the model (see [Signals](../../metadata/04-signals.md)).

## Rules

- Tool bar: [Select](../03-editor/select.md) and [Hand](../03-editor/hand.md). Right-hand panel: the animations of the selected part.
- The user selects a signal, then says what it animates: a shape, a layer, a text.
- Only the output signals of the type are offered for an animation. An output is what the model sends, and the model computes what the symbol shows. An input is what the model receives and is never animated.
- A value ordered and a value obtained are two signals for the model. Example: `opening_order` (input, what the user asks) and `opening` (output, what the model computes). The symbol animates `opening`. The faceplate can show both (see [Faceplates](../../metadata/08-faceplates.md)).
- Only a dynamic symbol has animations. A static symbol has none, and no signal to animate, since it has no type.

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
| Enum | `mode` | To settle: a look per value. |

The properties of a part of the drawing that an animation can drive (rotation, position, size, colour, opacity, visibility, blinking...) are to list.

## Texts: value and unit

A text of the symbol can be linked to a signal that has a quantity (a volume, a flow...).

- The text shows the signal's value, converted to the display unit and rounded to the decimal places set in the preset (see [Units](../../metadata/05-units.md)).
- The user chooses whether the text shows the unit or not.
- Another text can hold only the unit of the signal, in the display unit. This lets the user put the value in one place and the unit in another, and the unit follows the display unit.

```mermaid
flowchart LR
    S["Signal: flow, model unit L/s"] --> V["Text 1: the value, in the display unit"]
    S --> U["Text 2: the unit only, in the display unit"]
```

### A text that becomes an input

Decided by the Product Owner (2026-11-11). A text can be set at the size the user needs, and it can turn into an input when the user clicks it, if a command is linked to it (see [Commands](../../metadata/07-commands.md), the display that becomes an input). It makes quick commands: no separate panel is opened.

| What the text shows | What a click does |
| --- | --- |
| A number | The text turns into a **number input**, right there. This is the main case. |
| A text | The text can turn into a **text input**. Less common than the number. |
| An enum | A **selection menu** opens, with the whole list of the enum, and the user picks one item. |

- The user chooses, in the editor, which of these a text does: number input, text input, or selection menu.
- The enum case works on the value or on the string shown: a click on it opens the menu.
- What the user picks or types is sent as a command of the type, like any other command.

```mermaid
flowchart LR
    T["Text shown"] -->|"number: click"| N["Number input"]
    T -->|"text: click"| X["Text input"]
    T -->|"enum: click"| M["Menu with the whole list"]
    N --> C["Command sent to the model"]
    X --> C
    M --> C
```

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Animation (signal, target, mapping) | Symbol editor | Symbol | Create, edit | No |
| Text linked to a value or to a unit | Symbol editor | Symbol | Create, edit | No |

## Open questions

- The list of animatable properties, the shapes of mapping (linear or not), animation of an enum: left to the assistant's next research (question 7 of the [research brief](../research-brief.md)). See [Open questions](../10-open-questions.md).
