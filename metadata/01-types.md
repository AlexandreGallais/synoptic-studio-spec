# Types

> [Home](../README.md) › [Metadata](README.md) › Types · Next: [Icons](02-icons.md)

Status: validated by the Product Owner on 2026-11-11; changed by him on 2026-11-16 (no libraries of types, type tree actions, fixed parent, icon buttons in General, parts shown as a strip of icons, no Edit or Save step, no warning on delete). Open points are listed in [Open questions](12-open-questions.md).

A type is the representation of a symbol at one level of detail. Types form a tree, hence parents and sub-types.

```mermaid
flowchart TD
    Pump --> Centrifugal[Centrifugal pump]
    Pump --> Positive[Positive displacement pump]
    Positive --> Pneumatic[Pneumatic positive displacement pump]
    Valve
```

## Rules

- The General part holds the name, the parent, and an icon with its colour (see [Icons](02-icons.md)). The description and the links are in a separate documentation page (see [Documentation](03-documentation.md)).
- The name is the type's identifier for the model, like a signal's name. No second label. It must be readable and exact, because model authors use it to know what the type is (example: `centrifugal_pump`). Where a standard already names things, the type takes that name.
- A type also has an internal identifier, set by the software, that never changes. It exists on the application side only and never goes to the model. It is needed to define the parent and for symbols to point to the type, so renaming a type breaks nothing in the application.
- So there are two identifiers: the name (seen by the model, meaningful) and the internal one (seen by the application only, meaningless).

```mermaid
flowchart LR
    T[Type] --> N["Name = model identifier, readable"]
    T --> I["Internal identifier, fixed, app only"]
    N -->|"seen by"| M[Model]
    I -->|"used by"| A["Parent link, symbols"]
```

