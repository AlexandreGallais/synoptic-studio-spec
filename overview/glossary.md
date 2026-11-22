# Glossary

> [Home](../README.md) › [Overview](README.md) › Glossary

Each word of Synoptic Studio, its one meaning, the name it has in the files, and the words not to use for it: one glossary for the whole specification, so that a word keeps one meaning in every part. The words of Metadata were written by the assistant on 2026-11-22, at the Product Owner's request, from the [Data model](../metadata/data-model.md), the [entities](../metadata/entities/README.md) and the research reports T2 and T5; those of the other parts are added as each part is written again. Nothing here is validated. A word to avoid gives its reason and its source; "Analysis" marks the assistant's own reason.

## Metadata

### The type and what it holds

| Word | Meaning | In the files | Not to use |
| --- | --- | --- | --- |
| **Type** | What a symbol represents, at one level of detail: a pump, a centrifugal pump. Types form a tree. | `TYPE`, `<id>.type.json` | Template: the word of AutomationML for a type (T2, 3.12). Type Lib: removed on 2026-11-16. |
| **Parent**, **sub-type** | The type a type inherits from, set when it is created and never changed; a sub-type inherits the signals, the commands, the flags and the appearance of its parents, and starts with a copy of their presets (see [Inheritance of types](../metadata/inheritance.md)). | `TYPE.parent` | — |
| **Signal** | A value that goes between the front and the model, as an input or an output. | `SIGNAL` | Property: a metadata in OPC UA, a visual attribute on the front. Variable: too general (FMI). Tag: a controller address, a data point in supervision (T2, 3.12; T5). |
| **Input**, **output** | The direction of a signal: the model receives an input, and sends an output. | `SIGNAL.direction`: `input`, `output` | — |
| **Command** | What the front sends with one click: a fixed value to an input, an override of an output, or a trigger. | `COMMAND` | Control: an element of an interface; in French, « contrôle » means a check (T2, 3.12). |
| **Trigger** | A command that tells the layer above the model that an action happened; it never goes to the model. | `command_kind`: `trigger` | Event: in OPC UA and FMI, an event goes out of the system; on the front, it names the events of the browser (T2, 3.12). |
| **Override** | To replace the value of an output by another: a fixed value sent by a command, or a value typed in the faceplate. | `command_kind`: `override_output_signal`; `access`: `override` | — |
| **Flag** | A key each placed symbol of a type has on or off, written in the configuration files for a program outside. | `FLAG` | — |
| **Documentation** | What explains a type to people: a description in Markdown and links. | `DOCUMENTATION`, `LINK` | — |
| **Appearance** | The icon and the color a type shows, copied when picked; empty, those of its parent. | `APPEARANCE` | — |

### The preset and the faceplate

| Word | Meaning | In the files | Not to use |
| --- | --- | --- | --- |
| **Preset** | The defaults a symbol and a synoptic start from: how each signal of the type starts and is shown, and the faceplate. | `PRESET` | Profile: conformance in OPC UA. Template: the type in AutomationML, and a kind of enum here. Configuration: too general (T2, 3.12). |
| **Start value** | The value the model gets when it starts, also shown before the model sends anything. | `PRESET_VALUE.start_value` | Default value: its name until 2026-11-22; `start` is the word of FMI (T5). |
| **Display format** | The unit and the decimals a preset shows a number with. | `DISPLAY_FORMAT` | — |
| **Faceplate** | The panel a preset builds for a type, made of signal fields, command buttons, titles, paragraphs and groups. | `FACEPLATE_ELEMENT` and its parts | Pop-up: a form, not an object. Inspector: kept for the panel of the editor. Panel: too general (T2, 3.12). |
| **Signal field** | A signal shown in the faceplate, with its label, typed in when its access allows. | `SIGNAL_FIELD` | — |
| **Command button** | A button of the faceplate that sends one command. | `COMMAND_BUTTON` | — |
| **Range** | The values a person may type in a number field, between a minimum and a maximum. | `RANGE`, `BOUND` | — |

### Values and units

