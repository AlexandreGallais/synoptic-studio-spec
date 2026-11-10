# Presets

> [Home](../README.md) › [Metadata](README.md) › Presets · Previous: [Pop-ups](08-popups.md) · Next: [Libraries](10-libraries.md)

Status: draft, rules stated by the Product Owner on 2026-11-10. Nothing here is validated.

A preset is made under a type (example: pneumatic positive displacement pump). It saves a pop-up with its defaults, so that a symbol or a synoptic starts well configured. It stays simple: defaults, nothing more.

## What a preset holds

```mermaid
flowchart TD
    R[Preset] --> D[Default values of properties]
    R --> U[Display unit for each: starts as the model unit]
    R --> N[Decimal places for each: start as the Units page default]
    R --> V[Pop-up entries shown by default]
```

## Rules

- A type needs at least one preset to be chosen in a symbol or a synoptic. No preset is created automatically. If no preset fits, the user creates one in Metadata.
- Unticked pop-up entries are only unticked at the start, to save time. In a symbol or a synoptic the full list is still there and the user can tick them by hand.
- A preset does not choose commands: all the commands of the type stay available. The symbol says which it uses.
- Default values, display units and decimal places are first set in the preset, in Metadata.
- Default display unit: the unit the model uses for the property (its model unit). If the model works in litres, the preset starts with litres. The user changes it in the preset only when another unit is wanted.
- Decimal places: they start from the number set for the category on the Units page (see [Units](05-units.md)). The preset overrides it only if needed.
- Decimal places never go to the model: they are display only. The display unit does not change the model value either.
- In a symbol or a synoptic, the user chooses a preset, then can edit its default values, display units and decimal places there. Example: to see a green pump, the user sets the default colour in the symbol.

```mermaid
sequenceDiagram
    actor U as User
    participant MD as Metadata
    participant SY as Symbol
    participant SN as Synoptic
    U->>MD: creates a preset (defaults, units, entries shown)
    U->>SY: chooses the preset
    U->>SY: edits a default value or a display unit
    U->>SN: chooses the preset
    U->>SN: edits a default value or a display unit
```

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Preset | Metadata, under a type | Symbol and synoptic start from it | Choose one | Choose one |
| Default value, display unit, decimal places, entries shown | Preset, in Metadata | Pop-up of the symbol or synoptic | Edit | Edit |