- No abstract types: "Pump", "Positive displacement pump" and "Pneumatic positive displacement pump" can all be chosen.
- A type inherits the signals of its parents.
- The type tree is on the **left** of the screen, as in a code editor (IDE), where every tree sits on the left (Product Owner, 2026-11-11). It sits just right of the navigation bar of Metadata (see [Screens](../screens/README.md#layout-rules)).
- There are no libraries of types: every type of the tree can be chosen everywhere (Product Owner, 2026-11-16).
- The name is changed in the General part only. Double-clicking an item in the tree does not rename it: hidden options are avoided.
- **The parent never changes** (Product Owner, 2026-11-16). It is set when the type is created, by the + of the type under which it is created (or the + of the title, for a root type). General shows it, read only: its name with its icon.
  - Why: moving a type to another parent changes the signals it inherits and breaks what uses it. No signal goes from one parent to another "aussi bêtement que ça". Metadata must stay strict ("ça doit être carré").
  - A type created under the wrong parent is deleted and created again under the right one; it is never moved.

```mermaid
flowchart LR
    C["+ on a type, or + on the title"] --> P["Parent set at creation"]
    P --> F["Fixed: shown in General, read only"]
    W["Wrong parent"] --> D["Delete the type"] --> N["Create it again under the right parent"]
```

- The parts of a type are shown in this order (Product Owner, 2026-11-11): General, Documentation, Signals, Commands, Presets. The Faceplate part is merged into the Presets since 2026-11-16 (see [Presets](09-presets.md)). They are shown as **a strip of icons** in a column between the tree and the editor, the name of each part shown when the mouse is over its icon (proposal C, chosen by the Product Owner on 2026-11-16; see [The parts of a type](#the-parts-of-a-type-a-strip-of-icons)).

### The type tree: search, create, delete (Product Owner, 2026-11-16)

- A **search field** sits under the title "Type tree".
- **Create:** each type of the tree has a **+** on its right, shown when the mouse is over the type. It creates a new type **under** it (a child). The new type starts with a default name, changed afterwards in General.
- A **+** on the title "Type tree" creates a type at the root. It is always shown, so that creating a type is never hidden. The Product Owner fears it looks bad ("ça va être dégueulasse … s'il le faut"): kept, its look is for the design.
- **Delete:** a right click on a type opens a menu of options; **Delete** is one of them. No warning that symbols lose their type (Product Owner, 2026-11-16: "ça ne sert à rien … il ne faut pas faire ça"). The delete shows on the [Versions](13-versions.md) page, where it can be undone before a version is made.

```mermaid
flowchart LR
    H["Mouse over a type"] --> P["+ on its right"] -->|"click"| C["New child type, default name"]
    T["+ on the title Type tree, always shown"] -->|"click"| R["New type at the root, default name"]
    RC["Right click on a type"] --> M["Menu of options"] --> D["Delete"]
```

- The General part holds only the name, the parent, the icon and the colour. Nothing more is needed (Product Owner, 2026-11-11, confirmed on 2026-11-16).
- In General, the name is **always editable**: no Edit or Save button (Product Owner, 2026-11-16: "il faut que tout soit éditable tout le temps"). The resets to the parent (icon, colour) are **icon buttons**, without a text label.
- No virtual links between types of the tree. Duplicates are accepted: a change in one type must not change another silently, so nothing has to be retested everywhere. It also lets each type be versioned alone later. The documentary research (2026-11-10) finds this rule defensible: neither FMI, OPC UA nor AutomationML requires or forbids it.

### Limits of "no virtual link" (decided on 2026-11-11, from the research)

The rule is true between types that have no parent link. Three mechanisms do propagate a change, on purpose, and are written as such:

- Changing the content of a parent (its signals, its commands) changes all its descendants. The parent link itself never changes (see above).
- A sub-type cannot declare again a signal name it already inherits. No redefinition: it is the simplest rule, and a name stays one thing along the tree.
- The values of an enum are part of the contract with the model: changing them is breaking, like a rename (see [Enums](06-enums.md)). Links to an enum or a quantity go through an internal identifier, like symbols do for types.

Versions, the answer of OPC UA's best-practices guide and of Siemens, came on 2026-11-16: Metadata as a whole is versioned (see [Versions](13-versions.md)).

## What a type holds

```mermaid
flowchart LR
    T[Type] --> G[General: name, parent, icon]
    T --> DO[Documentation]
    T --> P[Signals]
    T --> C[Commands]
    T --> R[Presets, which build the faceplate]
```

| Part | File |
| --- | --- |
| General: icon and colour | [Icons](02-icons.md) |
| Documentation: description (Markdown), links | [Documentation](03-documentation.md) |
| Signals | [Signals](04-signals.md) |
| Commands | [Commands](07-commands.md) |
| Presets and their faceplate | [Presets](09-presets.md) |

## The parts of a type: a strip of icons

Chosen by the Product Owner on 2026-11-16: **proposal C**, a strip of icons.

- A narrow column sits between the type tree and the editor. It holds the five parts, one icon each, one under the other, in the order General, Documentation, Signals, Commands, Presets.
- The name of a part is shown when the mouse is over its icon.
- Why: everything is in columns, which saves height and follows the layout rule; the eye gets used to it ("le fait de tout avoir en colonne comme ça, ça habitue son cerveau"). The icons have to be learnt, which the name on hover helps.
- Its look is still to work on ("faudra le travailler"): the icons themselves are chosen with the design system.

```mermaid
block-beta
    columns 4
    tree["Type tree"] strip["Strip: 5 icons, name on hover"] editor["Editor of the selected part"]:2
```

The four proposals drawn before the choice, kept for the record. The Product Owner liked the tabs in a row, easy to use, but they break the rule "columns rather than rows" (see [Layout rules](../screens/README.md#layout-rules)). They are drawn in the Figma file, page "Spec", section "MD-01 · Parts of a type: four proposals". D was refused ("c'est mort"), B takes too much room.

| Proposal | What it is | For | Against |
| --- | --- | --- | --- |
| A. Tabs in a row | The five parts as tabs above the editor (the current wireframes). | Known by everyone; all the width stays for the part. | A row, against the rule of columns. |
| B. A column of parts | A narrow column between the tree and the editor lists the five parts, one under the other, with their names. | Follows the rule of columns; the names stay readable. | One more column: less width for the part. |
| C. A strip of icons (**chosen**) | The same column, reduced to five icons, the name in a tooltip. | Narrow: almost all the width stays for the part. | Icons to learn; the name is hidden until the mouse is over it. |
| D. Under the type, in the tree | When a type is selected, its five parts unfold under it in the tree, as the layers of a frame in Figma. | No extra column; the type and its part are read together. | The tree grows and moves; a part is mixed with the types. |

```mermaid
block-beta
    columns 4
    a["A: tree | tabs in a row above the part"] b["B: tree | column of parts | part"] c["C: tree | strip of icons | part"] d["D: tree with the parts under the selected type | part"]
```

## Type and symbol

- A symbol is attached to one type.
- The type of a symbol can only be changed in symbol editing.
- In a synoptic, the type can never be changed. Only the preset can be.

```mermaid
flowchart LR
    TY[Type] -->|"chosen in symbol editing"| SY[Symbol]
    SY -->|"placed in"| SN[Synoptic]
    SN -.->|"type fixed, only the preset can change"| SY
```

## Renaming is breaking, on purpose

The names of types (and of signals) build the interface definition of the model. They are meant to be defined at the start and never to change.

- A name is a contract with the model. No mapping layer between an old name and a new one: it would make no sense here.
- Renaming a type is possible but breaking: the model must change its name too, because its interface definition changed.
- The more names change, the more the model has to change. So names must be thought through before they are set.
- The application does not break on a rename, because it uses the internal identifier.

```mermaid
flowchart LR
    R[Rename a type] --> A["Application: nothing breaks (internal identifier)"]
    R --> M["Model: its interface definition changed, the model must follow"]
```

## How a rename is done: typed in place, checked in the versions

Changed by the Product Owner on 2026-11-16. It replaces the Edit and Save buttons of 2026-11-11.

- The name is typed in place in General, like every field of Metadata. No Edit or Save button, no warning, no confirmation dialog.
- What stops a mistake is the [Versions](13-versions.md) page: before a version is made, the rename is shown among the differences, and it can be undone. A rename breaks the model, so it makes the version a major one.
- The consequences for models (see above) are to be explained in a user manual. That manual is not part of the open source version.

```mermaid
flowchart LR
    A["Type the new name in General"] --> B["Versions page: the rename is in the differences"]
    B -->|"undo"| U["The old name is back"]
    B -->|"make a version"| V["Major version: the model must follow"]
```

## Where it is used

| Thing | Created and changed in | Used in | In a symbol | In a synoptic |
| --- | --- | --- | --- | --- |
| Type (name, parent) | Metadata: the name in General, the parent at creation only | Signal and command inheritance | Chosen among all the types, only here | No |
