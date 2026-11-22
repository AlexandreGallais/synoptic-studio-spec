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
| 17 | [Command target](17-command-target.md) | The signal a command sends its value to, and that fixed value. | Draft |
| 18 | [Command](18-command.md) | What the front sends with one click: a fixed value to an input, an override of an output, or a trigger for the layer above the model. | Draft |
| 19 | [Flag](19-flag.md) | A key each placed symbol of a type has on or off, written in the configuration files for a program outside. | Draft |
| 20 | [Display format](20-display-format.md) | The unit and the decimals a preset shows an integer or a real with. | Draft |
| 21 | [Boolean texts](21-boolean-texts.md) | The words a preset shows for true and for false. | Draft |
| 22 | [Preset value](22-preset-value.md) | How a preset starts and shows one signal: its start value, and its display format or its boolean texts. | Draft |
| 23 | [Bound](23-bound.md) | The minimum or the maximum of a range: a typed number, or the value of an input signal. | Draft |
| 24 | [Range](24-range.md) | The values a person may type in a number field of the faceplate. | Draft |
| 25 | [Signal field](25-signal-field.md) | A signal shown in the faceplate, with its label, and how a person types it when its access allows. | Draft |
| 26 | [Command button](26-command-button.md) | A button of the faceplate that sends one command. | Draft |
| 27 | [Text content](27-text-content.md) | The text of a title or a paragraph of the faceplate: typed, or the text of a designation. | Draft |
| 28 | [Faceplate element](28-faceplate-element.md) | One line of the faceplate builder: a signal, a command, a title, a paragraph or a group. | Draft |
| 29 | [Preset](29-preset.md) | The defaults a symbol and a synoptic start from: the preset values and the faceplate. | Draft |
| 30 | [Type](30-type.md) | What a symbol represents, in a tree of types, with everything it holds; one file each. | Draft |
