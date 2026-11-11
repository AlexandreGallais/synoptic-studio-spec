# symbols

> [Home](../README.md) › Symbols

The second part of Synoptic Studio: creating symbols. A symbol is a drawing, attached to a type from [Metadata](../metadata/README.md), that can be animated by the signals of that type and that can react to clicks. It is the front side of a type: how it looks and behaves.

Status: draft, written from the Product Owner's oral description of 2026-11-11. Nothing here is validated yet. The words are provisional: the Product Owner asked to be very critical about every name before keeping it (see [Open questions](07-open-questions.md)).

## The big picture

The user picks a symbol library, sees the flat list of its symbols, and creates or opens a symbol. In the symbol editor, the user draws, then links the drawing to the type's signals (animation) and commands (interactions).

```mermaid
flowchart LR
    L["Symbol library: a flat list of symbols"] --> S["Symbol"]
    S --> D["Drawing: shapes, text, pen, layers"]
    S --> T["Type and preset, from Metadata"]
    D --> A["Animation: an output signal moves a part of the drawing"]
    D --> I["Interactions: a zone or a layer reacts to a gesture and sends a command"]
    T --> A
    T --> I
    S --> Y["Placed in a synoptic (part 3)"]
```

## Static and dynamic symbols

| Kind | What it is | Animation | Interactions |
| --- | --- | --- | --- |
| Dynamic | A symbol that is animated and stands for something of the installation. | Yes | Yes |
| Static | A symbol that may stand for something, but is not animated. | No | To settle |

In a synoptic, a dynamic symbol can be placed and left unwired: it then behaves as a static one (this belongs to part 3).

## What it contains

| Page | What it holds |
| --- | --- |
| [Libraries and symbols](01-libraries-and-symbols.md) | Symbol libraries, the flat list, creating a symbol, static and dynamic. |
| [Drawing](02-drawing.md) | The editor tools, layers, point editing, the pen and its straight-after-curve option. |
| [Type, preset and faceplate](03-type-and-faceplate.md) | The type of a symbol, its preset, which faceplate entries the symbol shows. |
| [Animation](04-animation.md) | Linking an output signal to a change of the drawing, values and units in texts. |
| [Interactions](05-interactions.md) | Interaction zones, gestures, what a gesture does. |
| [Testing](06-testing.md) | Trying the symbol with values for all the signals that animate it. |
| [Open questions](07-open-questions.md) | Every open question in one place. |

## Reading order

1. [Libraries and symbols](01-libraries-and-symbols.md), then [Drawing](02-drawing.md).
2. [Type, preset and faceplate](03-type-and-faceplate.md).
3. [Animation](04-animation.md), then [Interactions](05-interactions.md), then [Testing](06-testing.md).
4. [Open questions](07-open-questions.md).

## Page layout

Same skeleton as the Metadata pages: title and navigation line, `Status:` line, `## Rules`, detail sections, `## Example`, `## Where it is used`, `## Open questions` last and only when the page has some (each also listed in the index).

## See also

- [Metadata](../metadata/README.md): types, signals, commands, faceplates, presets. This part only uses them and never changes them.
- [Storage](../storage/README.md): how the files of symbols and symbol libraries are saved.