| Word | Meaning | In the files | Not to use |
| --- | --- | --- | --- |
| **Quantity** | What a number measures: a mass, a temperature, a ratio. Every integer and real signal has one. | `QUANTITY`, `<name>.quantity.json` | Unit category: says less of what is chosen (T2, 3.12). Measurement: first a value read by a sensor (Analysis, 2026-11-21). |
| **Unit** | One way to count a quantity: the kilogram, the pound. | `UNIT` | — |
| **Unit symbol** | What is written after a value: `kg`, `°C`. Never the drawing of a symbol. | `UNIT.symbol` | Symbol alone, outside the files: it is the drawing placed (T5, 3.8). |
| **Unit system** | The units of a quantity that belong to one system, such as metric or imperial; it only groups them. | `UNIT_SYSTEM` | Family: also names families of equipment (T5). |
| **Default unit** | The unit of a quantity every conversion is written against; every number typed in Metadata is kept in it. | `QUANTITY.default_unit` | — |
| **Display unit** | The unit a preset shows a number in. | `DISPLAY_FORMAT.unit` | — |
| **Conversion** | The two formulas that turn a value of a unit into the default unit, and back. | `CONVERSION`: `to_default`, `from_default` | — |
| **Difference** | A gap between two points of a scale ("it rose by 5 °C"), against a value, a point on the scale ("it is 20 °C"). Only the temperatures convert them differently. | `relative_quantity`, `offers_relative_quantity` | Two words for one idea: the screens say "difference", the files `relative_quantity` (FMI). |
| **Gauge pressure** | A pressure read against the atmosphere: a quantity of its own, with no conversion to pressure. | `gauge_pressure` | — |
| **Enum** | A named list of items, picked by a signal whose value is one of them. | `ENUM`, `enums.json` | — |
| **Enum item** | One value of an enum: the number the model receives, and the name people read. | `ENUM_ITEM`: `key`, `display_name` | Key for the name: here the key is the number (TypeScript calls the names keys). |
| **Global enum**, **template enum** | A global enum has its items written once, the same everywhere; a template enum has its items completed on each placed symbol. | `enum_kind`: `global`, `template` | Template in any other sense in Metadata. |

### Names and keys of the files

| Word | Meaning | In the files | Not to use |
| --- | --- | --- | --- |
| **id** | The public identifier, written by the user, never a UUID: it leaves the software, to the model and the configuration files. | `id` | Identifier, for a designation (T5, 3.3). |
| **internal_id** | The key set by the software, a UUID version 7; every link holds one, and it never leaves the software. | `internal_id` | ID for this key: in AutomationML, `ID` is the UUID; an export says which is which (T5, 3.2). |
| **name** | A label people read, for a thing that has no `id`: nothing points to it by name, and it never goes to the model. | `name` | — |
| **display name** | A label shown in place of an `id` or a key; empty, the `id` or the key is shown. | `display_name` | — |
| **description** | A text that explains, for people. | `description` | — |
| **Designation** | What identifies the equipment of a placed symbol: Metadata defines it once (`tag`, `location`), its text is written on each placed symbol (`P-101`, `Hall B`). | `DESIGNATION`, `designations.json` | Identifier, Tag, Attribute, Parameter: each has another strong meaning for the users (T5, 3.3). |

## The other parts

The words Metadata uses from the other parts, as their pages say them today. Each part completes this section when it is written again.

| Word | Meaning | Defined in |
| --- | --- | --- |
| **Symbol** | A drawing, made in a Symbol Lib, that stands for a piece of equipment; it has a type or not yet. | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |
| **Placed symbol** | A symbol put in a synoptic: it has the texts of the designations and the flags of its type on or off. | [Synoptics](../synoptics/README.md) |
| **Synoptic** | An animated view of an installation, built by placing symbols and drawing pipes. | [Synoptics](../synoptics/README.md) |
| **Model** | The simulation model: it receives the inputs and sends the outputs. | [Introduction](introduction.md) |

## Open questions

- The name of the layer above the model, which receives the triggers: open in the [draft](../metadata/draft.md#open-questions-4).
- The names of the two quantities for numbers that measure nothing physical, "ratio" and "count": working names ([notes](../metadata/data-model-notes.md#open)).
- The names of the nested parts (`APPEARANCE`, `VALUE_TYPE`, `BOOLEAN_TEXTS`, `COMMAND_TARGET`, `DISPLAY_FORMAT`, `SIGNAL_FIELD`, `RANGE`, `BOUND`, `COMMAND_BUTTON`, `TEXT_CONTENT`, `CONVERSION`) and of `FACEPLATE_ELEMENT`: working names ([notes](../metadata/data-model-notes.md#open)).
