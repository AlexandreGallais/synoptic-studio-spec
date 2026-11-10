# Commands

> [Home](../README.md) › [Metadata](README.md) › Commands · Previous: [Enums](06-enums.md) · Next: [Faceplates](08-faceplates.md)

Status: validated by the Product Owner on 2026-11-11. Open points are listed in [Open questions](12-open-questions.md).

A command is how the front acts on the model. Two kinds, kept apart because they do not say the same thing.

| Kind | Meaning | What the user edits |
| --- | --- | --- |
| Set a signal | "This signal must take this value". | The signal targeted, and how the value is given: fixed (set in Metadata) or typed (see below). |
| Trigger | "This happened, deal with it". | Its name only. It targets nothing: the model decides what to do. |

```mermaid
flowchart TD
    C[Command] --> S[Set a signal]
    C --> E[Trigger]
    S --> F[Fixed value]
    S --> T[Typed value, number only]
    E --> N[A name, no target]
```

## Rules

- Commands are created and changed in Metadata only.
- In a symbol, direct commands: the user links a command from Metadata to a click on a part of the symbol.
- On the web front, a command is a button and nothing else (to check against the typed-value command below).
- A preset does not choose commands: all the commands of a type stay available. The symbol says which it uses.

## Set a signal, fixed value

Example: the command `start`, when the user clicks a zone of the symbol, sets the signal `running` to `true`. The user edits the value sent.

```mermaid
sequenceDiagram
    actor U as User
    participant S as Symbol (front)
    participant M as Model (back)
    U->>S: clicks the zone linked to "start"
    S->>M: for this symbol, running = true
    M-->>S: running = true (an output of the model)
    S-->>U: the symbol is redrawn
```

## Set a signal, typed value

On a number signal, an input appears and the person types the value to send, instead of a fixed one. Such a command is not necessarily tied to a click on the symbol: it can also live in a faceplate. The typed value follows the same checks as any typed value: bounds, conversion back to the model unit and rounding (see [Faceplates](08-faceplates.md) and [Units](05-units.md)).

```mermaid
sequenceDiagram
    actor U as User
    participant F as Front
    participant M as Model (back)
    U->>F: triggers the command
    F-->>U: an input appears
    U->>F: types 120
    F->>M: setpoint = 120
```

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Command (set a signal, trigger) | Metadata | Faceplate entry, click on a part of a symbol | Link a command to a click | No |

## Open questions

- On the web, what does a typed-value command do? Proposal: a button that opens a small input. It is also listed in [Open questions](12-open-questions.md).
