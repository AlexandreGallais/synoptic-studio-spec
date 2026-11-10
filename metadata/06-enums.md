# Enums

> [Home](../README.md) › [Metadata](README.md) › Enums · Previous: [Units](05-units.md) · Next: [Commands](07-commands.md)

Status: draft, rules stated by the Product Owner on 2026-11-10. Nothing here is validated.

An Enums page lists the enums of the application, like the Units page lists the unit categories. A property of the type enum does not hold its own list of values: it points to an enum of this page.

## Rules

- An enum is a named list of values: a list of numbers or a list of strings.
- Enums are created and changed on the Enums page only, never inside a property, a symbol or a synoptic.
- A new enum goes into the list of the Enums page. The list can be filled in advance, before any property uses it.
- A property of the type enum picks one enum of the list. It is a link to the existing enum, never a copy.
- Several properties can point to the same enum.
- Changing an enum changes it for every property that points to it: that is the point of a link.

```mermaid
flowchart LR
    P["Enums page: list of named enums"] --> E1["mode: auto, manual, off"]
    P --> E2["speed: 1, 2, 3"]
    A["Property mode of a pump"] -->|"link"| E1
    B["Property mode of a valve"] -->|"link"| E1
    C["Property gear of a motor"] -->|"link"| E2
```

## Steps

```mermaid
flowchart LR
    A["Create an enum on the Enums page"] --> B["Add its values"]
    B --> C["On a property of type enum, pick the enum"]
    C --> D["The property follows the enum: no copy"]
```

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Enum, its values | Enums page | Property: picks one as a link | No | No |

The pop-up chooses how an enum is shown (radio on one line, radio on several lines, select...), see [Pop-ups](08-popups.md).
