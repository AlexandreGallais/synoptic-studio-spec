# Screens of Metadata

> [Home](../README.md) › [Screens](README.md) › Metadata

Status: draft, written by the assistant on 2026-11-11 from the validated [Metadata](../metadata/README.md) pages, then reviewed with the Product Owner the same day (tree on the left, order of the parts, General complete, description modes, links, signals, commands, enums, units), and on 2026-11-16 from the review of the wireframes (navigation bar, list on the left and panel on the right, libraries of types removed). It adds no rule. Kinds, statuses and the [layout rules](README.md#layout-rules) are explained in the [guide of this folder](README.md).

## MD-00 · Navigation bar of Metadata

Path: on the far left of every screen of Metadata (Product Owner, 2026-11-16).

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-00.1 | Types | Button (icon) | Opens [MD-01](#md-01--types-the-tree-and-the-type-editor). | Decided | [Layout rules](README.md#layout-rules) |
| MD-00.2 | Units | Button (icon) | Opens [MD-08](#md-08--units). | Decided | [Layout rules](README.md#layout-rules) |
| MD-00.3 | Enums | Button (icon) | Opens [MD-09](#md-09--enums). | Decided | [Layout rules](README.md#layout-rules) |

Gaps:

- Which icons (to choose with the design system). Going from Metadata to the symbol mode is done in the top bar (see the [layout rules](README.md#top-bar-of-the-window)).

## MD-01 · Types: the tree and the type editor

Path: Metadata › Types.

The tree is on the left, as in a code editor, just right of the navigation bar; the selected type is edited on the right, its parts in a fixed order.

```mermaid
block-beta
    columns 4
    rail["MD-00 bar"] tree["Type tree"] editor["Type editor: General, Documentation, Signals, Commands, Faceplate, Presets"]:2
```

```mermaid
mindmap
  root((MD-01 Types))
    Type tree, on the left
      Plus on the title, always shown
      Search field under the title
      Types with icon and colour
      Plus on a type, on hover
      Select a type
      Right click, Delete
      No rename by double click
    Type editor, in this order
      1 MD-02 General
      2 MD-03 Documentation
      3 MD-04 Signals
      4 MD-05 Commands
      5 MD-06 Faceplate
      6 MD-07 Presets
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-01.1 | Type tree | Tree | On the left. Shows each type with its icon and colour. A click selects the type. | Decided | [Types](../metadata/01-types.md), [Icons](../metadata/02-icons.md) |
| MD-01.2 | Double click on a type | — | Does **not** rename: the name changes in General only. | Decided | [Types](../metadata/01-types.md) |
| MD-01.3 | Create a child type | Button (+), on hover | On the right of each type, shown when the mouse is over it; creates a type under it, with a default name. | Decided | [Types](../metadata/01-types.md) |
| MD-01.3b | Create a root type | Button (+), always shown | On the title "Type tree". Its look worries the Product Owner; kept. | Decided (look: Open) | [Types](../metadata/01-types.md) |
| MD-01.4 | Delete a type | Right click › menu › Delete | A menu of options opens on a right click; Delete is one of them. | Decided | [Types](../metadata/01-types.md) |
| MD-01.5 | Parts of the type | Open: four proposals | In this order: General, Documentation, Signals, Commands, Faceplate, Presets. Tabs, a column of parts, a strip of icons, or under the type in the tree. | Decided (order), Open (display) | [Types](../metadata/01-types.md) |
| MD-01.6 | Search | Text field | Under the title "Type tree". | Decided | [Types](../metadata/01-types.md) |

Gaps:

- Which other options the right-click menu holds (duplicate, rename?), and whether the user is warned that symbols lose their type on a delete.
- Fold arrows on the branches: drawn, never said.
- The parts of the type: see the four proposals in [Types](../metadata/01-types.md#the-parts-of-a-type-four-proposals) and in the Figma file.

## MD-02 · General

Path: Metadata › Types › a type › General. Complete: nothing more is needed (Product Owner, 2026-11-11).

```mermaid
mindmap
  root((MD-02 General))
    Name
      Read only
      Edit button
      Save button
    Parent
    Icon
      Predefined list
      Reset to the parent
    Colour
      Fixed palette
      Reset to the parent
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-02.1 | Name | Text field | Read only until Edit is clicked. The model identifier, readable (`centrifugal_pump`). | Decided | [Types](../metadata/01-types.md) |
| MD-02.2 | Edit | Button | Makes the name editable. | Decided | [Types](../metadata/01-types.md) |
| MD-02.3 | Save | Button | Saves the new name. No warning, no confirmation dialog. | Decided | [Types](../metadata/01-types.md) |
| MD-02.4 | Parent | not said (select or tree) | Changed here only. | Decided | [Types](../metadata/01-types.md) |
| MD-02.5 | Icon | not said (list of icons) | One icon of the predefined SVG list. No import. | Decided | [Icons](../metadata/02-icons.md) |
| MD-02.6 | Colour | Colour (palette only) | One colour of a fixed palette; no free colour. | Decided | [Icons](../metadata/02-icons.md) |
| MD-02.7 | Reset icon, reset colour | Button | Shown when the type overrides its parent's choice; makes it follow the parent again. | Decided | [Icons](../metadata/02-icons.md) |

Gaps:

- Does the parent change follow the same Edit and Save steps as the name?

## MD-03 · Documentation

Path: Metadata › Types › a type › Documentation.

```mermaid
mindmap
  root((MD-03 Documentation))
    Description
      View mode
        Default when not empty
      Edit mode
        Visual editor with a tool bar
        Default when empty
      Markdown mode
        Raw text
    Links
      Path to a file or a folder
      URL
      Description of the link
      Open
        A folder, never a file
        A URL in the browser
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-03.1 | Description, view mode | Rendered text | Shown by default when the type already has a description. | Decided | [Documentation](../metadata/03-documentation.md) |
| MD-03.2 | Description, edit mode | Editor (visual) | A "what you see is what you get" editor with a formatting tool bar; shown by default when the description is empty. | Decided | [Documentation](../metadata/03-documentation.md) |
| MD-03.3 | Description, Markdown mode | Editor (raw text) | For those who write Markdown faster; the user switches between edit and Markdown at any time. | Decided | [Documentation](../metadata/03-documentation.md) |
| MD-03.4 | Go to edit | not said (button) | From the view mode to the edit mode. | Implied | [Documentation](../metadata/03-documentation.md) |
| MD-03.5 | Links | List | Each link: a path or a URL, and a description. | Decided | [Documentation](../metadata/03-documentation.md) |
| MD-03.6 | Add a path | Button + selection window | The server opens a window; only the path is kept (`W:/...`). A file or a folder. | Decided | [Documentation](../metadata/03-documentation.md) |
| MD-03.7 | Add a URL | Text field | Typed or pasted. | Decided | [Documentation](../metadata/03-documentation.md) |
| MD-03.8 | Description of a link | Text field | Plain text, not Markdown. | Decided | [Documentation](../metadata/03-documentation.md) |
| MD-03.9 | Open | Button (not said) | Always a folder: the one that contains the file, or the folder itself. Never launches a file or a program. A URL opens in the browser. | Decided | [Documentation](../metadata/03-documentation.md) |
| MD-03.10 | Edit or remove a link | not said | — | Implied | — |

Gaps:

- How does the user leave the edit mode: a Save button, or a click outside?
- How is a link edited or removed? Can links be reordered?

## MD-04 · Signals

Path: Metadata › Types › a type › Signals.

The list of signals is on the left, the panel of the selected signal on the right (Product Owner, 2026-11-16): a panel under the list would move down as the list grows.

```mermaid
block-beta
    columns 3
    list["List of signals: own, then inherited"] panel["Panel of the selected signal: Edit, fields, Save"]:2
```

How the fields depend on each other: the type decides which fields exist; the quantity decides which units can be chosen.

```mermaid
flowchart LR
    T["Type"] -->|"enum"| E["Enum: a link to the Enums page"]
    T -->|"integer or real"| Q["Quantity: none, a quantity, or a difference"]
    T -->|"integer or real"| B["Minimum and maximum, in the model unit"]
    T -->|"boolean or text"| N["No other field"]
    Q -->|"a quantity is chosen"| U["Model unit: the quantity's default, or another of its units"]
    U --> B
```

```mermaid
mindmap
  root((MD-04 Signals))
    List of signals, on the left
      Own signals
      Inherited signals
      Enum line shows the enum name
        Hover shows its items
    Panel of the selected signal, on the right
      Edited as a whole
      Edit button
      Name
      Type
      Enum, for an enum
      Quantity, optional
      Model unit, with a quantity
      Minimum and maximum
      Direction, input or output
      Save button
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-04.1 | List of signals | List | On the left. Own and inherited signals. A click selects a signal and shows it in the panel on the right. | Decided | [Signals](../metadata/04-signals.md), [Layout rules](README.md#layout-rules) |
| MD-04.2 | Enum on a signal line | — | The line shows the enum's name; hovering it shows its items. | Decided | [Signals](../metadata/04-signals.md) |
| MD-04.3 | Inherited signals | not said | How they look in the list (greyed, with the parent's name) is not said. | Implied | [Signals](../metadata/04-signals.md) |
| MD-04.4 | Add a signal | not said (button) | — | Implied | [Signals](../metadata/04-signals.md) |
| MD-04.5 | Edit, Save | Button | In the panel on the right. The whole signal goes into edit mode, then is saved: nothing changes by mistake; no warning. | Decided | [Signals](../metadata/04-signals.md) |
| MD-04.6 | Name | Text field | Model identifier. A sub-type cannot reuse an inherited name. | Decided | [Signals](../metadata/04-signals.md) |
| MD-04.7 | Type | not said (select) | Integer, real (64-bit double), boolean, text, enum. | Decided | [Signals](../metadata/04-signals.md) |
| MD-04.8 | Enum | not said (select) | Only for the type enum: an enum of the Enums page, as a link. | Decided | [Enums](../metadata/06-enums.md) |
| MD-04.9 | Quantity | not said (select) | Optional, integer and real only. A quantity or a difference (a difference sits under its quantity). | Decided | [Units](../metadata/05-units.md) |
| MD-04.10 | Model unit | not said (select) | Only with a quantity. Default: the quantity's model unit; another unit of the same quantity can be chosen. | Decided | [Units](../metadata/05-units.md) |
| MD-04.11 | Minimum, maximum | Number field | Integer and real only; indicative; in the model unit. | Decided | [Signals](../metadata/04-signals.md) |
| MD-04.12 | Direction | not said (radio) | Input or output of the model. | Decided | [Signals](../metadata/04-signals.md) |
| MD-04.13 | Delete a signal | not said | Its effect on symbols is written; the control is not. | Implied | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |

Gaps:

- Are the fields that do not apply hidden or greyed (quantity for a boolean, enum for a real)?
- Order of the signals: by creation, by name, or chosen by the user?

## MD-05 · Commands

Path: Metadata › Types › a type › Commands.

As for the signals, the list of commands is on the left and the panel of the selected command on the right ([layout rules](README.md#layout-rules)).

```mermaid
mindmap
  root((MD-05 Commands))
    List of commands
    A command
      Name
      Kind
        Set a signal
          Target signal
          Fixed value
          Typed value, of the target's type
        Trigger
          Name only, its identifier
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-05.1 | List of commands | List | On the left; the selected command in a panel on the right. | Implied (layout: Decided) | [Commands](../metadata/07-commands.md) |
| MD-05.2 | Add a command | not said (button) | — | Implied | [Commands](../metadata/07-commands.md) |
| MD-05.3 | Name | Text field | For a trigger, the name is its identifier and all it has. Symbols follow a rename (internal identifier). | Decided | [Commands](../metadata/07-commands.md) |
| MD-05.4 | Kind | not said (radio) | Set a signal, or Trigger. | Decided | [Commands](../metadata/07-commands.md) |
| MD-05.5 | Target signal | not said (select) | For "Set a signal". | Decided | [Commands](../metadata/07-commands.md) |
| MD-05.6 | Value: fixed or typed | not said (radio) | — | Decided | [Commands](../metadata/07-commands.md) |
| MD-05.7 | Fixed value | Field of the target signal's type | The value sent (example: `running` = `true`). | Decided | [Commands](../metadata/07-commands.md) |
| MD-05.8 | Typed value | — | The person types a value of the target signal's type: a number, a text, or an item of an enum. | Decided | [Commands](../metadata/07-commands.md) |
| MD-05.9 | Delete a command | not said | Its effect on symbols is written; the control is not. | Implied | [Libraries and symbols](../symbols/01-libraries-and-symbols.md) |

Gaps:

- Is a command edited as a whole with Edit and Save, like a signal?
- A typed value on a boolean signal: allowed (a switch), or always a fixed value?
- Can a command target a signal of any direction, or only an input?

## MD-06 · Faceplate

Path: Metadata › Types › a type › Faceplate.

The list of entries is on the left and the panel of the selected entry on the right ([layout rules](README.md#layout-rules)). The Product Owner will go over this screen again later (2026-11-16).

```mermaid
mindmap
  root((MD-06 Faceplate))
    Entries
      Signal entry
        Signal
        Read or write
        Display unit
        Input of an enum
      Command or trigger entry
        Picked in the list of commands
        Name shown
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-06.1 | Entries | List | Signal entries and command or trigger entries. | Decided | [Faceplates](../metadata/08-faceplates.md) |
| MD-06.2 | Add a signal entry | not said (button) | — | Implied | [Faceplates](../metadata/08-faceplates.md) |
| MD-06.3 | Signal | not said (select) | The signal shown. | Decided | [Faceplates](../metadata/08-faceplates.md) |
| MD-06.4 | Read or write | not said (radio) | — | Decided | [Faceplates](../metadata/08-faceplates.md) |
| MD-06.5 | Display unit | Select | Units of the signal's quantity. | Decided | [Faceplates](../metadata/08-faceplates.md) |
| MD-06.6 | Input of an enum | Select | Radio on one line, radio on several lines, select, "and so on"; in read and in write. Shows the display texts. | Decided (list open: "and so on") | [Faceplates](../metadata/08-faceplates.md) |
| MD-06.7 | Add a command or trigger entry | not said (button) | Picked in the list of the type's commands. | Decided (control not said) | [Faceplates](../metadata/08-faceplates.md) |
| MD-06.8 | Name shown | Text field | The name of the command button in the faceplate. | Decided | [Faceplates](../metadata/08-faceplates.md) |

Gaps:

- This page is the thinnest of Metadata (Product Owner's remark, 2026-11-11), to go over again.
- Order of the entries: can the user reorder them? Groups or separators?
- Full list of enum inputs ("and so on").
- Can the same signal appear twice (read and write)?
- A preview of the faceplate while editing?
- Remove an entry.

## MD-07 · Presets

Path: Metadata › Types › a type › Presets.

The list of presets is on the left and the selected preset on the right ([layout rules](README.md#layout-rules)).

```mermaid
mindmap
  root((MD-07 Presets))
    List of presets
    A preset
      For each signal
        Default value
        Display unit
        Decimal places
        Name shown
        Description, to confirm
      Entries shown by default
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-07.1 | List of presets | List | At least one is needed to use the type in a symbol; none is created automatically. | Decided | [Presets](../metadata/09-presets.md) |
| MD-07.2 | Create a preset | not said (button) | — | Implied | [Presets](../metadata/09-presets.md) |
| MD-07.3 | Name of the preset | not said | Never mentioned. | Open | [Presets](../metadata/09-presets.md) |
| MD-07.4 | Default value | Field of the signal's type | One per signal. | Decided | [Presets](../metadata/09-presets.md) |
| MD-07.5 | Display unit | Select | Starts as the model unit. | Decided | [Presets](../metadata/09-presets.md) |
| MD-07.6 | Decimal places | Number field | Starts as the quantity's default. | Decided | [Presets](../metadata/09-presets.md) |
| MD-07.7 | Name shown | Text field | Plain text; shown in the faceplate instead of the signal's name. | Decided | [Presets](../metadata/09-presets.md) |
| MD-07.8 | Description | Text field, multi-line | Plain text, line breaks kept, shown in the faceplate. The Product Owner is no longer sure it belongs to the preset. | Open | [Presets](../metadata/09-presets.md) |
| MD-07.9 | Entries shown by default | Checkbox per entry | Unticked entries stay available in a symbol and a synoptic. | Decided | [Presets](../metadata/09-presets.md) |

Gaps:

- Rename, duplicate and delete a preset; what happens to the symbols that use a deleted preset?
- Does a sub-type see the presets of its parent?

## MD-08 · Units

Path: Metadata › Units (navigation bar).

The page goes from the list of quantities to a quantity, then to a family. Following the [layout rules](README.md#layout-rules), they sit in columns from left to right: the list, the selected quantity, the selected family.

```mermaid
flowchart LR
    L["List of quantities, each difference under its quantity"] -->|"click"| Q["A quantity"]
    Q -->|"click"| F["A family"]
```

```mermaid
mindmap
  root((MD-08 Units))
    List of quantities
      Temperature
        Temperature difference
      Mass
      Flow
    A quantity
      Name
      Default model unit
      Default decimal places
      Reference family
      Families
    A family
      Name
      Units and their ratio
      Conversion to the reference and back
    Ready-made catalogue
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-08.1 | List of quantities | List | Mass, volume, flow... Each difference is shown under its quantity, and stays a quantity of its own. | Decided | [Units](../metadata/05-units.md) |
| MD-08.2 | Add a quantity | not said (button) | The user can add and change quantities, families and units. | Decided (control not said) | [Units](../metadata/05-units.md) |
| MD-08.3 | Default model unit | Select | Among the units of the quantity. | Decided | [Units](../metadata/05-units.md) |
| MD-08.4 | Default decimal places | Number field | The global setting for display. | Decided | [Units](../metadata/05-units.md) |
| MD-08.5 | Reference family | Select | Every other family converts to it and back. | Decided | [Units](../metadata/05-units.md) |
| MD-08.6 | Families | List | A click opens the family. | Decided | [Units](../metadata/05-units.md) |
| MD-08.7 | Unit | Text field + number field | Name with its variant (US gallon); ratio inside the family. Flat units (`m³/h` is one unit). | Decided | [Units](../metadata/05-units.md) |
| MD-08.8 | Conversion form | not said (select) | Proportional, affine, inverse, logarithmic, or a pair of free expressions (going and back). | Decided | [Units](../metadata/05-units.md) |
| MD-08.9 | Parameters of the form | Number fields | a, b, k, x₀, base, depending on the form. | Implied | [Units](../metadata/05-units.md) |
| MD-08.10 | Round-trip check | — | The application checks that a pair of expressions comes back. | Decided | [Units](../metadata/05-units.md) |
| MD-08.11 | Ready-made catalogue | — | Loaded at the first launch; source and licence open. | Decided, licence Open | [Units](../metadata/05-units.md) |

Gaps:

- How is a difference created: from its quantity ("add a difference"), or as any quantity then attached?
- What does the user see when the round-trip check fails?
- Delete a quantity or a unit that signals use.

## MD-09 · Enums

Path: Metadata › Enums (navigation bar).

The list of enums is on the left and the selected enum, with its items, on the right ([layout rules](README.md#layout-rules)).

```mermaid
mindmap
  root((MD-09 Enums))
    List of enums
    An enum
      Name
      Items
        Key, a number, sent to the model
        Display text, shown to people
```

| ID | Element | Kind | Values and behaviour | Status | Source |
| --- | --- | --- | --- | --- | --- |
| MD-09.1 | List of enums | List | A page of its own, not part of the signals. Enums can be made before any signal uses them. | Decided | [Enums](../metadata/06-enums.md) |
| MD-09.2 | Add an enum | not said (button) | — | Implied | [Enums](../metadata/06-enums.md) |
| MD-09.3 | Name | Text field | — | Decided | [Enums](../metadata/06-enums.md) |
| MD-09.4 | Kind of key | — | Removed (Product Owner, 2026-11-16): a key is always a number, there are no string keys. | Decided | [Enums](../metadata/06-enums.md) |
| MD-09.5 | Items | List | Each item a key and a display text. | Decided | [Enums](../metadata/06-enums.md) |
| MD-09.6 | Key | Number field | Unique; what the model receives. Changing it is breaking for the model. Whole numbers only: open. | Decided | [Enums](../metadata/06-enums.md) |
| MD-09.7 | Display text | Text field | What the faceplate, the symbol texts and the test values show. Not breaking. | Decided | [Enums](../metadata/06-enums.md) |
| MD-09.8 | Add, remove an item | not said | — | Implied | [Enums](../metadata/06-enums.md) |

Gaps:

- Must the display texts be unique too?
- Changing a key is breaking: the same Edit and Save step as for a signal, or nothing?
- Order of the items: is it the order of the menu in the faceplate?
- Which signals use an enum: is it shown (a usage counter)?

## MD-10 · Libraries: removed

The libraries of types (Type Libs) were removed by the Product Owner on 2026-11-16. The identifier MD-10 is not reused.
