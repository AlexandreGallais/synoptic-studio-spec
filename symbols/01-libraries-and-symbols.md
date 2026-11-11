# Libraries and symbols

> [Home](../README.md) › [Symbols](README.md) › Libraries and symbols · Next: [Drawing](02-drawing.md)

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

Symbols are kept in Symbol Libs. As for types, a library is only a way to sort and to find. What changes from one library to another is mostly the graphics: the same pump can be drawn differently in each library.

## Rules

- Symbols are a flat list, never a tree. A Symbol Lib is a flat list of symbols.
- In symbol mode, the user first selects a Symbol Lib. The list of its symbols is then shown. Then the user opens a symbol or creates a new one.
- The two kinds of library are called **Symbol Lib** and **Type Lib** (named by the Product Owner on 2026-11-11). A Type Lib is the Metadata one (see [Libraries](../metadata/10-libraries.md)): it sorts types. A Symbol Lib sorts drawings. This page says "Symbol Lib" and "Type Lib" from here on.
- A symbol always lives in a library. There is no symbol outside a library, and a symbol lives in one library only: it cannot be in several (decided by the Product Owner on 2026-11-11).
- There is one kind of Symbol Lib. A library is a way of representing symbols, and it only has a name given by the user. It has no style, no category and no other field.
- Why several libraries: one library alone cannot be enough. Symbols used for one kind of software, or for one factory, must look one way; another software or factory needs another look. A pump is not always drawn the same way, and a symbol that exists in one library may not be needed in another.
- A library also lets a graphic representation evolve over time: when the user wants to change the look, they create another library and draw the symbols again there, instead of changing the first one.
- A symbol is static or dynamic (see [the overview](README.md)). In a Symbol Lib, the user clicks "Create a symbol" and first chooses static or dynamic.
- A dynamic symbol is attached to one type of Metadata (see [Types](../metadata/01-types.md)), which the user must choose before drawing, the way Metadata says: first a Type Lib, then one of its types (see [Libraries](../metadata/10-libraries.md)). The symbol is linked to its type from the start. Several dynamic symbols can be attached to the same type, with different drawings and different presets: a centrifugal pump can have a manual symbol and a motorised one, with no change in Metadata.
- A static symbol has no type, no preset, no faceplate, no animation and no interaction. Only the creation of the symbol and its visuals remain: the drawing (see [Drawing](02-drawing.md)).
- The user can switch a symbol between static and dynamic whenever they want, in the symbol editor. Becoming dynamic requires choosing a type then. What happens to the type, the animations and the interactions when a dynamic symbol becomes static is to settle (see [Open questions](07-open-questions.md)).
- The type of a dynamic symbol can be changed afterwards, in the symbol editor only (see [Types](../metadata/01-types.md)).

```mermaid
flowchart TD
    A["Symbol mode"] --> B["Select a Symbol Lib"]
    B --> C["Flat list of its symbols"]
    C --> D["Open a symbol"]
    C --> E["Create a symbol"]
    E --> K{"Static or dynamic?"}
    K -- "Dynamic" --> F["Choose a Type Lib, then a type"]
    K -- "Static" --> H["No type"]
    F --> G["Symbol editor"]
    H --> G
    D --> G
    G -.->|"switch static or dynamic at any time"| K
```

## Example

The names below are only names given by the user, not styles.

| Symbol Lib | Symbols | Types they use |
| --- | --- | --- |
| Plant A | Manual centrifugal pump, motorised centrifugal pump, valve, tank outline (static) | Centrifugal pump, Valve, none |
| Plant B | Centrifugal pump, valve, circuit breaker | Centrifugal pump, Valve, Circuit breaker |

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Symbol Lib | Symbol mode | Choice of a symbol | Create, select | To settle (part 3) |
| Symbol | Symbol editor | Synoptics | Create, draw, link | Placed |
| Static or dynamic | Chosen at creation, switched in the symbol editor | Symbol | Choose, switch | No |
| Type of a dynamic symbol | Chosen at creation, changed in the symbol editor | Symbol | Choose, change | No |

## Open questions

- What happens to the type, animations and interactions when a dynamic symbol is switched to static (kept hidden, or dropped)? See [Open questions](07-open-questions.md).
