# Properties

> [Home](../README.md) › [Metadata](README.md) › Properties · Previous: [Documentation](03-documentation.md) · Next: [Units](05-units.md)

Status: draft, rules stated by the Product Owner on 2026-11-10. Nothing here is validated.

A property is a signal between the front and the model: an input or an output of the model. Only these are defined here. Metadata is the contract with the model: what is negotiated with the model author is written here. Only inputs and outputs exist: no separate constant parameters, and no display label apart from the name (the research notes that FMI has parameters and OPC UA has a display name; the project keeps neither). Transforming data (for example mapping a value to a 0 to 1 range for an animation, proportionally or not) is not done here: it belongs to symbol editing. Properties that stay inside the model are not defined in Metadata: the people who write the model name them as they wish, and they are invisible to the application.

## Rules

- No default value on a property: default values live in presets only (see [Presets](09-presets.md)).
- Properties are inherited along the tree: "Pneumatic positive displacement pump" has the properties of Pump, of Positive displacement pump and of its own.
- Properties are created and changed in Metadata only, never in a symbol or a synoptic.
- A property's name is part of the model's interface definition: it is set once and is not meant to change. Renaming one is breaking for models, as for types (see [Types](01-types.md)). It is done the same way: Edit button, change, Save button, with no warning.

## Fields

| Field | Meaning | Rule |
| --- | --- | --- |
| Name | The property's name. | It is also its variable identifier. No second label. |
| Type | What kind of value. | Integer, real, boolean, text or enum (decided on 2026-11-11). A real is a 64-bit double. |
| Enum | For an enum: the list of values. | An enum picked from the Enums page (see [Enums](06-enums.md)). A link to it, never a copy, and never defined in the property. |
| Unit category | What the value measures (volume, flow, pressure...). | Picked from the Units page (see [Units](05-units.md)). Only for numbers. |
| Model unit | The unit in which the model handles the value. | By default the model unit of the category. Can be overridden here with another unit of the same category. |
| Minimum, maximum | Bounds of a number. | Metadata of the property, indicative, written in the model unit (decided on 2026-11-11). They are the zone the model is designed for, not a guarantee. They do not block anything in the data model; whether the pop-up warns or blocks an input outside them is a pop-up matter. |
| Direction | Input or output of the model. | Belongs to the property. |

```mermaid
classDiagram
    class Property {
        name
        type
        enum
        unit category
        model unit
        minimum
        maximum
        direction in or out
    }
    class UnitCategory
    class Enum
    Property ..> UnitCategory : category
    Property ..> Enum : link
```

## Example

| Name | Type | Enum | Unit category | Min | Max | Direction |
| --- | --- | --- | --- | --- | --- | --- |
| `running` | boolean |  |  |  |  | input |
| `flow` | number |  | flow | 0 | 500 | output |
| `mode` | enum | `operating_mode` (auto, manual, off) | none |  |  | input |

In the list of properties, an enum property shows its type and, next to it, the enum it points to with its values, so the user sees at a glance which enum was chosen.

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Property (name, type, enum, unit category, model unit, bounds, direction) | Metadata | Pop-up entries, commands that set it, preset default values | No | No |
