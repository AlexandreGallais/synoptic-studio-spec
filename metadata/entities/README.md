# entities

> [Home](../../README.md) › [Metadata](../README.md) › Entities

The entities of Metadata, one file each: what the entity is, its schema, its JSON Schema, and the JSON Schema of its file when it has one of its own. The whole picture is the [Data model](../data-model.md).

| # | File | What it holds | Status |
| --- | --- | --- | --- |
| 01 | [Color](01-color.md) | One color of a palette, picked for the appearance of a type. | Draft |
| 02 | [Palette](02-palette.md) | A set of colors: the only colors a type can pick. | Draft |
| 03 | [Icon](03-icon.md) | One drawing of an icon set, picked for the appearance of a type. | Draft |
| 04 | [Icon set](04-icon-set.md) | A set of icons of one style or one origin: the icons a type can pick. | Draft |
| 05 | [Enum item](05-enum-item.md) | One value of an enum: the number the model receives and the name people read. | Draft |
| 06 | [Enum](06-enum.md) | A named list of items, picked by a signal whose value is an enum. | Draft |
| 07 | [Conversion](07-conversion.md) | The two formulas that turn a value of a unit into the default unit of its quantity, and back. | Draft |
| 08 | [Unit](08-unit.md) | One way to count a quantity, with its name, its symbol and its conversion. | Draft |
| 09 | [Unit system](09-unit-system.md) | The units of a quantity that belong to one system, such as metric or imperial. | Draft |
| 10 | [Quantity](10-quantity.md) | What a value measures, with its default unit and its unit systems; one file each. | Draft |
| 11 | [Designation](11-designation.md) | What identifies the equipment of a placed symbol, such as its tag or its location. | Draft |
| 12 | [Appearance](12-appearance.md) | The icon and the color a type shows, copied when picked; null, those of its parent. | Draft |
| 13 | [Link entity](13-link.md) | A path to a file or a folder, or a URL, in the documentation of a type. | Draft |
| 14 | [Documentation](14-documentation.md) | What explains a type to people: a description in Markdown and links. | Draft |
| 15 | [Value type](15-value-type.md) | What kind of value a signal holds, and for a number, the quantity it measures. | Draft |
| 16 | [Signal](16-signal.md) | A value that goes between the front and the model, as an input or an output. | Draft |
| 17 | [Display format](17-display-format.md) | The unit and the decimals an integer or a real is shown with. | Draft |
| 18 | [Boolean texts](18-boolean-texts.md) | The words shown for true and for false. | Draft |
| 19 | [Signal setting](19-signal-setting.md) | How one signal starts and is shown: its start value, and its display format or its boolean texts. | Draft |
| 20 | [Command target](20-command-target.md) | The signal a command sends its value to, and that fixed value. | Draft |
| 21 | [Command](21-command.md) | What the front sends with one click: a fixed value to an input, an override of an output, or a trigger for the layer above the model. | Draft |
| 22 | [Bound](22-bound.md) | The minimum or the maximum of a range: a typed number, or the value of an input signal. | Draft |
| 23 | [Range](23-range.md) | The values a person may type in a number field of the faceplate. | Draft |
| 24 | [Signal field](24-signal-field.md) | A signal shown in the faceplate, with its label, and how a person types it when its access allows. | Draft |
| 25 | [Command button](25-command-button.md) | A button of the faceplate that sends one command. | Draft |
| 26 | [Text content](26-text-content.md) | The text of a title or a paragraph of the faceplate: typed, or the text of a designation. | Draft |
| 27 | [Faceplate element](27-faceplate-element.md) | One line of the faceplate builder of a type: a signal, a command, a title, a paragraph or a group. | Draft |
| 28 | [Flag](28-flag.md) | A key each placed symbol of a type has on or off, written in the configuration files for a program outside. | Draft |
| 30 | [Type](30-type.md) | What a symbol represents, in a tree of types, with everything it holds; one file each. | Draft |

The entities of a type are numbered in the order of its parts (General, Documentation, Signals, Signal settings, Commands, Faceplate, Flags), each part's details before the entity that holds them; renumbered on 2026-11-24 when the parts took this order. Number 29 was Preset, removed on 2026-11-24 with the presets.
