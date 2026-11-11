# Libraries and symbols

> [Home](../README.md) › [Symbols](README.md) › Libraries and symbols · Next: [Drawing](02-drawing.md)

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

A **Symbol Lib** holds symbols. A **Type Lib** (see [Libraries](../metadata/10-libraries.md)) holds types. This page is about the Symbol Lib, how a symbol is created, and what happens when Metadata changes.

## Rules

### Symbol Lib

- It is a flat list of symbols, not a tree.
- It has a name and a Type Lib. Nothing else.
- Every symbol is in one Symbol Lib, and only one. No symbol lives outside a library.
- In symbol mode, the user selects a Symbol Lib, sees its symbols, then opens one or creates one.
- Why several Symbol Libs: a software or a factory needs its own look for the same objects. To change a look over time, the user creates a new Symbol Lib instead of editing the old one.

### Type Lib of a Symbol Lib

- The user links the Symbol Lib to one Type Lib when creating it.
- In this Symbol Lib, only the types of that Type Lib can be chosen.
- The user can change the Type Lib later: they click the Symbol Lib and change its Type Lib.
- One Type Lib can serve several Symbol Libs.
- Changing it can break every symbol of the Symbol Lib. If the new Type Lib has exactly the same types, nothing breaks.
- Why: types are global in Metadata, and each project can have its own Type Lib. The link avoids choosing a Type Lib at every symbol. A pump is the same in Metadata wherever it is used.

### Creating a symbol

"Create a symbol" first asks: static or dynamic?

|  | Dynamic | Static |
| --- | --- | --- |
| Type | Required, chosen before drawing, among the types of the Type Lib | None |
| Preset, faceplate, animation, interaction | Yes | None |
| What the user does | Draws, then links the drawing to the type | Draws only (see [Drawing](02-drawing.md)) |

The user can switch between static and dynamic at any time.

### Static to dynamic and back

- Dynamic to static hides everything linked to the type (type, preset, faceplate entries, animations, interactions). Nothing is deleted.
- Static to dynamic brings it all back, with the same type. A mistake costs nothing.
- The user chooses a type again only if the old one was deleted in Metadata, or if the symbol was never dynamic.

### When Metadata changes

- **A rename** is followed. The symbol is linked by identifier, not by name, so it keeps working and nothing is asked.
- **A change of interface** can break a link: what it points to is gone, or can no longer be used the same way. Example: a signal goes from number to string. This also happens when the Type Lib of the Symbol Lib is changed. The full list of what breaks a link is to write (see below).
- **A broken item** is shown as broken, with a small red mark. How it looks is for the design, later. It may say why, later too. The animation itself is not changed: it just cannot work the same way any more.
- **Fixing it**: there is no tool and no automatic repair. The item only warns that it is broken, and the user redoes the mapping properly, on the symbol side, never in Metadata.

```mermaid
flowchart TD
    A["Select a Symbol Lib (linked to a Type Lib)"] --> B["Create a symbol"]
    B --> C{"Static or dynamic?"}
    C -- "Dynamic" --> D["Choose a type of the Type Lib"]
    C -- "Static" --> E["No type"]
    D --> F["Symbol editor"]
    E --> F
    F -.->|"switch at any time"| C
```

## Example

| Symbol Lib | Type Lib | Symbols |
| --- | --- | --- |
| Plant A | Hydraulics | Manual centrifugal pump, motorised centrifugal pump, valve (dynamic), tank outline (static) |
| Plant B | Electricity | Circuit breaker, transformer (dynamic) |

## Where it is used

| Thing | Created and changed in | In a symbol | In a synoptic |
| --- | --- | --- | --- |
| Symbol Lib and its Type Lib | Symbol mode | Create, select | To settle (part 3) |
| Static or dynamic | Symbol editor | Choose, switch | No |
| Type of a dynamic symbol | Symbol editor | Choose, change | No |

## Open questions

- Does a Symbol Lib of static symbols need a Type Lib?
- The complete list of changes that break a link, to write in these specs.

Both are in [Open questions](07-open-questions.md).
