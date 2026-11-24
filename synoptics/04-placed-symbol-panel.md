# Panel of a placed symbol

> [Home](../README.md) › [Synoptics](README.md) › Panel of a placed symbol · Previous: [Placed symbols](03-placed-symbols.md) · Next: [Pipes](05-pipes.md)

Status: extrapolated by the assistant. It gathers in one panel what Metadata leaves "to the synoptic, part 3" (designation texts, flags, template items, values changed). The instance ID and what a synoptic may change are settled; the rest is not validated.

The right-hand panel of the synoptic editor, when one placed symbol is selected. It is where a placed symbol gets its identity.

## Rules

- One panel, **sections one under the other**, each with a title and folded or unfolded by a click on it. The order goes from what the user fills most to least. Proposed.
- A section with something to fill shows a **small warning mark** on its title, the same as in the [faults](08-faults.md). Proposed.

```mermaid
flowchart TD
    A["Symbol: library, symbol, type, Open, Replace"] --> B["Identity: instance ID, designation texts"]
    B --> C["Signal settings: values changed"]
    C --> D["Flags: one checkbox each"]
    D --> E["Template enums: items of this placed symbol"]
    E --> F["Placement: position, rotation, mirror, size"]
    F --> G["Faults of this placed symbol"]
```

### Symbol

| Element | What it does | Status |
| --- | --- | --- |
| Thumbnail, Symbol Lib › symbol | What is placed. | Proposed |
| Type | Read only: the type never changes in a synoptic. | Decided ([Type and symbol](../metadata/draft.md#type-and-symbol)) |
| Open the symbol | Opens it in the symbol mode, in its Symbol Lib. | Proposed |
| Replace | Another symbol of the same type (see [Replacing a symbol](03-placed-symbols.md#replacing-a-symbol)). | Proposed |
| Reference | In a view: "From the installation Water treatment", with a link that opens the placed symbol there. The sections below show the identity of the installation's placed symbol: a change made here is made there. | Decided (a reference shares the identity, 2026-11-20), Proposed (the link) |

### Identity

- **Instance ID**: the key of the placed symbol in the configuration files and in the signal list (`pump_p101.speed`). Decided on 2026-11-20: every placed symbol has an instance ID of its own, a field apart from the designations of Metadata; the tag is never the key. Proposed: set by the software from the type's `id` and a number (`centrifugal_pump_3`), changed by the user, unique in the folder. Its name is open: the research on names (T5) covered Metadata only.
- **Designations**: one text field per [designation](../metadata/entities/11-designation.md) of Metadata, in the order of the Designations page, labelled by their ID (a designation has no display name since 2026-11-21).
  - **Every required designation** is shown on every placed symbol, whether or not the faceplate of its type uses it, and marked as required.
  - **A required text left empty warns, never blocks**: the field is marked, the section shows the small warning mark, the placed symbol is listed in the [faults](08-faults.md) as a warning, and the synoptic is saved anyway.
  - **A designation that is not required** is shown when the faceplate of its type uses it (decided in Metadata: the designations used give the synoptic its list to fill). Proposed: the others are not shown.
- **Uniqueness**: a text already used by another placed symbol, for the same designation, is marked at once in the field, and listed in the faults as a warning. It is never refused: the user may be in the middle of renaming. Proposed; Metadata left open whether it is checked.

### Signal settings

- No preset to choose (2026-11-24): there are no presets; the placed symbol starts from the [signal settings](../metadata/entities/22-signal-setting.md) and the faceplate of its type.
- Decided on 2026-11-20: a synoptic may change, for one placed symbol, the **start values**, the **display units**, the **decimals** and the **texts** of the title and description elements of its faceplate. Nothing else changes in a synoptic.
- Decided on 2026-11-20: these changes are **kept as changes from the type**. A placed symbol that changes nothing follows its type when the type changes.
- A table of the values this placed symbol changes: signal, start value, display unit, decimals, then the texts. Proposed (the table).
- A changed value shows a dot, and a **Reset to the type** button on its line, as the reset of the signal settings of a sub-type ([MD-07.28](../screens/metadata.md#md-07--signal-settings); decided on 2026-11-20); the dot is proposed.
- A value typed is kept in the default unit of its quantity, as every number typed in Metadata (decision 0051); the screen shows it in the display unit. Proposed: the same rule here.

### Flags

- One **checkbox per flag of the type**, own and inherited, with its description beside it, so that it is ticked knowingly (decided: [Flags](../metadata/draft.md#flags), the description is shown when editing a synoptic).
- In the order of the type's flags. Nothing is ticked on a new placed symbol. Proposed.

### Template enums

- One block per **enum signal of the type that points to a template**, titled with the signal and the description of the template (decided: the items are completed on each placed symbol).
- Each block is a **table of items**: key, display name, description, with the small + on the right of its title and a delete button at the far right of each line (layout rules of the application).
- Until a block has at least one item, the placed symbol shows the **small warning** decided in Metadata, on the canvas and in this section. It never stops the user from working.
- Proposed: **Copy the items from** another placed symbol of the same type, for ten switches with the same positions.

### Placement

| Element | What it does | Status |
| --- | --- | --- |
| X, Y | Position of the frame of the symbol, in pixels, number fields. | Proposed |
| Rotation | Four buttons: 0°, 90°, 180°, 270°. | Proposed |
| Mirror | Two toggles: horizontal, vertical. | Proposed |
| Size | Number field in percent. | Proposed |
| On a pipe | When connected: the pipe, the distance from its start, **Free from the pipe**. | Proposed (the connection is decided) |
| Locked, hidden | Two toggles, as on its line in the Objects panel. | Proposed |

### Faults of this placed symbol

- The lines of the [faults](08-faults.md) about this placed symbol, with the same **Show** button. Proposed.

## Example

`P-101`, placed symbol of "Motorised centrifugal pump", type `centrifugal_pump`:

| Section | Content |
| --- | --- |
| Identity | Instance ID `pump_p101`; Tag `P-101`; Location `Building A` |
| Signal settings | `speed_setpoint` start value 1450 rpm changed to 1200 rpm (dot, reset) |
| Flags | `has_bypass` ticked, `remote_start` not ticked |
| Template enums | `mode` (template `pump_mode`): 0 Off, 1 Local, 2 Remote |

## Where it is used

| Thing | Created and changed in | In a symbol | In a synoptic |
| --- | --- | --- | --- |
| Instance ID | Panel of a placed symbol | No | Set, unique; shared by its references in views |
| Designation texts | Panel of a placed symbol, or the page Placed symbols | No | Fill |
| Flags ticked | Panel of a placed symbol | No | Tick |
| Template items | Panel of a placed symbol | No | Create, edit, delete, copy from another |
| Values changed from the type | Panel of a placed symbol | No (the symbol chooses its type only, 2026-11-24) | Change, reset |

## Open questions

- The name of the instance ID: not treated by the research T5.
- For a designation that is not required: show only those used by the faceplate of the type (advised), or all of them? (A required one is always shown, 2026-11-21.)
- Is a duplicate designation text a warning (advised) or refused?
- With sub-types standing for the former presets (2026-11-24), does a synoptic still need to change values of one placed symbol, or does a sub-type do it?
