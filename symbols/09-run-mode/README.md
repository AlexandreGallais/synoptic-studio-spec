# Run mode

> [Home](../../README.md) › [Symbols](../README.md) › Run mode · Previous: [Animation mode](../08-animation-mode/README.md) · Next: [Open questions](../10-open-questions.md)

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

The mode of the [editor](../03-editor/README.md) in which the user tries the symbol without a model: they give values to the signals that animate it, and see it move. Only symbols with a type have it.

## Rules

- Tool bar: [Hand](../03-editor/hand.md) only. Right-hand panel: the test values, and the simulated screen.
- There is no model. The Run mode is simply a mode with a menu on the right (or elsewhere) that lists all the output signals of the model that animate the symbol. What the model does does not matter: the mode only shows what can happen.
- The user gives each signal a value (see [Signals](../../metadata/draft.md#signals)). A signal has no bounds of its own since 2026-11-17: a bound is a plain signal, given a value like the others.
- Since a bounded linear animation can take its minimum or its maximum from an input signal (Product Owner, 2026-11-17, see [Animation mode](../08-animation-mode/README.md#the-input-range-of-a-bounded-linear-animation)), the list also shows **the signals used as a minimum or a maximum**, inputs included: without a test value for them, the animation could not be tried. Assistant's reading, to confirm.
- The control depends on the type (decided by the Product Owner, 2026-11-11):

| Signal | Control |
| --- | --- |
| A number, for example from 0 to 1 | A number input or a slider. |
| An enum | A select of the display texts of the enum, to choose an item and see the animation that goes with it. |
| A boolean | A switch (assumed by the assistant, the Product Owner named only the two above). |

- The symbol is redrawn at each change, with the display units and decimal places of its preset.
- Nothing is sent to a model, and nothing is saved in the symbol.

### Interactions in the Run mode

- There is no real interaction, since there is no model: nothing is sent.
- When the user acts on a place of the symbol that has an interaction, the editor only **simulates** what would happen:
  - an interaction that opens the faceplate simulates the opening of the pop-up;
  - a command assigned to the place gives a line in a log of the simulation: "you clicked here, so this action would be done".
- The exact form of the log and of the simulated pop-up is not decided: the Product Owner has no precise idea yet, only the principle (see the open question).

```mermaid
flowchart LR
    U["User gives a test value"] --> S["Symbol in Run mode"]
    S --> D["Animated drawing, texts with value and unit"]
```

## Simulating another screen

The Run mode can show the symbol as it would look on another screen, which is not the edit mode's job.

- The user picks a simulated screen by its size and resolution. Example: a 24 inch 1080p screen, while working on a 27 inch 4K one.
- The editor then shows the size that screen would have, and displays the symbol at that resolution. It may zoom to do so.
- If the simulated screen is bigger than the real one (a 24 inch screen on a 16 inch laptop), the simulated screen goes beyond the window: scroll bars appear and the user moves in it.

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Run mode | Symbol editor | Checking a symbol | Use | No |

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.15, 3.16).

- Figma's prototype chains triggers and actions without running anything. Opinion of the report: the log is a list, one line per action: time, place, gesture, effect, value.
- Faceplate: a click on a value or an element opens its faceplate, which must not hide the graphic (HMI guide). Opinion: a floating window near the symbol, that can be moved.
- Screen simulation: size and resolution are not enough; opinion of the report: add the **scale factor of the system** (100 % to 200 %).
- Quality: a selector of quality per signal (good, uncertain, bad) would let the user test the quality mark (see [Animation mode](../08-animation-mode/README.md)).
- Name: nothing runs here. Opinion of the report: **Test mode** (the archived Figma file has a separate "Runtime" page).

## Open questions

- Name: Test mode, to confirm.
- The form of the simulation log and of the simulated faceplate (where the log is shown, what a line says, whether the faceplate shows the test values). See [Open questions](../10-open-questions.md).
