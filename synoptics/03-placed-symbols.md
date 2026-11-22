# Placed symbols

> [Home](../README.md) › [Synoptics](README.md) › Placed symbols · Previous: [Synoptic editor](02-synoptic-editor.md) · Next: [Panel of a placed symbol](04-placed-symbol-panel.md)

Status: extrapolated by the assistant on 2026-11-20, from the rules of Metadata and Symbols about placed symbols, and the opinions of the research (report T4, sections 3.16 and 3.17). Not validated.

A **placed symbol** is a symbol of a Symbol Lib put in a synoptic. It shows the drawing of its symbol and has an identity of its own: the pump `P-101` is one placed symbol of the symbol "Centrifugal pump".

## Rules

### What is decided elsewhere

- The **type** of a placed symbol is the type of its symbol and **can never be changed** in the synoptic; only the **preset** can (Metadata draft, [Type and symbol](../metadata/draft.md#type-and-symbol)).
- A symbol with a type can be placed and **left unwired** (Symbols, 2026-11-15).
- Each placed symbol has its own **flags**, **designation texts** and **template enum items** (Metadata, [Flags](../metadata/draft.md#flags), [Designation](../metadata/entities/11-designation.md), [Enums](../metadata/draft.md#global-enums-and-templates)). They are filled in its [panel](04-placed-symbol-panel.md).
- A symbol can be **connected to a pipe** and then only slides along it (Pipes, 2026-11-11; see [Pipes](05-pipes.md#symbols-on-a-pipe)).

### A linked instance

- A placed symbol is a **linked instance** of its symbol: when the symbol changes in its Symbol Lib (drawing, animations, interactions, connection points), every placed symbol follows (research T4, section 3.16, opinion; proposed).
- So nothing of the drawing can be changed in the synoptic. To change a drawing, the user opens the symbol (a button in the panel). To have another drawing for one pump, the user makes another symbol, or a [sub-symbol](../symbols/12-sub-symbols.md). Proposed.
- What belongs to the placed symbol itself, proposed:

| Belongs to the placed symbol | Belongs to its symbol |
| --- | --- |
| Position, rotation, mirror, size | Drawing, layers |
| Order in the stack, folder, hidden, locked | Animations, interactions |
| Identity: instance ID, designation texts, flags, template items | Connection points |
| Preset chosen, and its start values, units, decimals and faceplate texts changed from it | Type |
| Pipe it is connected to, and where | Faceplate (from the preset) |

### Placing a symbol

- Drag a symbol from the **Library** panel onto the canvas, or click it then click the canvas. Proposed.
- While it is dragged, its connection points snap to the free ends of pipes and to the grid. Proposed.
- Dropped onto a pipe, a symbol with two connection points offers **Connect to the pipe** (decided action, see [Pipes](05-pipes.md#symbols-on-a-pipe)). Proposed: offered by a small floating button next to the drop, never done without asking.
- A newly placed symbol gets the **first preset** of its type, and empty designations. It is listed at once in the [faults](08-faults.md) as incomplete when it needs texts (a warning, never a block). Proposed.

### Rotation, mirror, size

From the research (report T4, section 3.17, 14b and 14c; opinions), proposed:

- **Rotation by quarter turns** (0°, 90°, 180°, 270°), with a key and a button; no free angle, so that pipes stay at right angles.
- **Mirror**, horizontal or vertical.
- The **connection points and their directions follow** the rotation and the mirror, so the pipes still leave in the right direction.
- **Texts stay readable**: a text of the symbol turned by 180° or mirrored is shown the right way up. Open: the symbol editor says nothing about it yet.
- **Size**: a uniform scale of the whole symbol, set in percent (100 % is the size drawn in the symbol editor). The rule "never a scale" of the symbol editor stays there. Whether the borders grow with the scale is open.

### Replacing a symbol

- **Replace** swaps the symbol of a placed symbol for another symbol **of the same type**, in any Symbol Lib used: a manual pump becomes a motorised pump. Its identity (designations, flags, template items) and its values are kept. Proposed.
- Only symbols of the same type are offered, since the type of a placed symbol never changes. A sub-symbol with a **sub-type** is therefore not offered. Open: the Product Owner may want to allow a sub-type, which keeps every signal of the parent.
- The pipes stay connected when the new symbol has connection points at the same places (matched by their order); otherwise their ends become free and a fault says so. Proposed.

### Changing the Symbol Lib of a synoptic

The research advises it as the way to change the look of a synoptic over time, since a new look is a new Symbol Lib (Libraries and symbols, research opinion).

- **Change the Symbol Lib** opens a table: one line per symbol used, the symbol found in the new library opposite it, matched by name, then by type when the name differs. The user corrects the table, then confirms. Proposed.
- Every placed symbol keeps its identity; only its drawing changes. A symbol with no match stays as it is and is listed in the faults. Proposed.

### When the symbol changes

- The rules of [When Metadata changes](../symbols/01-libraries-and-symbols.md#when-metadata-changes) hold for a placed symbol too: a broken link is marked with a small red mark and listed in the faults; nothing is repaired by itself (decided for symbols; applied here).
- Added for the synoptic, proposed:

| Change in the Symbol Lib | What happens to the placed symbol |
| --- | --- |
| The symbol is deleted | It keeps its place, its identity and its values, drawn as an empty frame with a red mark; a fault says it; Replace repairs it. |
| A connection point is deleted | The pipe attached to it gets a free end; a fault says it. |
| The symbol changes type | Every placed symbol is in fault, since the type of a placed symbol never changes; the identity is kept. |
| The Symbol Lib is removed from the synoptic | Its placed symbols and pipe styles are in fault until a library is added again. |

## Example

| Placed symbol | Symbol | Type | Rotation | Connected to |
| --- | --- | --- | --- | --- |
| `P-101` | Motorised centrifugal pump | `centrifugal_pump` | 0° | Pipes W-01 (in), W-02 (out) |
| `V-12` | Motorised valve | `valve` | 90° | On pipe W-02, 140 px from its start |
| `T-1` | Tank | `tank` | 0° | Pipe W-01 (out) |

## Where it is used

| Thing | Created and changed in | In a symbol | In a synoptic |
| --- | --- | --- | --- |
| Placed symbol | Synoptic editor, Build mode | No | Place, move, turn, replace, delete |
| Its symbol and type | Symbol mode | Create, edit | Read only; Replace by a symbol of the same type |
| Its rotation, mirror, size | Panel of the placed symbol | No | Set |

## Open questions

- May Replace offer a symbol whose type is a sub-type of the current one?
- Do borders grow with the size of a placed symbol, or keep their width?
- Is a placed symbol turned by 180° drawn with its texts the right way up?
- Changing the Symbol Lib: matched by name then by type (advised), or by an identifier given to each symbol?
