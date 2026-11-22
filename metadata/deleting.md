# Deleting and its consequences

> [Home](../README.md) › [Metadata](README.md) › Deleting and its consequences

| Version | Date | Status | Change |
| --- | --- | --- | --- |
| 1 | 2026-11-22 | Draft | Creation of the file |

What a user can delete in Metadata, how, and what happens to everything that points to the deleted thing, in Metadata and outside it. The rules come from decisions 0017, 0053, 0079 and 0080, the [layout rules](../screens/README.md#delete-with-a-button-and-a-warning-in-metadata), the [whole draft](draft.md), the [entity files](entities/README.md) and [When Metadata changes](../symbols/01-libraries-and-symbols.md#when-metadata-changes) in the part Symbols. This page decides nothing new: what is not settled is in [Open questions](#open-questions).

## Where it is used

| Where | What it takes from here |
| --- | --- |
| [Type](entities/30-type.md), [Signal](entities/16-signal.md), [Command](entities/18-command.md), [Flag](entities/19-flag.md), [Preset](entities/29-preset.md), [Faceplate element](entities/28-faceplate-element.md), [Link entity](entities/13-link.md) | Deleted with a button and a warning; what they hold goes with them. |
| [Enum](entities/06-enum.md), [Enum item](entities/05-enum-item.md), [Designation](entities/11-designation.md) | Deleted on their page; what they hold goes with them. |
| [Preset value](entities/22-preset-value.md), [Signal field](entities/25-signal-field.md), [Command button](entities/26-command-button.md) | Removed with the signal or the command they point to. |
| [Inheritance of types](inheritance.md) | A deleted line of a parent is gone from every sub-type. |
| [MD-02 · General](../screens/metadata.md#md-02--general), [MD-03](../screens/metadata.md#md-03--documentation), [MD-04](../screens/metadata.md#md-04--signals), [MD-05](../screens/metadata.md#md-05--commands), [MD-12](../screens/metadata.md#md-12--flags-a-part-of-the-type), [MD-07](../screens/metadata.md#md-07--presets), [MD-09](../screens/metadata.md#md-09--enums), [MD-13](../screens/metadata.md#md-13--designations) | The delete button and its warning. |
| [When Metadata changes](../symbols/01-libraries-and-symbols.md#when-metadata-changes) | What a delete breaks in a symbol, shown there, never repaired by Metadata. |

## How a delete is done

- **A delete button** (an icon): at the far right of a line, with no column header; for a type, in its General part, never in the tree.
- **A warning asks to confirm**, the same for a type as for a line; nothing is deleted before the user confirms. There is no right click in Metadata.
- **The warning never lists what the delete breaks**: the user knows what they delete. What is broken shows later, in the symbol mode and the synoptic mode.
- **An inherited line has no delete button**: it is deleted in the type that declares it.
- **No versions, no undo**: what is deleted comes back only through Git, on the JSON files (decision 0053).

```mermaid
flowchart LR
    B[Delete button] --> W{Warning: confirm?}
    W -- No --> K([Nothing changes])
    W -- Yes --> D[Deleted, with what it holds]
    D --> P[Its preset values and faceplate elements removed]
    D --> S[Symbols and synoptics: shown broken]
```

## What can be deleted

| Thing | Where | Deleted with it |
| --- | --- | --- |
| Type | Its General part (MD-02) | Its whole file: appearance, documentation and links, own signals, commands and flags, presets. |
| Link | Documentation of the type (MD-03) | Nothing else. |
| Signal | Signals of the type (MD-04), own lines only | Its value type. |
| Command | Commands of the type (MD-05), own lines only | Its command target. |
| Flag | Flags of the type (MD-12), own lines only | Nothing else. |
| Preset | Presets of the type (MD-07) | Its preset values and its faceplate elements. |
| Faceplate element | Faceplate builder of a preset (MD-07) | Its part; for a group, every element in it, at any depth. |
| Enum | Enums page (MD-09) | Its items. |
| Enum item | Enums page (MD-09) | Nothing else. |
| Designation | Designations page (MD-13) | Nothing else. |

Never deleted in the software:

- **Quantities, unit systems and units**: a catalogue, read only (MD-08); contributors change their files.
- **Palettes and icon sets**: added or removed with their file. An appearance copies the color and the drawing it picks, so removing them changes no type.

## The rules

1. **What a thing holds goes with it.** A type deletes its lines, a group its elements, an enum its items: nothing is left behind.
2. **In the presets, what shows a deleted signal or sends a deleted command goes too**, in every preset of the type and of its sub-types: the preset value of the signal, the faceplate elements whose signal field shows it, those whose button sends the command (decisions 0079, 0080).
3. **Symbols and synoptics are never changed by a delete.** What points to the deleted thing is shown broken, with a small red mark, and listed in the symbol mode and the synoptic mode; there is no automatic repair.
4. **A delete is breaking for the model when the thing goes to it**: a type, a signal, a command, a flag, an enum item. Nothing warns; the change is seen in the differences of Git.
5. **A file missing or unreadable is not a delete.** What points to it is flagged in error and kept as written, so that it links again when the file comes back (decision 0079, for a parent).

## What points to each thing

| Deleted | Pointed to by | Effect |
| --- | --- | --- |
| Type | Its sub-types (`TYPE.parent`) | Not settled: see [Open questions](#open-questions). |
| Type | Symbols | The symbol keeps existing without a type: its animations and interactions are broken until the user chooses a type. |
| Signal | Preset values (`PRESET_VALUE.signal`) | Removed (decision 0079). |
| Signal | Signal fields (`SIGNAL_FIELD.signal`) | Their faceplate elements removed (decision 0079). |
| Signal | Bounds (`BOUND.signal`), command targets (`COMMAND_TARGET.signal`) | Not settled. |
| Signal | Symbols | Its animations, the texts that show its value or its unit, its test value are broken. |
| Command | Command buttons (`COMMAND_BUTTON.command`) | Their faceplate elements removed (decision 0080). |
| Command | Symbols | The interactions that send it are broken. |
| Flag | Placed symbols | Nothing is said at the delete; the synoptic mode lists it as broken. |
| Preset | Symbols, placed symbols | Not in the schema yet. |
| Enum | Value types (`VALUE_TYPE.enum`) | Not settled. |
| Enum item | Start values (`PRESET_VALUE.start_value`), command values (`COMMAND_TARGET.value`) | Not settled. |
| Enum, enum item | Symbols | The animations and the texts that use it are broken. |
| Designation | Text contents (`TEXT_CONTENT.designation`) | Not settled. |
| Designation | Texts filled on placed symbols | Not in the schema yet. |
| Link, faceplate element | Nothing | — |

## Open questions

- **A type that has sub-types**: is its delete refused, does it delete its whole branch, or are its sub-types left with a missing parent? Their parent never changes (decision 0013).
- **A bound or a command target** whose signal is deleted, own or inherited: removed, or flagged in error? A range may lack a bound; a command `set_input_signal` or `override_output_signal` needs its target.
- **An enum, an enum item or a designation still used** by a signal, a preset or a faceplate: is the delete refused, are those who point to it flagged in error, or emptied?
- **The last preset of a type**: a type needs one to be chosen in a symbol or a synoptic.
- **A preset deleted that symbols use**: with the synoptic (gap of MD-07).
- **A quantity whose file is missing**: the signals and display formats that point to it flagged in error and kept as written, as for a missing parent: assistant's reading.
- **An undo in Metadata**: open in the [whole draft](draft.md#metadata-open-questions).
