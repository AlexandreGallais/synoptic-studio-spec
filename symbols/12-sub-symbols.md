# Sub-symbols

> [Home](../README.md) › [Symbols](README.md) › Sub-symbols · Previous: [Enums of a Symbol Lib](11-enums-of-a-symbol-lib.md)

Status: draft, from the Product Owner's description of 2026-11-18 and his answers the same day (the changes of the parent reach the sub-symbols; a sub-symbol only adds; its type is the parent's or a sub-type of it). Not validated. Open points are listed in [Open questions](#open-questions).

A symbol can have a **parent symbol**, as a type of Metadata has a parent type (see [Types](../metadata/01-types.md)). A **sub-symbol** starts from everything made for its parent, and the user adds more on top of it (Product Owner, 2026-11-18: "t'as un symbole parent et tu peux créer un sous-symbole [...] ça prend [ce] qui a été fait pour le symbole, et tu peux rajouter [...] en plus").

## Rules

- A symbol can be created as a sub-symbol of another symbol: its parent.
- A sub-symbol takes what was made for its parent symbol, then the user adds to it: shapes, and the links of these shapes to the signals and commands (Product Owner, 2026-11-18).
- A sub-symbol can itself have sub-symbols: the example below has three levels (Product Owner, 2026-11-18).
- **The changes of the parent reach its sub-symbols** (Product Owner, 2026-11-18): a sub-symbol is linked to its parent, never a copy made once. The valve is corrected once, and the motorised valve and the motorised valve with command follow. It is the inheritance of Metadata, applied to symbols.
- **A sub-symbol only adds** (Product Owner, 2026-11-18): what it takes from its parent is read only in it, as the inherited signals of a type are (see [Signals](../metadata/04-signals.md#the-table-of-signals)). It cannot change it, move it or hide it. To change it, the user opens the parent.
- **Its type is the type of its parent, or a sub-type of it** (Product Owner, 2026-11-18). So the animations and interactions taken from the parent keep their signals and commands. In the example, the motorised valve with command can have a sub-type of the valve's type that adds the commands open and close.
- Assistant's reading, to confirm: the dictated message says "ça prend l'IA qui a été faite pour le symbole"; "l'IA" is read as what was made for the symbol, its drawing and what is linked to it.

```mermaid
flowchart TD
    P["Parent symbol: drawing, animations, interactions"] -->|"linked: a change reaches the sub-symbol"| S["Sub-symbol"]
    S --> R["What it takes: read only"]
    S --> A["What it adds: shapes, animations, interactions"]
    T["Type of the parent"] -->|"same type, or a sub-type"| S
```

## Example

The Product Owner's example (2026-11-18): each level is the one above, plus what it adds.

| Symbol | Parent | What it adds |
| --- | --- | --- |
| Valve | none | The drawing of the valve. |
| Motorised valve | Valve | A small square with an M inside. |
| Motorised valve with command | Motorised valve | Two buttons: open and close, linked to the commands of its type. |

```mermaid
flowchart LR
    V["Valve"] --> M["Motorised valve: + a small square with an M"]
    M --> C["Motorised valve with command: + two buttons, open and close"]
```

## Where it is used

| Thing | Created and changed in | In a symbol | In a synoptic |
| --- | --- | --- | --- |
| Parent of a symbol | Symbol mode | Choose at creation (how: open) | To settle (part 3) |

## Open questions

- The list of symbols of a Symbol Lib is flat, never a tree (decided on 2026-11-11). Does it become a tree, as in Metadata, or does it stay flat, the parent shown elsewhere?
- Can the parent be in another Symbol Lib?
- How a sub-symbol is created (from the list, from the parent symbol open in the editor...).
- A parent without a type: can its sub-symbol take any type? Assistant's reading: yes, since there is nothing to keep.
- What happens to a sub-symbol when its parent changes type, or loses it.
- Does a sub-symbol take the preset of its parent, and the connection points of its pipes?
- Can the parent be deleted while it has sub-symbols?
