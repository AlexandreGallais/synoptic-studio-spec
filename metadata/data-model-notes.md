# Data model: notes

> [Home](../README.md) › [Metadata](README.md) › [Data model](data-model.md) › Notes

Status: everything written around the schema of the [Data model](data-model.md) from 2026-11-19 to 2026-11-21, moved here on 2026-11-21 at the Product Owner's request, so that the data model shows the schema and its JSON alone ("je veux que le schéma et l'objet JSON, sans commentaire tout autour [...] je veux pas que tu supprimes tout ce que t'as écrit"). The content is unchanged, apart from the links and the section [Checked on 2026-11-21 (schema against JSON)](#checked-on-2026-11-21-schema-against-json). The documentation of each object comes later, object by object, in the data model itself.

## Rules of the schema

- `internal_id`: the UUID set by the software, always a UUID; every FK holds one. It is the surrogate key and never leaves the software (its match in the standards: [Files](files.md#the-two-keys-of-an-entity)).
  - Every UUID of Synoptic Studio is a **UUID version 7** (Product Owner, 2026-11-21: "le format qui a un timestamp [...] ça permettra d'avoir des trucs plus propres si jamais on met ça dans une base de données"). Version 7 starts with the time of its creation, in milliseconds since 1970 (UTC), so that UUIDs sort in the order they were made; RFC 9562 (May 2024, section 5.7) advises it over versions 1 and 6, the other two with a timestamp.
  - Written in lower case, 36 characters with the dashes; the 13th digit is always `7`.
  - The made-up UUIDs of the examples follow this shape (`01a1f800-0000-7000-8000-…`).
- `id`: the public identifier, written by the user, never a UUID, that leaves the application: sent to the model and written in the configuration files.
- `name`: a label people read, for a thing that has no `id`: nothing points to it and it never goes to the model. What the software ships (quantities, unit systems, units), the name of a preset (see [Read again on 2026-11-21](#read-again-on-2026-11-21-presets-and-faceplate)), the name of a palette, of an icon or of a color (decision 0057). Unlike FMI, Kubernetes or Google, where `name` identifies a thing, it is only a label here.
- `display_name`: a label people read, for a thing that has an `id` or a key: it is shown in place of that `id` or key, and never goes to the model (an enum item, a signal field, a command button). A designation has none: its `id` is shown (2026-11-21). Empty, the `id` or the key is shown.
- `key` of an enum item: the whole number sent to the model, never the item's name (TypeScript calls the names keys; here the key is the number).
- `description`: a text that explains, for people; plain text everywhere, Markdown only in `DOCUMENTATION`.
- A choice of the software (`kind`, `direction`, `access`...) is written in the JSON as an English word (`"input"`, `"real"`), never as a number, so that a file reads by itself (Product Owner, 2026-11-19). A value of several words is joined by underscores (`set_signal`, `number_field`), the same in the schema and in the JSON. The key of an enum item stays a whole number: it goes to the model (decisions 0012, 0016).
- The field that says which alternative a box is: `kind` when the alternative changes what the thing is (a link is a path or a URL, an element is a signal field or a button); `source` when the thing stays the same and only its value comes from elsewhere (a bound is always a number, typed or read from a signal; a text is always a text, typed or read from a designation), each value of `source` naming the field that then holds the value (`typed` → `typed_value` or `typed_text`, `signal` → `signal`, `designation` → `designation`); `direction`, `access` and `input_kind` where their own word says more. Never `type`, which already names `TYPE` and `VALUE_TYPE`.
- One idea, one word, across the whole JSON: a value that is a gap between two points is a `relative_quantity` everywhere in the files (`VALUE_TYPE.relative_quantity`, `QUANTITY.offers_relative_quantity`); the screens keep "difference" for people.
- A list of choices is named after its field; a field called `kind` or `source`, which several boxes have, takes its box as prefix (`command_kind`, `bound_source`). Every list is in [The choice lists](#the-choice-lists).
- A value typed in the builder is prefixed `typed_` where it stands beside a value taken elsewhere (`typed_value`, `typed_text`). A value read by the value type of its signal (a number, a boolean or an enum item) has the type `signal_value`.
- A box without `internal_id` is a part of its owner (a nested object in the JSON), never pointed to.
- Fields that only exist together go in a part of their own (`RANGE`, `DISPLAY_FORMAT`), with one exception: the `quantity` of a number and its `relative_quantity` stay on `VALUE_TYPE`, in the words of FMI (decision 0059).
- `has`: one nested object; `holds`: an ordered list inside its owner. When an owner has two parts of the same box, the link says their role (`has, as min`).
- Every other link is a FK, labelled by the field that holds it, so that the reader knows which field points where. The field is named after the box it points to (`signal`, `quantity`, `unit`), or after its role when the box alone says too little (`parent`, `default_unit`).
- A link or a field that only exists in some cases says when, always in the same words: `when kind is enum`, `when the signal is an enum`.
- A number typed in Metadata (a default value, the value of a command, a typed bound) is kept in the default unit of its signal's quantity, whatever unit the screen shows it in (decision 0051).
- Field order in each box: `internal_id`, then `kind` or `source` (so that the reader knows at once which fields follow, Product Owner, 2026-11-21), then the links (FK), then the other choices (`direction`, `access`, `input_kind`), then `id` or the name, then the values, then the texts.
- Every name follows these rules (see [Names made even on 2026-11-21](#names-made-even-on-2026-11-21)) and the research T5 (see [Applied on 2026-11-22 (names, research T5)](#applied-on-2026-11-22-names-research-t5)).

## How the schema becomes JSON

Asked by the Product Owner on 2026-11-21 ("que tu me construises juste en dessous du schéma l'objet JSON [...] qui représente un peu tout ce qu'il pourrait avoir"). One made-up type that uses every box of a type at least once, without trying every combination; then a global enum and a quantity of the catalogue, which live in files of their own. The designations, the icons and the palettes are left out; the file of the designations is in [Designation](entities/01-designation.md) since 2026-11-21. The internal IDs are made up, and only their last digits differ, to read them easily.

How the boxes become JSON, one rule for each, with no exception (the names of the lists confirmed by the Product Owner on 2026-11-21, decision 0057):

- A field keeps its name in the schema (`internal_id`, `display_name`, `typed_value`).
- A part (`has`) is a nested object named after its box, in lower case (`value_type`, `display_format`, `command_target`, `signal_field`); two parts of the same box are named by their role (`min`, `max`).
- A list (`holds`) is an array named after the box it holds, in lower case and in the plural (`signals`, `enum_items`, `preset_values`, `faceplate_elements`, `units`): the same list has the same name everywhere, in a preset and in a group.
- The field order is the rule of the head of this file; the parts and the lists come after the fields of their box.
- A field or a part that does not exist in this case (its `when` is false) is left out; one that exists but is empty is `null` (no parent, no color, no display name).
- A choice of several words is joined by underscores: `"set_signal"`, `"number_field"`, `"radio_horizontal"`.
- A file adds one key that no box shows: `"format_version"`, the version of the file format, first key of the file. It belongs to the file, not to an object, so it is described in the rules of the files only ([Files](draft.md#files)), never in the schema (Product Owner, 2026-11-21, see [Settled on 2026-11-21 (format key)](#settled-on-2026-11-21-format-key)).

### What the type shows

What the example of a type shows, beyond the fields themselves:

- **Numbers are kept in the default unit** (decision 0051): the speeds are in rad/s, the default unit of the made-up quantity `…900` (angular velocity), while the preset shows them in rpm (`…902`). `157.0796` is 1500 rpm, `151.8436` is 1450 rpm.
- **A typed value is read by the signal it targets**: `switch_to_auto` sends the internal ID of the item `auto` because `mode` is an enum; `force_speed` sends a number because `speed` is a real.
- **The maximum of the setpoint is a signal**: `speed_max`, an input of the same quantity (decision 0056); the minimum is typed.
- **No `input_kind` and no `range` in read**, no `display_format` for the boolean and the enum, `boolean_texts` for the boolean only, no `command_target` for a trigger: their `when` is false.
- **The texts of a boolean are in the preset** (decision 0058): `running` shows "Running" or "Stopped" with the preset `Standard`; another preset of the same type may say "On" and "Off".
- **`display_name: null`**: the field of `speed` shows the signal's `id`.
- **A difference**: `bearing_temperature_rise` holds a gap of temperature, shown in °C (`…912`), kept in kelvins.
- The title shows the designation `…800` (`tag`, say `P-101`) of each placed symbol; the designations have their file of their own ([Designation](entities/01-designation.md)).

### What the quantity shows

A quantity is shipped with the software, never copied into the user's files: they hold the internal IDs only (draft, Data model).

- The kelvin has no `conversion`: it is the default unit.
- A difference is converted by the software from these two formulas (decision 0050): a rise of 1 °C is 1 K, a rise of 1 °F is 5/9 K.
- The syntax of the formulas goes to a documentary research (see [Noted on 2026-11-22](#noted-on-2026-11-22-syntax-of-the-formulas)).

## The faceplate, box by box

Written on 2026-11-21, at the Product Owner's request ("pour la partie faceplate, j'aimerais bien que tu refasses un retravail là-dessus [...] c'est un peu flou"). It says, field by field, what the boxes of the mode Faceplate of a preset hold. The rules are those of [Presets and their faceplate](draft.md#presets-and-their-faceplate) and of the dated sections below (decision 0055 for the text, the display name and the range; decision 0056 for the quantity of a bound).

A preset holds an ordered list of elements. Each element has a kind, and its kind gives it exactly one part, or, for a group, its own list of elements.

```mermaid
flowchart LR
    P["Preset"] -->|"holds, in order"| E["Faceplate element: kind"]
    E -->|"kind is signal"| SF["SIGNAL_FIELD: a signal shown, maybe typed in"]
    E -->|"kind is command"| CB["COMMAND_BUTTON: a button that sends a command"]
    E -->|"kind is title or paragraph"| TC["TEXT_CONTENT: typed, or a designation"]
    E -->|"kind is group"| G["Its own elements, in order"]
    SF -->|"when input_kind is number_field"| R["RANGE: the values allowed"]
    R -->|"min, max"| B["BOUND: typed, or an input of the same quantity"]
```

### `FACEPLATE_ELEMENT`: one line of the builder

| Field | What it holds | When |
| --- | --- | --- |
| `internal_id` | The UUID set by the software. | Always. |
| `kind` | Signal, command, title, paragraph or group (see [The choice lists](#the-choice-lists)). | Always. |
| `faceplate_elements` | The elements inside a group, in order, with the same five kinds; the same name as the list of the preset. | When `kind` is group. |

### `SIGNAL_FIELD`: a signal shown in the faceplate

A labelled field that shows the value of one signal, and lets a person type it when its access allows.

| Field | What it holds | When |
| --- | --- | --- |
| `signal` | The signal shown: one of the type, own or inherited. | Always. |
| `access` | `read`: the field only shows the value, as text alone: in the display unit and with the decimals of the preset, an enum by the display name of its item, a boolean by the text of its state (the `BOOLEAN_TEXTS` of the preset). `write`, for an input: a person types the value the model receives. `override`, for an output: a person types a value that replaces the model's. | Always. Write is offered for an input only, override for an output only (decision 0040). |
| `input_kind` | How the value is typed: `number_field`, `radio_horizontal`, `radio_vertical`, `select` or `switch` (see [The choice lists](#the-choice-lists)). | When `access` is write or override. The choices depend on the value type of the signal. |
| `display_name` | The label beside the field, for people; never sent to the model (decision 0055). | Always; empty, the signal's `id` is shown (decision 0018). |
| `range` | A `RANGE`: the values a person may type. | When `input_kind` is `number_field`. |

### `RANGE`: the values allowed in a number field

The minimum and the maximum only exist together, for a number field: they go in a part of their own, by the rule of the schema (see [Read again on 2026-11-19 (enums)](#read-again-on-2026-11-19-enums)).

| Field | What it holds | When |
| --- | --- | --- |
| `min` | A `BOUND`: the smallest value allowed. | Optional: empty, no minimum. |
| `max` | A `BOUND`: the largest value allowed. | Optional: empty, no maximum. |

A typed value outside the range is refused (assistant's reading, screen MD-07.22).

### `BOUND`: the minimum or the maximum of a range

A bound is its own box because it is one of two things, a number or a signal: three fields that say which, rather than six fields in `RANGE`.

| Field | What it holds | When |
| --- | --- | --- |
| `source` | `typed`: a number typed in the builder. `signal`: the value of an input signal of the type, read at each moment. | Always. |
| `typed_value` | The number. Shown and typed in the display unit of the preset (`g`, if the preset shows a mass in grams); kept in the default unit of the quantity of the signal shown, the unit of the Units page that every conversion is written against (`kg` for the mass), so that changing the display unit never changes the bound (decision 0051). | When `source` is typed. |
| `signal` | The signal whose value is the bound, picked with the small icon inside the field (decision 0041). An input only, never an output: an input is what the model receives, so the bound stays what the user set (decision 0055). An integer or a real of the same quantity as the signal shown, so that both compare in the same default unit; the list offers only these inputs (decision 0056). | When `source` is signal. |

### `COMMAND_BUTTON`: a button that sends a command

Found right by the Product Owner on 2026-11-21 ("button text, ça, c'est parfait, et la commande associée"); its text renamed `display_name` the same day, to read like the label of a signal field (decision 0057).

| Field | What it holds | When |
| --- | --- | --- |
| `command` | The command sent by a click, one of the type, own or inherited. | Always. |
| `display_name` | The text on the button, for people; never sent to the model. | Always; empty, the command's `id` is shown, as for a signal field. |

### `TEXT_CONTENT`: the text of a title or a paragraph

The text a title or a paragraph element shows, and where it comes from. The small icon on the right of its field chooses the source (Product Owner, 2026-11-18, decision 0048).

| Field | What it holds | When |
| --- | --- | --- |
| `source` | `typed`: a text typed in the builder. `designation`: the text filled for a designation on each placed symbol. | Always. |
| `typed_text` | The text. A paragraph keeps its line breaks; neither takes Markdown. | When `source` is typed. |
| `designation` | The designation whose text is shown: `tag` shows `P-101` on one pump and `P-102` on the next. | When `source` is designation. |

**Never a signal** (Product Owner, 2026-11-21: "ça doit venir que d'un identifiant et jamais d'un signal [...] un signal, on peut l'afficher avec la partie signal"): the value of a signal is shown by a signal element in read. Decision 0055 changes decisions 0048 and 0054 on this point.

## The choice lists

Every field whose value is one word from a fixed list. Each is written in the JSON as that word in English (see the head of this file).

| List | Field | Values | Meaning |
| --- | --- | --- | --- |
| `link_kind` | `LINK.kind` | path, url | A path to a file or a folder, or a web address; held in `LINK.address`. |
| `direction` | `SIGNAL.direction` | input, output | The model receives it, or the model sends it. |
| `value_type_kind` | `VALUE_TYPE.kind` | integer, real, boolean, enum | A whole number, a number, true or false, an item of an enum. |
| `command_kind` | `COMMAND.kind` | set_signal, trigger, override | Send a fixed value to an input; tell the model something happened; replace the value of an output. |
| `enum_kind` | `ENUM.kind` | global, template | Items written on the Enums page, the same everywhere; or items completed on each placed symbol. |
| `faceplate_element_kind` | `FACEPLATE_ELEMENT.kind` | signal, command, title, paragraph, group | See [The faceplate, box by box](#the-faceplate-box-by-box). |
| `access` | `SIGNAL_FIELD.access` | read, write, override | Shown only; typed in, for an input; typed in, for an output. |
| `input_kind` | `SIGNAL_FIELD.input_kind` | number_field, radio_horizontal, radio_vertical, select, switch | `number_field`: for an integer or a real. `radio_horizontal` (the buttons on one line), `radio_vertical` (one button per line), `select`: for an enum, its items in the order of the handles of the Enums page. Switch: for a boolean, one click turns it on or off. |
| `bound_source` | `BOUND.source` | typed, signal | See `BOUND`. |
| `text_content_source` | `TEXT_CONTENT.source` | typed, designation | See `TEXT_CONTENT`. |

## Checked on 2026-11-21 (schema against JSON)

Asked by the Product Owner on 2026-11-21 ("une longue recherche et une comparaison entre l'objet JSON et le schéma, pour voir si tout est cohérent, et [...] pour voir si tous les noms sont logiques"), before the entities are validated one by one. Every box, field, link and label of the schema was read against the three JSON examples and against the rules of the head of this file.

- **The JSON matches the schema.**
  - Every key of the examples is a field, a part or a list of the schema, under its name; `format` is the only exception (see [Open](#open)).
  - Every `when` is followed: no `input_kind` nor `range` in read, no `command_target` for a trigger, `display_format` for the numbers only, `boolean_texts` for the boolean only, `quantity` and `relative_quantity` for the reals only.
  - One preset value per signal of the type: six for six.
  - The order of the keys follows the rule in every object.
  - The numbers are right: 1500 rpm is 157.0796 rad/s, 1450 rpm is 151.8436 rad/s; the two formulas of the °F go there and back.
- **The names follow the rules**: `name`, `display_name`, `description`; `kind` and `source`; the FK fields; the lists named after their box; the choice lists named after their field. Nothing renamed.
- **Changed in the schema, to follow rules already written** (assistant; nothing new decided, the JSON examples do not change):
  - `ICON` and `COLOUR`: `name` before `drawing` and `value`, by the order of the fields (the name before the values), as `UNIT` and `QUANTITY` already do.
  - `ENUM_ITEM.display_name` and `IDENTIFIER.display_name` say what is shown when they are empty (the key, the `id`), by the rule of `display_name`, as `SIGNAL_FIELD` and `COMMAND_BUTTON` already did.
  - `COMMAND_TARGET.signal` says which signal each kind takes: an input for `set_signal`, an output for `override`, as the list `command_kind` says.
  - `SIGNAL_FIELD.input_kind` says which choices go with which value type, as the list `input_kind` says.
  - `DISPLAY_FORMAT.unit` says it is a unit of the signal's quantity; `QUANTITY.default_unit` says it is one of its units.
- **Checked and unchanged**: `RANGE` is drawn without fields of its own, since it only holds its two bounds; `IDENTIFIER`, `ICON` and `PALETTE` have no owner in this schema, since they live in files of their own.

## Changed on 2026-11-19

Asked by the Product Owner on 2026-11-19, while reading the schema; the three points the assistant proposed were settled by the Product Owner the same day, in the questionnaire. Decision 0049 (accepted, 2026-11-19) records them: it changes decision 0003 (reference family, closed forms) and specifies decision 0020 (a difference).

- **The default unit** replaces `model_unit` (Product Owner: "c'est plutôt la unit par défaut"): the unit of the quantity that every conversion is written against, as the Units page already calls it. Its own conversion is empty: it is the unit itself.
- **No reference family any more**: every unit converts to the default unit and back, never to another family. It answers the question of 2026-11-17 the way the assistant proposed then; the families only group the units for reading.
- **A conversion is the real formula** (Product Owner: "que la conversion on puisse mettre le calcul réel"), not only a factor: two expressions in `x`, one from the default unit, one back to it, because a free formula cannot be turned round by the software. Confirmed by the Product Owner on 2026-11-19 ("Oui, formules libres"). It replaces the rule of 2026-11-11 (decision 0003) by which a conversion was one of four closed forms, a pair of free expressions being the last resort. The four forms of the research (proportional, affine, inverse, logarithmic) are now just formulas like any other. The catalogue is written by contributors, so its tests check that each pair goes there and back.
- **A quantity has a `name`, not an `id`** (Product Owner: "c'est pas vraiment ce que j'appellerai un ID, c'est plutôt un nom"): mass, volume, flow are shipped by the software, never typed by the user.
- **A difference is no longer a quantity of its own** (assistant's proposal, chosen by the Product Owner on 2026-11-19: "une lecture de la grandeur"; no table of its own): the signal says whether its value is the quantity or a difference of it (`measure`, as decision 0020 already says), and the units of a quantity whose conversion changes (`offers_difference`, temperature, gauge pressure...) carry a second conversion, for a difference (computed by the software since the evening, see below). It removes the quantity that points to another quantity (`difference_of`, `kind`), which read badly. It is what FMI does with its flag `relativeQuantity` (research T2, section 3.8).
- **`integer` stays a value kind** beside `real`, `boolean` and `enum` (Product Owner, 2026-11-19: "Garder integer"), as decisions 0003 and 0043 already say: the model receives an exact whole number, and the input refuses decimals. FMI and SSP keep integers apart from reals (research T2, section 3.1).

## Read again on 2026-11-19 (afternoon)

The Product Owner read the quantity part again and found it right (`measure`: "ça, c'est vraiment bien"; families: metric or imperial "c'est juste ça"; units: name and symbol).

- **The units of a family are sorted by the software, never by hand** (Product Owner: "Oui, go faire ça. C'est plus simple comme ça"): smallest first, by the size of one step in the default unit, `to_default(1) − to_default(0)`; equal sizes by name. The catalogue writes them in any order. A quantity whose formulas give no finite step (an inverse such as l/100 km, a logarithm such as dB) keeps the order the catalogue writes.
- **The two expressions of a conversion are named by where `x` goes**: `to_default` takes `x` in this unit and gives the default unit; `from_default` takes `x` in the default unit and gives this unit. The labels of the schema said it the wrong way round.
- **What a difference is, said for the Product Owner** (the assistant's explanation, not a new rule): a value is a point on the scale ("it is 20 °C"), a difference is a gap between two points ("it rose by 20 °C"). Most conversions only multiply (litres to decalitres, kilograms to pounds): a value and a difference then convert the same way, so a quantity like volume needs nothing more. A conversion that also shifts the zero (°C to °F: `x × 9/5 + 32`; gauge to absolute pressure) converts them differently: 20 °C is 68 °F, but a rise of 20 °C is a rise of 36 °F, because the `+ 32` cancels out in a gap. `offers_difference` marks these quantities, as decision 0020 says.
- **`default_decimals` is for the screen, never for the model**: the model always gets the full value; the decimals only round what is shown. Removed the same day (see below).

## Settled on 2026-11-19 (evening)

The Product Owner answered the two questions of the afternoon in the questionnaire. Decision 0050 (accepted, 2026-11-19) records them: it changes decisions 0049 (a second conversion for a difference) and 0020 (default decimals in the catalogue).

- **A difference is converted by the software, never written in the catalogue** (Product Owner: "si tout peut être calculé, « logiquement », ben go"; with no exception, else everything by hand): the difference of `x` in the default unit is `to_default(x) − to_default(0)`, and back `from_default(x) − from_default(0)`. A unit has one conversion only; the conversion "of a difference" is gone.
  - Why there is no exception: this computation is exact for every conversion that multiplies then shifts (°C, °F, K, gauge or absolute pressure), and these are the only quantities that offer a difference. A conversion that only multiplies needs no difference at all. A conversion that is not a straight line (an inverse such as l/100 km, a logarithm such as dB) has no difference that converts on its own, and such a quantity never offers one.
  - Hence one rule of the catalogue, checked by its tests: a quantity with `offers_difference` has only conversions that multiply then shift (`to_default(x) − to_default(0)` proportional to `x`).
- **No `default_decimals` on the quantity** (Product Owner: "les décimales à montrer, c'est vraiment selon les presets [...] il faut l'enlever de l'objet quantité"): the decimals shown are set in the presets only, which start from one default number of decimals, the same everywhere. The assistant agrees: the right number of decimals depends on the unit shown, not on the quantity (2 decimals show 10 g in kilograms, but 0.01 g in grams), so a default per quantity would be wrong as soon as a preset shows another unit.

## Read again on 2026-11-19 (enums)

The Product Owner read the enums and found them right (enum: kind, `id`, description, "faut pas plus"; item: key, display name, description, and its place in the list). The Product Owner then asked why `VALUE_TYPE` holds `measure` beside `enum`, when a signal does not always have a quantity. The question was right: `measure` only means something when there is a quantity, and the box did not say it. The fix is a rule for the whole schema, not only for this box (assistant's proposal, asked by the Product Owner: "corriger tous les endroits où il y aura des problèmes comme ça").

- **Fields that only exist together go in a part of their own.** The quantity and `measure` move to `MEASUREMENT`, which a value type has for an integer or a real only. The enum stays a single field of `VALUE_TYPE`: it has nothing else that goes with it, so it needs no part.
- **A part that only exists for some signals says so on its link.** `DISPLAY` (unit and decimals) is there for an integer or a real only, never for a boolean or an enum; its unit only when the signal has a quantity.
- **A choice between alternatives says which one it is**, as `VALUE_TYPE.kind` does, instead of leaving the reader to guess from the field that is filled. `BOUND` gets `source` (typed or signal), `TEXT_CONTENT` gets `source` (fixed, identifier or signal); each other field says when it is filled.
- **A typed value says what it holds**: a number, a boolean, or the internal ID of an enum item (decision 0047), in `COMMAND_TARGET` and `PRESET_VALUE`.
- The screen of an enum showed "Name": it is the `id`, as the Product Owner said ("ça devrait être ID"), in `screens/metadata.md`, MD-09.3.

## Read again on 2026-11-19 (signals, commands, flags)

The Product Owner read the signals, the commands and the flags and found them right; nothing changes in the schema.

- **Signals**: right ("j'ai l'impression que c'est bon, en tout cas pour moi").
- **Commands** ("C'est propre, je trouve"): a type holds its commands; a command has its `id` and its kind (set a signal, trigger or override); a command that sets a signal has a `COMMAND_TARGET`, the signal and the value sent; it is used by a command button of a faceplate element.
- **The typed value is not checked by its own field** (Product Owner: "en fonction de l'UID, on est censé savoir ce que c'est [...] tout est censé parser en fonction de la foreign key"): the field accepts a number, a boolean or the internal ID of an enum item, and it is read by the value type of the signal it targets. An integer signal reads a whole number, a boolean signal a boolean, an enum signal the internal ID of one of its items.
- **Flags**: an `id` and a description, "faut pas plus".
- Next: the presets, after a break.

## Read again on 2026-11-19 (presets)

The Product Owner read the preset, its values and their display. The preset (a name) and its values (a signal, a default value) are right ("ça fait sens"). He found the links to the enums and the signals unclear, and left the fix to the assistant ("je te laisse faire"), with a pass over the whole schema to make it even.

- **The "default item" and "sends" links were not fields of their own**: they are the typed value itself (`default_value`, `value`) when the signal is an enum, as decision 0047 says. They are now labelled by that field: `default_value, when the signal is an enum`, `value, when the signal is an enum`. The item is always one of the signal's enum.
- **Every FK link is labelled by its field**, all over the schema (`signal`, `quantity`, `default_unit`, `icon`...), instead of a verb (`targets`, `value of`, `shown in`, `measures`). `has` and `holds` stay for nested parts.
- **Every condition is said the same way**, `when ...`, on the fields and on the links: it replaces `enum only`, `signal only`, `typed only`, `integer or real only`, `a group holds`.
- **The parts of a faceplate element say when they exist**: a signal field for a signal element, a command button for a command element, a text content for a title or a description, the children for a group.
- **A command target exists for "set a signal" and for "override"**: the section above said "a command that sets a signal" only; an override targets an output the same way (draft, Commands).
- **A preset holds one value per signal of the type**, own and inherited, so none for a type without signals: `o{` instead of `|{`.
- **A unit has a conversion except the default unit**: said on the link, as the section of the morning already said.

### Can a number have no quantity? Checked on 2026-11-19

Asked by the Product Owner, who thinks a real always has a quantity or a difference ("il faut que tu fasses une recherche"). A fact to find, checked in the standard and in a catalogue of units, not a documentary research of its own.

- **FMI allows a number without unit**: "Variables without unit must not have a `unit` attribute" ([FMI 3.0.1](https://fmi-standard.org/docs/3.0.1/), section 2.4.7.5, table 21, read on 2026-11-19). A display unit needs a unit: "If `displayUnit` is defined a `unit` must also be defined" (same document, section 2.4.4, table 15). AutomationML also makes the unit optional (research T2, `research/t2-recherche-documentaire-unique-modeles-de-donnees/rapport.md`, section 3.1, source S8).
- **Such numbers exist in models**: a ratio, an efficiency, a valve opening from 0 to 1, a count. Paraphrase, assistant's examples.
- **A catalogue of units gives them a quantity anyway**: QUDT puts the percent and the per mille under the quantity "DimensionlessRatio" (percent = 0.01), and a count under the quantity "Count", whose unit is "unitless" ([QUDT, percent](https://qudt.org/vocab/unit/PERCENT), [QUDT, count](https://qudt.org/vocab/quantitykind/Count), read on 2026-11-19 through a search summary, pages not opened one by one).
- **What it changes in `DISPLAY`**: the unit and the decimals do not always go together. A real with no quantity still needs decimals, but has no unit to show. An integer needs decimals only when it is shown in another unit than its default unit (1450 rpm is 24.17 rps).
- Asked in the questionnaire: either every integer and real has a quantity, or a number may have no quantity and the decimals leave `DISPLAY`. Settled the same day, see below.

## Settled on 2026-11-19 (night)

The Product Owner answered the two questions of the presets in the questionnaire, with the option the assistant advised each time. Decision 0051 (accepted, 2026-11-19) records them: it changes the rule of the draft by which the quantity of a signal is optional (`draft.md`, Signals; screen MD-04.9), and extends decision 0024 (the bounds of a signal written in the model unit of its quantity) to every number typed in Metadata.

- **Every integer and real signal has a quantity** (Product Owner: "Quantité obligatoire"). A number that measures nothing physical gets one from the catalogue, as QUDT does (see above): a **ratio** (units 1, %, ‰, ppm; default unit 1) for a rate, an efficiency or a valve opening from 0 to 1, and a **count** (unit 1) for a number of things. Working names, as the other quantities of the catalogue. In the schema:
  - `MEASUREMENT` is always there for an integer or a real, and its `quantity` is required (it already was on the link);
  - `DISPLAY` keeps its unit and its decimals together; its `unit` is required and no longer says "when the signal has a quantity";
  - the rule of the head of the file gives another example of a condition.
- **A number typed in Metadata is kept in the default unit of its quantity** (Product Owner: "Unité par défaut"): the default value of a preset, the value of a command, a typed bound of a signal field. Changing the display unit of a preset never changes a stored value: the screen converts it with `from_default` to show it, and what the user types in the display unit is turned back with `to_default` before it is kept. A difference is turned the way decision 0050 says.
  - The bound is the assistant's reading: the question named the default value and the value of a command; a typed bound is the same kind of number, so the same rule applies.
  - It answers the gap the research T2 found: the conversion back of the values typed (`research/t2-recherche-documentaire-unique-modeles-de-donnees/rapport.md`, short answer, point 4).

## Changed on 2026-11-20 (descriptions)

The Product Owner found that the signals and the commands had no description ("il manque un champ description [...] c'est essentiel parce qu'il faut pouvoir expliquer ce qu'on veut dire au modeleur"). Decision 0052 (accepted, 2026-11-20) records it: it replaces the rule of the draft "a signal has no description" (2026-11-16).

- **A signal and a command each get a `description`**: a text that says what the line means, for the person who writes the model.
- Checked against the rest of the schema, as he listed it: the type has its description in `DOCUMENTATION`; a flag, an enum, an enum item and an identifier already have one. Nothing else changes.
- Plain text, like the description of a flag or of an enum item, never Markdown: assistant's reading.

## Settled on 2026-11-20 (descriptions)

The Product Owner answered the two questions of the morning in the questionnaire, with the option the assistant advised each time. Decision 0052 records them.

- **The description is optional** (Product Owner: "Facultative"), as for the flags and the enum items: an empty description never blocks anything. `description` stays a plain `text` field, which may be empty.
- **It is written in the configuration files sent with the model** (Product Owner: "Dans les fichiers de configuration"), so that the model author reads it where they work. It is edited in Metadata only (Product Owner: "on ne peut la modifier que dans la metadata"). Changing it changes nothing the model reads.
- A way for model authors to read the synoptics without changing them, with a summary sheet when they click a symbol, is an idea of the Product Owner for later ("ça, on verra ça plus tard"): noted in the open questions of the synoptics, nothing written here.

## Settled on 2026-11-21 (no versions)

The Product Owner answered the question of the day before in the questionnaire, with the option the assistant advised ("Les retirer, Git suffit"). Decision 0053 (accepted, 2026-11-21) records it: it changes decision 0017.

- **The schema has no version of Metadata**: no version number, no change log, nothing "not yet versioned". The application keeps no versions; the types are clean JSON files, one per type, that the user versions with Git if they want.
- So the JSON files must stay readable and stable (one field per line, the same order of keys every time), for the differences of Git to be clear: assistant's reading, to settle with the format of the files.
- The `"format"` number at the top of each file stays: it is the version of the file format, not of Metadata.

## Read again on 2026-11-21 (presets and faceplate)

The Product Owner read the preset, its values and the faceplate again. The values are right ("default value", the link to the enum item, the decimals beside the unit: "ça fait sens, c'est cool"); the command button too. He found the rest of the faceplate unclear and asked for it to be reworked, and left two names to the assistant ("à toi de me le dire").

- **The preset keeps a `name`, not an `id`** (assistant's choice, left to it by the Product Owner, who leaned that way: "peut-être que non, c'est mieux là, parce que ça va pas être utilisé comme un ID"). Nothing points to it, every link goes through its `internal_id`, and it never goes to the model: it only tells two presets of a type apart for people. The head of the file now says what `id` and `name` each mean, so that the difference is a rule and not an exception. Screen MD-07.3 already says "Name of the preset".
- **`DISPLAY` becomes `DISPLAY_FORMAT`, not "display unit"** (assistant's choice, asked by the Product Owner: "Pourquoi pas display unit ?"). The part holds two things that go together, the display unit and the decimals, so "display unit" would name only half of it; "display" alone said too little. Its `unit` field is the display unit, said in the schema.
- **The faceplate is described box by box**, in [The faceplate, box by box](#the-faceplate-box-by-box): what each field holds and when, with a diagram of which part goes with which kind of element.
- **Every choice list is described**, in [The choice lists](#the-choice-lists), with its values and their meaning (Product Owner: "Input kind : c'est un enum pour moi, mais du coup, tu décris pas l'enum").
- **Fields renamed so that they say what they hold** (Product Owner: "Je veux bien que tu repasses sur les noms des propriétés"):
  - `SIGNAL_FIELD.input` becomes `input_kind`, the Product Owner's own reading, so that it is never mistaken for an input of the model; its values are written in the schema;
  - `access` says in the schema which value goes with which direction: write for an input, override for an output;
  - `BOUND.value` becomes `typed_value` and `TEXT_CONTENT.text` becomes `typed_text`: each says it is the typed one, beside the signal or the identifier;
  - the source of a text says `typed` instead of `fixed`, the same word as for a bound; screen MD-07.19 and the draft keep "fixed text" for the user, which means the same.
- **Why a title or a description could point to a signal** (Product Owner: "Je comprends pas pourquoi y a un truc signal"): he asked for it on 2026-11-18 (decision 0048). Removed the same day, see [Read again on 2026-11-21 (faceplate fields)](#read-again-on-2026-11-21-faceplate-fields).

## Settled on 2026-11-21 (faceplate fields)

The Product Owner answered the two questions of the faceplate in the questionnaire, with the option the assistant advised each time.

- **A boolean signal is typed with a switch** (Product Owner: "Interrupteur (switch)"): `switch` is added to `input_kind`, for a boolean only. One click turns it on or off, and its state reads at a glance.
- **A signal field in read shows the text of the value alone** (Product Owner: "Le texte de la valeur seul"): in the display unit and with the decimals of the preset, an enum by the display name of its item, a boolean by the text of its state. No field is drawn, not even greyed.
- **A boolean signal has two texts of its own** (Product Owner, in a third question: "Deux mots choisis par signal"): `true_text` and `false_text` ("Open" and "Closed", "Running" and "Stopped"), in a part `BOOLEAN_TEXTS` that a value type has for a boolean only, as `MEASUREMENT` for a number. They were typed in the table of signals; moved to the preset the same day, see [Changed on 2026-11-21 (boolean texts)](#changed-on-2026-11-21-boolean-texts). Assistant's reading, to confirm: they never go to the model, which gets `true` or `false`; empty, the faceplate shows "true" and "false"; the switch shows the text of its state beside it.
- Decision 0054 (accepted, 2026-11-21) records the three answers.
- **So `input_kind` only exists in write or override**: it says how a value is typed, and nothing is typed in read. The builder may keep the last choice while the access changes, so that going back to write finds it: assistant's reading, a matter of the screen, not of the file.
- The bounds follow: `min` and `max` exist only for a number field, so never in read.

## Read again on 2026-11-21 (faceplate fields)

The Product Owner read the signal field, its bounds and the text content again. Decision 0055 (accepted, 2026-11-21) records the first three points: it changes decisions 0048 and 0054 (a text bound to a signal) and specifies decisions 0018 (the name) and 0041 (a bound taken from a signal).

- **A title or a description comes from a typed text or an identifier, never from a signal** (Product Owner: "le titre ou une description, je pense que ça doit venir que d'un identifiant et jamais d'un signal [...] Puisqu'un signal, on peut l'afficher avec la partie signal"). `signal` leaves `TEXT_CONTENT` and `text_source`. The value of a signal is shown by a signal element in read, which does the same with a label.
- **`name_shown` becomes `display_name`** (Product Owner: "est-ce que c'est pas display name qu'on appellerait ça [...] faudrait homogénéiser ça partout"): the name people read, the same word as the field of an identifier. The screens and the draft say "Display name" too.
- **A bound taken from a signal takes an input only, never an output, for now** (Product Owner: "qu'en entrée, jamais en sortie pour l'instant [...] Au moins, le signal, il reste fixe"): an input is a value the user sets and the model receives, so the range does not move with what the model computes. A bounded linear animation of a symbol keeps any signal, input or output: it is another rule (decision 0027).
  - The signal of a bound is an integer or a real of the same quantity as the signal shown: settled the same day, see below.
- **`min` and `max` go in a part `RANGE`** (left to the assistant: "je te laisse réfléchir [...] pouvoir mettre un min/max [...] une range de valeurs"). They only exist together, for a number field: the rule of the schema puts them in a part of their own. `BOUND` stays a box, because a bound is a number or a signal and says which. In the JSON: `"range": { "min": { "source": "typed", "typed_value": 0 }, "max": { "source": "signal", "signal": "…" } }`.
- **The default unit of a typed bound, explained** (Product Owner: "Et où, le default unit ?"): it is the default unit of the quantity of the signal shown, set on the Units page (kilogram for a mass). The user types the bound in the display unit of the preset; the file keeps it in the default unit (decision 0051). The labels of the schema now say it.

## Settled on 2026-11-21 (enum item and bounds)

The Product Owner answered the two questions left by decision 0055 in the questionnaire, with the option the assistant advised each time. Decision 0056 (accepted, 2026-11-21) records them: it specifies decisions 0032 (the column of an enum) and 0041 with 0055 (the signal of a bound).

- **`ENUM_ITEM.display_text` becomes `display_name`** (Product Owner: "Oui, display_name"): the same word as for an identifier and a signal field, "Display name" on screen. Its rule does not change: what people read, never sent to the model.
- **The signal of a bound has the same quantity as the signal shown** (Product Owner: "Même grandeur obligatoire"): an input, integer or real, of that quantity, so that a speed is bounded by a speed and both compare in the same default unit. The list of the bound offers only these inputs.

## Names made even on 2026-11-21

Asked by the Product Owner on 2026-11-21 ("voir tout, tout, tout [...] comment c'est nommé, et donc homogénéiser le tout"). Every box, field, link, choice list and value was read again against one set of rules, now written at the head of this file. What changed:

- **Two things had the same name**: `typed_value` was both the type of a value read by its signal (`COMMAND_TARGET.value`, `PRESET_VALUE.default_value`) and the field of a bound typed in the builder. The type becomes `signal_value`; the field keeps `typed_value`, beside `typed_text`.
- **The choice lists are named by one rule**: their field, with the box as prefix for `kind` and `source`. `value_kind` becomes `value_type_kind`, `element_kind` becomes `faceplate_element_kind`, `text_source` becomes `text_content_source`. The others already followed it.
- **A value of several words is joined by underscores**, the same in the schema and in the JSON: `set_signal` (was "set a signal"), `number_field`, `radio_one_line`, `radio_several_lines`. The screens and the draft keep their words for people ("Set a signal", "radio on one line").
- **The two bounds of a range are parts**, so their link says `has, as min` and `has, as max`, not `min` alone, which read like a FK.
- **The JSON keys follow the boxes with no exception**: `command_target` (was `target`, which `LINK.target` already uses), `enum_items` (was `items`), `preset_values` (was `values`), `faceplate_elements` in the preset and in a group (were `faceplate` and `elements`).
- **`name`, `display_name` and `description` are told apart** at the head of the file: `name` for a thing without `id`, `display_name` shown in place of an `id` or a key, `description` to explain.
- Checked and unchanged: the FK fields (`parent`, `icon`, `colour`, `enum`, `quantity`, `signal`, `command`, `identifier`, `unit`, `default_unit`), the field order in every box, `has` and `holds`, the conditions in `when`.
- Left open, because they changed words the Product Owner validated or wait for a research: `id` and `internal_id` (research T5), `button_text`, and the `description` of an icon or a colour. The last two were settled the same day, see below.

## Settled on 2026-11-21 (names)

The Product Owner answered the three questions of the names in the questionnaire, with the option the assistant advised each time. Decision 0057 (accepted, 2026-11-21) records them: it changes the field name of a command button found right the same day.

- **The lists of the JSON keep the name of their box, with no exception** (Product Owner: "Nom de la boîte, sans exception"): `enum_items`, `preset_values`, `faceplate_elements` in a preset and in a group, `command_target`. One rule, and `command_target` is never mistaken for `LINK.target`.
- **`COMMAND_BUTTON.button_text` becomes `display_name`** (Product Owner: "Renommer en display_name"): it is shown in place of the command's `id`, as the label of a signal field is shown in place of the signal's. Empty, the button shows the command's `id`.
- **The short text that names an icon or a colour becomes `name`** (Product Owner: "Renommer en name"): a label for a thing without `id`, shown on hover; `description` stays for a text that explains.

## Changed on 2026-11-21 (boolean texts)

Asked by the Product Owner on 2026-11-21 ("le boolean text, ça serait plutôt dans les presets. Ce serait pas dans le signal directement"). Decision 0058 (accepted, 2026-11-21) records it: it changes decision 0054 on where the two texts are set.

- **`BOOLEAN_TEXTS` leaves `VALUE_TYPE` and becomes a part of `PRESET_VALUE`**, for a boolean signal only, as `DISPLAY_FORMAT` is for an integer or a real: how a value is shown is set in the preset, beside the display unit and the decimals.
- So two presets of the same type may name the states differently ("Running" / "Stopped", "On" / "Off"); the signal itself only says that it is a boolean.
- They are typed in the table of values of the preset (mode Values), in a column for booleans only: assistant's reading, its header and place to confirm (screen MD-07.13b).
- They never go to the model, which gets `true` or `false`; nor in the configuration files sent with it, since they are a matter of display like the display unit: assistant's reading.

## Changed on 2026-11-21 (kind of a measurement)

The Product Owner found `"measurement": { "measure": "value" }` odd in the JSON, and asked whether the field should rather be a type, "soit c'est une valeur, soit c'est une différence"; he left the choice to the assistant ("je te laisse réfléchir").

- **`MEASUREMENT.measure` becomes `MEASUREMENT.kind`**, and its list `measure` becomes `measurement_kind` (assistant's choice). It says which of two alternatives the measurement is, which is what `kind` means everywhere in the schema; `measure` repeated the name of its box (`measurement.measure`) without saying more.
- **Not `type`**: the schema already has `TYPE` and `VALUE_TYPE`, and `measurement.type` beside `value_type` would read as a third kind of type. `kind` is the word the rules give for this.
- **Not `typed`**: in the schema, `typed` means typed by hand in the builder (`typed_value`, `typed_text`), which this is not.
- **The values stay `value` and `difference`**: a point on the scale or a gap between two points, as decision 0020 says. In the JSON: `"measurement": { "quantity": "…", "kind": "difference" }`.
- The earlier sections keep `measure`, as written when they were settled.
- Replaced the same day: the part `MEASUREMENT` is gone, see below.

## Settled on 2026-11-21 (quantity of a number)

The Product Owner asked whether `measurement` was really the best name, and to keep it if it was. It was not: in supervision and simulation a "measurement" is first a value read by a sensor, so an output, and an input setpoint with a `measurement` part read as "this input is a measurement" (assistant's analysis, not sourced). Of the three options of decision 0059, the Product Owner chose the one the assistant advised ("Faire comme FMI, sans partie"). Decision 0059 (accepted, 2026-11-21) records it.

- **The part `MEASUREMENT` is gone**: its two fields go on `VALUE_TYPE`, for an integer or a real only. In the JSON: `"value_type": { "kind": "real", "quantity": "…", "relative_quantity": true }`.
- **`quantity`**: the FK to the quantity, required for an integer or a real (decision 0051). The word of FMI, OPC UA and CLDR (research T2, sources S1, S3, S16).
- **`relative_quantity`**: a boolean, `true` when the value is a difference (a gap between two points), `false` when it is a value (a point on the scale). The word of FMI, `relativeQuantity`, whose offset is then ignored (research T2, section 3.8, source S1). It replaces the list `measurement_kind` and its values `value` and `difference`. It may only be `true` when the quantity has `offers_relative_quantity` (renamed the same day, see below).
- **The rule of the parts gets one written exception**, at the head of this file: these two fields only exist together, but stay on `VALUE_TYPE`, to keep the words of a standard and one level less in the JSON.
- The screens do not change: the column Quantity of the table of signals still offers a quantity or its difference, each with its icon (screen MD-04.9); only the file says it with `relative_quantity`.

## Read again on 2026-11-21 (kind or source)

The Product Owner asked why `TEXT_CONTENT` says `source` and not `kind` "comme partout", thought `source` might be better, left it to the assistant ("à toi d'y réfléchir"), and asked for a pass over the whole JSON on this kind of thing.

- **`source` stays, on `TEXT_CONTENT` and on `BOUND`** (assistant's choice). `kind` says what a thing is, and its other fields change with it: a faceplate element of kind signal has a `signal_field`, one of kind command a `command_button`. A bound is always a number and a text always a text, whatever is chosen: only where the value comes from changes. `source` says it in one word, and each of its values names the field that then holds the value (`typed` → `typed_value` / `typed_text`, `signal` → `signal`, `identifier` → `identifier`), which `kind` would not show. The head of this file now gives that reason.
- **Every field of choice of the JSON read again against this rule**, nothing else changes:
  - `kind` on `LINK`, `VALUE_TYPE`, `COMMAND`, `ENUM` and `FACEPLATE_ELEMENT`: each says what the thing is, and is always there;
  - `direction` on `SIGNAL` and `access` on `SIGNAL_FIELD`: their own word says more than `kind`;
  - `input_kind` stays, not `kind`: the Product Owner's word (2026-11-21), and it only exists in write or override, while a `kind` is always there.
- **`QUANTITY.offers_difference` becomes `offers_relative_quantity`** (assistant's choice, found in the pass): since decision 0059 the signal says `relative_quantity`, and the same idea had two words in the files. The screens keep "difference" for people.
- **The minimum and the maximum of a range**: the same question (Product Owner: "c'est pareil, c'est source, c'est typed ou signal"), the same answer. A bound is always a number; `source` says whether it is typed or read from an input signal.

## Settled on 2026-11-21 (order of the keys)

The Product Owner answered the question of the pass in the questionnaire, with the option the assistant advised ("Le mettre en premier").

- **`kind` or `source` comes right after `internal_id`**, before the links: the reader learns what the object is, then reads the fields that go with it. `{ "source": "identifier", "identifier": "…" }`, `{ "kind": "enum", "enum": "…" }`.
- Changed in the schema and the JSON example: `VALUE_TYPE`, `BOUND`, `TEXT_CONTENT`; the other boxes already had it in that place, or have no link before it.
- `direction`, `access` and `input_kind` keep their place after the links: `SIGNAL_FIELD` starts with the signal it shows (assistant's reading).

## Settled on 2026-11-21 (format key)

The Product Owner answered the question of the check of the schema against the JSON in the questionnaire, with the option the assistant advised ("Règles des fichiers seulement").

- **`"format"` is described in the rules of the files only** ([Files](draft.md#files)): it is the version of the file format, so it belongs to the file, not to an entity. The schema stays the schema of the entities; no box `FILE` is added.
- The JSON examples keep `"format": 1` at the top of the file of a type and of an enum; nothing else changes.
- Still open: whether the catalogue of quantities is one file with one `format` at its top, or one file per quantity (see [Open](#open)).

## Changed on 2026-11-21 (identifier)

Asked by the Product Owner on 2026-11-21 ("dans l'identifiant, on va dégager display name [...] on voit que l'ID [...] Pour une première version, ça va rien casser [...] faut laisser la description").

- **`IDENTIFIER.display_name` is removed**: an identifier has its `internal_id`, its `id` and its `description`. Its `id` is shown wherever it is picked or filled. The earlier sections keep the field, as written when they were settled.
- **The page Identifier (now [Designation](entities/01-designation.md)) draws the identifier alone**, without `TEXT_CONTENT` (assistant's choice, left to it by the Product Owner: "je te laisse décider"): a text content belongs to the faceplate of a preset, and points to the identifier; it stays drawn in the schema of the [Data model](data-model.md), with its link.
- Screen MD-13 loses its column Display name; the identifiers of the placed symbol panel are labelled by their `id`.
- **`IDENTIFIER.required` is added**, a boolean (Product Owner, later the same day: "j'ai complètement besoin de dire si c'est required ou non"). `true`: every placed symbol must have its text (a control ID); `false`: it may stay empty (a location, for context).
- Settled in the questionnaire the same day: a required text is asked on **every placed symbol**, whether or not its faceplate shows it ("Sur tous les symboles placés"); left empty, it **warns and never blocks** ("Avertir sans bloquer").
- **Field order `internal_id`, `id`, `required`, `description`** (assistant's choice, left to it by the Product Owner: "un ordre le plus logique possible [...] à toi de décider"): what the identifier is, what it asks for, then the text that explains it, last as in every box. It follows the rule of the head of this file.
- Usually three identifiers, four at most (Product Owner: "trois, quatre grands max"): an order of size, not a limit.
- **`required` is `false` for a new identifier** (Product Owner, later the same day: "Le booléen required, ce serait genre false").
- **The schema of an entity page shows only the structure** (Product Owner, same day): type, name, key, required or optional and the default value; what a field means is in the table below it. Written in [Entities](entities/README.md#how-an-entity-file-is-written).

## Changed on 2026-11-21 (entity files and global rules)

Asked by the Product Owner on 2026-11-21 ("c'est des règles globales").

- **Required and default leave the schema for the table**: column `Required`, with `✓` when required.
- **The section The file of an entity keeps its JSON Schema only**: no text, no example. A tag **File** under the status says the entity has a file of its own.
- **The rules shared by every file move to [Files](files.md)**: the `format` key, how the schema becomes JSON, the order of the keys. New rule: a file whose key order is not respected is still read, and is written again in the order of the schema when saved.
- **No section Product Owner context** on an entity file or on Files (Product Owner, later the same day: "ça ne sert strictement à rien"): the history stays in these notes.
- **No Where it is used and no status sentence on an entity file** (Product Owner, same day): a table of versions (version, date, status, change) and a table of tags (`File`) open the file instead.

## Settled on 2026-11-21 (identifier answers)

- `internal_id` is the primary key, so it is unique; `id` is never empty (it is required).
- The configuration files of a synoptic are always made, even with an empty required text; the software checks each object and lists where the errors are.
- The file of an entity is named after its list (`identifiers.json`), a name reserved for it; where files are placed is left to the software architecture.
- A text is never an empty string: empty is `null`; the JSON Schema says it with `minLength: 1`.
- The names of every term of the data model go to one research (T5, rewritten).

## Applied on 2026-11-22 (names, research T5)

Asked by the Product Owner on 2026-11-22 ("applique ce que la recherche a trouvé [...] je te dirai si je suis d'accord ou pas"): the advice of the research T5 (`research/t5-recherche-documentaire-les-noms-de-tous/rapport.md`, sections 3.2, 3.3 and 6) is applied, to be reviewed by the Product Owner. Decision 0064 (proposed) records it. The earlier sections keep the old names, as written when they were settled.

- **`id` and `internal_id` stay** (report, 3.2): a readable key written by the user and a surrogate key set by the software, as Home Assistant, Google and Kubernetes do. The risk is the swap with standards where `ID` is the UUID (AutomationML); three rules answer it, written in [Files](files.md#the-two-keys-of-an-entity) and at the head of this file: `id` is never a UUID, `internal_id` always is and every FK holds one, `internal_id` never leaves the software; plus a table of matches for any export.
- **`IDENTIFIER` becomes `DESIGNATION`** (report, 3.3, confidence low): the word of IEC 81346, which covers the tag (`P-101`) and the location; "identifier" also named `id` and `internal_id` in French, and promised a uniqueness that a location has not. File `designations.json`, value `designation` of `text_content_source`, field `TEXT_CONTENT.designation`; the entity file is now [Designation](entities/01-designation.md).
- **Six names changed for a precise collision** (report, 6, decision 3):
  - `colour` → `color`, `COLOUR` → `COLOR`, `colours` → `colors`: the word of design tokens, CSS and SVG;
  - `LINK.target` → `address`: in HTML, `target` says where a link opens, not where it goes;
  - `radio_one_line` → `radio_horizontal`, `radio_several_lines` → `radio_vertical`: the orientation of a radio group in a design system;
  - `FAMILY` → `UNIT_SYSTEM`, `families` → `unit_systems`: a system of units, and "family" also names families of equipment;
  - the kind of faceplate element `description` → `paragraph`: `"kind": "description"` read like the description of the element;
  - the file key `format` → `format_version`: `format` is a keyword of JSON Schema.
- **Kept, with their meaning written**: `ENUM_ITEM.key` (the number sent to the model, at the head of this file), `override` (the same word in `command_kind` and `access`), `default_value`, `name` (a label here, an identifier in FMI), `display_name`, `description` and every other name.
- The screens and the draft keep their words for people for now; the other parts (synoptics, symbols, screens) still say "identifier": to change once the Product Owner confirms `DESIGNATION`.

## Settled on 2026-11-22 (names, answers of the Product Owner)

The Product Owner reviewed what was applied above (questionnaire of 2026-11-22). Decision 0064 is accepted.

- **`DESIGNATION` is kept** ("Garder Designation"). The synoptics and the screens say "designation" too: the page Designations (MD-13), the designation texts of a placed symbol. The draft and the earlier decisions keep "identifier", as written when they were settled.
- **The six other names are kept** ("Tous OK"): `color`, `address`, `radio_horizontal` / `radio_vertical`, `UNIT_SYSTEM`, `paragraph`, `format_version`.
- **`PRESET_VALUE.default_value` becomes `start_value`** (answer: "Valeur au démarrage"): the value the model gets when it starts, the word of FMI (`start`). It is also the value shown before the model sends anything. The screens say "Start value"; the value a synoptic changes for a placed symbol is the start value too (`VALUE_CHANGE.start_value`).

## Settled on 2026-11-22 (palettes)

Said by the Product Owner on 2026-11-22 ("les couleurs sont dans des palettes [...] Je ne veux pas que ce soit stocké à part [...] une palette par fichier [...] Comme ça, on peut les ajouter ou les enlever"). Decision 0065 recorded it; decision 0066 replaces it, with the color's `name` made optional.

- **A color is kept only inside its palette**, never in a file or a list of its own.
- **One palette per file**, never every palette in one file: a palette is added or removed with its file.
- **Two entity files** (the Product Owner's proposal): [Color](entities/02-color.md), its box and its schema only; [Palette](entities/03-palette.md), its box, its schema and the schema of its file.
- **A palette's file is named after the palette**, never after its `internal_id` (answer to the questionnaire: "Faut que ça ait un sens pour un humain [...] Si on met un internal ID, c'est incompréhensible"). So a palette's `name` is unique, and renaming a palette renames its file. How a name becomes a file name is written in [Files](files.md#the-name-of-a-file): simplified (answer: "Simplifié"), in kebab-case, the Product Owner leaving the choice between kebab-case and snake_case to the assistant.
- **The `name` of a color is optional** (Product Owner, later the same day: "le nom des couleurs, pour moi, faut pas qu'ils soient obligatoires [...] Le RGBA, il va suffire"; decision 0066, which replaces 0065): a palette can be made of values only. As every empty field, a color without a name has `name` set to `null`.
- **The `name` of a color, when given, is not unique**: two colors of a palette may share it (answer to the questionnaire of 2026-11-22: "Non, deux couleurs peuvent avoir le même nom"). This replaces the earlier answer "Non, unique", given while the name was required.
- **Every file holds `format_version`, then one object named after what it holds** (answer: "Objet nommé"), the palette as the type and the global enum: the two examples of the [Data model](data-model.md) were rewritten so.
- **A color has an opacity** (answer: "Avec transparence"): its value is `#rrggbbaa`, always eight digits, `ff` being opaque; the box says `rgba`.
- `name` is required for a palette, never empty; a palette holds at least one color, as the link `|{` of the schema says.
- **No table of the fields on an entity file** (Product Owner, same day: "le tableau [...] c'est un doublon du schéma JSON [...] il sert à rien, strictement rien"): an entity file shows its schema, then its JSON Schema, which Arsenal draws as a tree; each field is described once, in its `description`. This replaces the table set on 2026-11-21; the three entity files were changed so.

## Settled on 2026-11-22 (color of a type, configuration folders)

Said by the Product Owner on 2026-11-22, answering the two open questions of the [Palette](entities/03-palette.md), then the questionnaire that followed (decisions 0070 and 0071).

- **A type keeps the color it picked, even when its palette is removed** (Product Owner: "j'ai pas envie que ça soit cassant [...] inscrire que la couleur vient d'une palette, mais qu'on mette aussi la couleur. Comme ça, si la palette est supprimée, la couleur, elle reste"). `APPEARANCE` holds both: `color`, the FK to the color picked in a palette, and `color_value`, a copy of its value (`#rrggbbaa`). The rule belongs to the type, not to the palette (Product Owner: "j'ai pas l'impression que ce soit dans la palette"), so the [Color](entities/02-color.md) file no longer says that a type points to it.
  - Removing a palette never empties the color of a type: the type does not follow its parent's color then. This answers the first open question of the palette.
  - Assistant's reading, to confirm: `color` is kept as written when its palette is removed, so that putting the palette's file back links the type again; both are `null` when the type has no color of its own.
  - **While its palette exists, a type follows the value of its color** (Product Owner, answering the questionnaire the same day; decision 0070): when the color changes in its palette, `color_value` is refreshed. The copy is only used once the palette is gone.
- **Two configuration folders** (Product Owner: "un dossier de configuration logiciel et un dossier de configuration de l'utilisateur"): the software's holds what it ships, the user's what the user adds. The user may change the software's files by hand ("s'il les casse, c'est de sa faute, et point barre"); their own files are theirs. Written in [Files](files.md#the-two-configuration-folders). It answers the second open question of the palette: the user adds their own palettes in their folder; which palettes ship stays with the design system.
  - **Which palettes ship, and their names, are chosen once the screens are drawn** (Product Owner, same day: "on verra ça une fois que l'UI sera faite"): there may be several (one for the theme of the software, one for the colors of the icons…). Nothing to write in Metadata until then; the open question of the palette is closed.
  - **The same file name in both folders: the user's file is offered** (Product Owner, answering the questionnaire the same day; decision 0071).
  - Which files go in the two folders beside the palettes: left for later ("on verra ça après"), open in [Files](files.md#open-questions).
- Also done: the box `COLOR` of the [Data model](data-model.md) loses "optional, shown on hover", as its entity file already did.

## Settled on 2026-11-22 (enums in one file)

Said by the Product Owner on 2026-11-22 ("les enums, non, c'est un truc d'entreprise, tu vas pas les partager [...] y a qu'un fichier, un peu comme les désignations"). Decision 0072 records it.

- **Every enum is kept in one file, `enums.json`**, like the designations: enums belong to one company and are not shared, while a palette may be exported and imported, hence one file per palette. An enum per file would also make very small files.
- **Two entity files** (the Product Owner's proposal): [Enum item](entities/04-enum-item.md), its box and its schema only, kept inside its enum; [Enum](entities/05-enum.md), its box, its schema and the schema of its file.
- The example of the [Data model](data-model.md) now shows the file `enums.json`, with a global enum and a template.
- **A template keeps its items** in `enum_items`, unused, so that going back to global finds them (draft, Enums: changing the kind loses nothing). Assistant's reading of that rule in the file.
- **The items of a template follow the schema of an enum item exactly** (Product Owner, 2026-11-22: "ça follow exactement la même chose, sauf que ce sera défini par les gens qui font les vues"): `internal_id`, `key`, `display_name`, `description` (which may be `null`), filled on each placed symbol. A template is for enums known only on the view, such as the positions of a switch. Written in the introduction of [Enum item](entities/04-enum-item.md).
- Extra properties hung on the items of an enum or a template (a color per position, for example) will be another object, linked to the enum, settled with the symbol editor: nothing is added to the item (Product Owner, same day: "faut pas intégrer ça dans l'item pour l'instant").

## Settled on 2026-11-22 (unique ids of enums and designations)

Said by the Product Owner on 2026-11-22, answering the questionnaire ("Unique, pour les enums et les désignations"), with a note on the items.

- **The `id` of an enum is unique among the enums**, and **the `id` of a designation unique among the designations**: both are written in configuration files and picked in lists. Written in the `description` of each `id`.
- **The name of an item is unique in its enum, not across enums** (Product Owner: "tu peux avoir deux enums avec une même désignation à l'intérieur, parce que c'est deux thèmes différents"): two enums may both hold an item named the same. Assistant's reading of the note, which says "désignation" for the name of an item (`display_name`), to confirm. Written in the `description` of `display_name` in [Enum item](entities/04-enum-item.md).

## Noted on 2026-11-22 (format of the ids, idea)

An idea of the Product Owner, said on 2026-11-22 as a note, not a decision ("ça me passe par la tête"). Nothing in the schema changes for now.

- **A settings page to choose the format of every `id`**: a regular expression per kind of `id`, kept in the settings configuration file ("dans le fichier de config des paramètres"). When an `id` typed in the software does not follow it, the software says so ("ça ne respecte pas le format attendu").
- **The user writes their own expressions in that file** and adds others there ("qu'on puisse faire sa propre regex en fichier de conf et rajouter des trucs en fichier de conf").
- The Product Owner first hesitated on where the expression is kept ("qui ne serait pas du tout dans les fichiers de config, ou je ne sais pas quoi"), then said the settings file: assistant's reading, to confirm.
- Open: whether the software ships a format or none, since the Product Owner wanted no rule on how an ID is written (2026-11-17, [whole draft](draft.md#flags)); a message only or the `id` refused; one expression per entity (type, signal, enum, designation…) or shared ones; which configuration folder holds the settings file ([Files](files.md#the-two-configuration-folders)).

## Settled on 2026-11-22 (icon sets)

Said by the Product Owner on 2026-11-22 ("c'est un peu comme les couleurs [...] des fichiers d'icônes différentes [...] ça, c'est des icônes carbone, ça, c'est des icônes Microsoft [...] ça permettra de surcharger les icônes du logiciel"). Decision 0073 records it: it replaces the rule of the draft by which the icons are one list shipped with the program, which the user cannot add to.

- **The icons are kept in icon sets, one set per file**, as the colors in their palettes: a set gathers icons of one style or one origin (Carbon's, Microsoft's…), and is added or removed with its file.
- **`ICON_SET`** (the name left to the assistant: "il va falloir que tu trouves un nom"): "icon set" is the usual word for such a set; "library" is kept for the symbols, and "pack" says less. Its `name` is unique, since it names the file (`carbon.icon-set.json`).
- **Two entity files** (the Product Owner's request): [Icon](entities/06-icon.md), its box and its schema only, kept inside its set; [Icon set](entities/07-icon-set.md), its box, its schema and the schema of its file.
- **The user's sets go in their configuration folder**; a user's set of the same file name replaces the software's (decision 0071): that is how the icons the software ships are overridden (Product Owner, answering the questionnaire the same day). Only whole sets are replaced: neither one icon of a set nor the icons of the software's own interface.
- **A type keeps the icon it picked, even when its icon set is removed** (Product Owner, answering the questionnaire the same day), as for its color: `APPEARANCE` holds `icon`, the FK to the icon picked in a set, and `icon_drawing`, a copy of its SVG, refreshed while the set exists. Both are `null` when the type has no icon of its own (assistant's reading, as for the color).
- **The `name` of an icon is optional, and two icons of a set may share it** (Product Owner, answering the questionnaire the same day), as for a color: the key is always written, `null` when empty.
- **The drawing of an icon is an ordinary SVG**, which may have a `viewBox` (Product Owner, same day: "c'est un SVG normal").
- **An icon is drawn with fills only, never strokes**, even its thin lines (Product Owner: "même si c'est des bords fins [...] faut que ce soit du fil, et puis basta"): the color of the type goes on the fills.
- **The software puts the color of the type on every fill of the drawing**, whatever color the drawing gives it: an icon is always of one color, and any icon set works as it is, with nothing to prepare (Product Owner, answering the questionnaire the same day). `currentColor` is not used.
- **An icon drawn with a stroke, against the rule, is shown as it is** (Product Owner, same questionnaire): the software does not check the drawings; its stroke may not take the color of the type.
- **An icon without a name shows no name**: nothing stands in its place, the user gives one if they want it; and the icons are not searched (Product Owner, same day: "s'il n'y a pas de nom, il n'y a pas de nom [...] faire des recherches sur les icônes, je vois pas trop l'intérêt"). A color without a name shows its RGBA value (same message).
- **An icon set says nothing of its origin nor of its licence** (Product Owner, same day: "je pense qu'on s'en fout [...] je suis pas là pour faire des trucs trop chiants"): no field for them.
- **The icon sets the software ships are drawn for it, following its own rules** (Product Owner, same day: "on va les faire selon des règles"): no licence of others to keep.
- **Which icon sets ship, and their names, are chosen in due time**, as for the palettes. The Product Owner gave, with a doubt, an example of a file name: `synoptic-studio.icon-set.json` ("un truc du genre. J'en ai aucune idée").

## Settled on 2026-11-22 (unique id of a flag)

Said by the Product Owner on 2026-11-22, answering the questionnaire ("Unique dans le type et ses parents").

- **The `id` of a flag is unique among the flags of its type and of the types it inherits from**: a placed symbol has the flags of its type and of its parents, so two flags with the same `id` would write the same key twice in the configuration files. Written in the `description` of `id` in [Flag](entities/08-flag.md). It answers the question left open in the [whole draft](draft.md#flags) on 2026-11-17; the format of an `id` stays free.

## Settled on 2026-11-22 (descriptions of the documentation)

Said by the Product Owner on 2026-11-22, answering the questionnaire ("Facultative", twice). Flag v1 stays `Draft` at their request.

- **The description of a link is optional**: without it, only the path or the URL is shown. Written in [the Link entity](entities/09-link.md) and in the [whole draft](draft.md#the-links).
- **The description of the documentation of a type is optional**: a new type has none. Written in [Documentation](entities/10-documentation.md) and in the [whole draft](draft.md#the-description).

## Settled on 2026-11-22 (one file per quantity)

Said by the Product Owner on 2026-11-22 ("on va avoir un fichier par quantité [...] ça, ça contient tout ça"), who left the rest to the assistant ("à toi de gérer").

- **Each quantity is one file, `<name>.quantity.json`**, which holds the whole quantity: its unit systems, their units and the conversion of each unit. It answers the open question of the format key and of [Files](files.md#open-questions).
- **Four entity files**: [Conversion](entities/11-conversion.md), [Unit](entities/12-unit.md) and [Unit system](entities/13-unit-system.md), kept inside the quantity's file; [Quantity](entities/14-quantity.md), with the schema of its file. The example of the [Data model](data-model.md) now shows the whole file.
- **The `name` of a quantity is unique**, since it names its file, by the rule of [Files](files.md#the-name-of-a-file). Assistant's reading of that rule.
- **`offers_relative_quantity` is `false` unless set** (assistant's reading): most quantities only multiply.
- Which configuration folder holds the quantity files stays open in [Files](files.md#open-questions).

## Settled on 2026-11-22 (names and symbols of units)

The Product Owner answered the three questions of the quantity files in the questionnaire, each with the advised choice.

- **The `name` of a unit system is unique among the unit systems of its quantity, and the `name` of a unit among the units of its quantity** ("Uniques dans leur grandeur"): two "metric" or two "kelvin" in one quantity would mean nothing. Written in [Unit system](entities/13-unit-system.md) and [Unit](entities/12-unit.md).
- **A unit's `symbol` may be `null`** ("Symbole facultatif"): nothing is written after the value, such as the unit 1 of a count (12, not 12 1). Written in [Unit](entities/12-unit.md).
- **A difference shows the same symbol as a value** ("Le même : « °C »"): a rise of 5 °C is written 5 °C, never Δ°C; the column Quantity of the table of signals already shows the icon of a difference. Written in [Unit](entities/12-unit.md).

## Noted on 2026-11-22 (syntax of the formulas)

- **The syntax of the formulas of a conversion goes to a documentary research** (Product Owner: "il va falloir faire une grosse recherche documentaire"), a task of the specification feature: the operators, functions and constants needed to convert from one unit to another of the same quantity, the grammar, and an evaluation without `eval`. It replaces "chosen with the architecture" of decision 0049.
- Its scope is one quantity at a time, never everything into everything (Product Owner: "pas convertir tout en tout"): converting a temperature into an energy would need other quantities and stays out.
- **Its result is written in a file of its own in Metadata, not in the entity files** (Product Owner: "ça n'ira pas dans les entités"); [Conversion](entities/11-conversion.md) will link to it. The question left the open questions of Conversion and of this page.

## Not in the schema yet

- The texts filled on each placed symbol: with the synoptic.

## Open

- The default unit and the model unit (decision 0024): open in [Quantity](entities/14-quantity.md#open-questions).
- An integer signal shown in another unit than its default unit: a number typed there may not give a whole number in the default unit (24.17 rps is 1450.2 rpm). Rounded to the nearest whole number, or refused?
- The names of the two quantities added for numbers that measure nothing physical: "ratio" and "count" for now.
- The default number of decimals of a preset: 2 or 3 (Product Owner, 2026-11-19: "qui serait de 2 ou de 3"), and whether it is fixed by the software or set for the project.
- The names of the nested parts (`APPEARANCE`, `VALUE_TYPE`, `BOOLEAN_TEXTS`, `COMMAND_TARGET`, `DISPLAY_FORMAT`, `SIGNAL_FIELD`, `RANGE`, `BOUND`, `COMMAND_BUTTON`, `TEXT_CONTENT`, `CONVERSION`) and of `FACEPLATE_ELEMENT`: working names.
- The two texts of a boolean, in the preset: required, or "true" and "false" when empty (assistant's reading)? Never in the configuration files sent with the model, since they are display only (assistant's reading, since decision 0058)?
- `SIGNAL_FIELD` starts with its signal, then `access`: the assistant's reading of the order of the keys, to confirm.
- The `internal_id` of the boxes nothing points to in this schema (found on 2026-11-21): `LINK`, `FACEPLATE_ELEMENT`, `UNIT_SYSTEM`, and for now `FLAG` and `PRESET` (a placed symbol will likely point to its preset and to its flags, assistant's reading). The rule says that a box without `internal_id` is never pointed to, not that a box with one must be. Keep them all, for stable files and for links to come, or remove those nothing will ever point to? To settle when each object is validated.
- Is the `name` of a preset unique in its list? (A palette's, an icon set's, a quantity's, and in its quantity a unit system's and a unit's are; a color's and an icon's are optional and may be shared: settled on 2026-11-22.) To say on its entity file (research T5, open question 3).
- `UNIT.symbol` and the symbol of Synoptic Studio (the drawing placed) share a word: a glossary should say both meanings (research T5, 3.8).
