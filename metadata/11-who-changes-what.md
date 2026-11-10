# Who changes what, and where

> [Home](../README.md) › [Metadata](README.md) › Who changes what · Previous: [Libraries](10-libraries.md) · Next: [Open questions](12-open-questions.md)

Status: validated by the Product Owner on 2026-11-11. Open points are listed in [Open questions](12-open-questions.md).

Rule of the Product Owner: no duplicate ways to change the same thing. Each thing has one place where it is created and changed.

| Thing | Created and changed in | In a symbol | In a synoptic |
| --- | --- | --- | --- |
| Library | Metadata | Choose a library, then one of its types | No |
| Type (name, parent, icon) | Metadata, General | Choose its type (only here) | No |
| Type documentation | Metadata | No | No |
| Signal | Metadata | No | No |
| Quantity, families, reference family, conversions, default model unit, default decimals | Units page | No | No |
| Model unit of a signal (override of the quantity's default) | Signal, in Metadata | No | No |
| Enum and its values | Enums page | No | No |
| Command | Metadata | Link a command to a click | No |
| Faceplate | Metadata | Tick or untick entries | Tick or untick entries |
| Faceplate title and description | Synoptic only | No | Write them, on each placed symbol |
| Preset | Metadata | Choose one | Choose one |
| Default value, display unit, decimal places, name and description of a signal | Preset, in Metadata | Edit | Edit |

```mermaid
flowchart LR
    M[Metadata] -->|"types, signals, commands, faceplates, presets, libraries"| S[Symbol]
    S -->|"choose a preset, edit defaults, display units, names and descriptions, link a command to a click, tick faceplate entries"| Y[Synoptic]
    Y -->|"choose a preset, edit defaults, display units, names and descriptions, tick faceplate entries"| Y
```

## Details

- Types: [Types](01-types.md), [Icons](02-icons.md), [Documentation](03-documentation.md).
- Model side: [Signals](04-signals.md), [Units](05-units.md), [Enums](06-enums.md).
- Front side: [Commands](07-commands.md), [Faceplates](08-faceplates.md), [Presets](09-presets.md).
- Use: [Libraries](10-libraries.md).

Each page also has its own "Where it is used" table, the detail of the table above. When one changes, the other must change too.
