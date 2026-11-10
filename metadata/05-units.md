# Units

> [Home](../README.md) › [Metadata](README.md) › Units · Previous: [Properties](04-properties.md) · Next: [Enums](06-enums.md)

Status: draft, rules stated by the Product Owner on 2026-11-10. Nothing here is validated.

A Units page lists unit categories (mass, volume, flow, pressure...), created by the user.

## Rules

```mermaid
flowchart TD
    Cat[Category] --> Fam[Family: a table of units]
    Cat --> Model[Default model unit]
    Cat --> Dec[Default decimal places]
    Fam --> Unit[Unit with its ratio inside the family]
    Fam -- "formula, one per direction" --> Fam2[Another family]
```

- A category holds one or more unit families.
- A family is a table of units, like the school ladder: kilogram, hectogram, decagram, gram, decigram, centigram, milligram. Each unit has its ratio to the others in the family.
- A category can hold several families. Example: category "mass" has the family "gram" (the metric ladder) and the family "pound" (pound, ounce...).
- Each category has a reference family. Every other family is converted to it and from it, never pairwise (decided by the Product Owner on 2026-11-11). Formulas are not limited to a factor, so cases like temperature are covered. See "Conversions only inside a category".

```mermaid
flowchart LR
    subgraph Mass[Category: mass]
        subgraph G[Family: gram]
            kg[kilogram] --- g[gram] --- mg[milligram]
        end
        subgraph P[Family: pound]
            lb[pound] --- oz[ounce]
        end
        G -- "formula A to B" --> P
        P -- "formula B to A" --> G
    end
```

## Model unit and display unit

- The Units page gives each category a default model unit. Example: category "volume", default model unit centilitre.
- A property takes a category, not a unit: a property is "volume", not "m³/h". By default it uses the model unit of its category.
- A property can override it: in its definition, the user picks another unit of the same category as the model unit of that property. The model then handles this property in that unit.
- So the model unit is not one for all models: the category gives the default, the property can change it.
- A display unit is any unit of the same category, in any family. It is chosen in a pop-up, then in a preset, and can be edited in a symbol or a synoptic.
- The value is converted for display only. The model value stays the same.

```mermaid
flowchart TD
    C["Units page: category volume, default model unit cL"] --> P1["Property flow_in: no choice, model unit cL"]
    C --> P2["Property tank_level: overrides, model unit L"]
    P1 --> D["Display unit: chosen in pop-up, preset, symbol, synoptic"]
    P2 --> D
```

```mermaid
sequenceDiagram
    participant M as Model (centilitres)
    participant F as Front
    participant U as User
    M->>F: volume = 250 (cL)
    F->>F: convert cL to L for display
    F-->>U: 2.5 L
```

## Conversions only inside a category

A conversion only exists between two units of the same category: kilograms to pounds, never kilograms to volts.

The documentary research (2026-11-10) answers which function is needed: no single one. Four closed forms cover the useful cases, and a pair of free expressions covers the rest.

| Form | Going | Back | Example |
| --- | --- | --- | --- |
| Proportional | y = a·x | x = y / a | kilogram and pound |
| Affine | y = a·x + b | x = (y − b) / a | Celsius, Fahrenheit |
| Inverse | y = a / x | x = a / y | L/100 km and miles per gallon |
| Logarithmic | y = k·log(x / x₀) | x = x₀·base^(y / k) | decibel, pH |
| Other, one value | y = f(x) | x = f⁻¹(y) | slope in % = 100·tan(angle) |

All of it stays in pure JavaScript.

### Decided on 2026-11-11

- Each category has a reference family. Families convert to it and from it, not pairwise: 4 families need 6 formulas instead of 12, and two formulas cannot contradict each other.
- A conversion is one of the closed forms. A pair of free expressions, going and back, is the last resort. The application checks that the pair is a round trip.
- The application needs a good stock of ready-made units from the start. Whether it ships a catalogue (and under which licence: UCUM, QUDT, CLDR) is open.

The following were validated on 2026-11-11 by the Product Owner, who asked for the choice that makes the most sense from the research.

- The user types a value in the display unit, so the back conversion (display unit to model unit) is also needed. The model value is still the only one stored.
- A temperature and a temperature difference are not converted the same way: 25 °C is 77 °F, but a difference of 25 °C is a difference of 45 °F (a heating rate in °C/min is a difference). A difference is its own category ("temperature difference"), with its own units and a proportional conversion. This needs no new mechanism, and it keeps the rule that a conversion only exists inside a category.
- Unit names carry their variant (US gallon, thermochemical calorie), because one name hides several values.
- Units are flat: "m³/h" is one unit with its own factor, nothing is deduced from its parts.
- When a conversion is not defined (logarithm of zero), the display says so instead of showing a wrong number.
- Floating point does not round-trip exactly (12 997 of 100 000 values do not come back unchanged from °C to °F to °C): display rounding hides it. A value typed in the display unit is converted back to the model unit, then rounded to 12 significant digits before it goes to the model, which removes the floating-point noise (100.03999999999999 becomes 100.04) and keeps the real precision of a 64-bit double (about 15 digits).

## Decimal places

- Decimal places are the number of decimals shown for a value. They are a display matter only.
- The Units page gives a default number of decimals per category. It is the global setting: one choice, applied everywhere, which suits a company that wants the same display for all.
- The preset can override it for each property, next to its display unit (see [Presets](09-presets.md)). It keeps a minimum of flexibility.
- The symbol and the synoptic can edit it from the preset, like the display unit.

```mermaid
flowchart LR
    U["Units page: default decimals per category"] -->|"applies unless overridden"| P["Preset: decimals per property"]
    P -->|"editable"| S["Symbol and synoptic"]
```

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Category, families, formulas, default model unit, default decimals | Units page | Property (category, model unit), pop-up and preset (display unit, decimals) | No | No |
| Display unit, decimal places | Pop-up, then preset in Metadata | Pop-up entry | Edit | Edit |
