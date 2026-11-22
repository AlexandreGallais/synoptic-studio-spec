# Icons

> [Home](../README.md) › [Design system](README.md) › Icons

Status: first draft, written by the assistant on 2026-11-22 from the screens of Metadata. Not validated. The drawing of each icon: on the page Icons of the Figma file.

## Rules

- One component per icon, named `icon/<name>`, drawn on a 16 px grid and scaled to 20 px without a second drawing.
- Drawn in lines: a stroke of 1.5 px, round ends and round corners, no fill; the drawing stays inside the 16 px square, its line included, and two lines never touch where they should not (Product Owner, 2026-11-22: "passe sur chacune de tes icônes minutieusement"). On that day `metadata`, `types`, `reset`, `group`, `paragraph` were redrawn: the folded corner, the boxes of the tree, the arrow joined to its circle, the inner boxes apart, the two stems apart.
- An icon "-add" is its icon, smaller, in the top left, with a + in the bottom right, both inside the 16 px square.
- An icon takes its colour from a token (`icon-primary`, `icon-secondary`, `accent`, `danger`), never a fixed colour.
- An icon alone on a button always has an accessible name and a tooltip ([Components](04-components.md#atoms)).
- The icons of the interface are not the icons of the types: those are files of Metadata ([Icon](../metadata/entities/03-icon.md)).

## The icons the screens call for

| Icon | Meaning | Screens |
| --- | --- | --- |
| `app-mark` | The logo, a valve: two triangles meeting at their tips, without the stem on top (Product Owner, 2026-11-22) | Top bar |
| `metadata` | The Metadata part | Top bar |
| `symbols` | The Symbols part | Top bar |
| `synoptic` | The Synoptic part | Top bar |
| `minimise`, `maximise`, `restore`, `close` | Window buttons | Top bar |
| `types` | Page Types | MD-00.1 |
| `units` | Page Units | MD-00.2 |
| `enums` | Page Enums | MD-00.3 |
| `designations` | Page Designations | MD-00.6 |
| `add` | The small + of a title, the + on hover of a type | MD-01.3, MD-04.4 and every list |
| `search` | Search in the type tree | MD-01.6 |
| `dismiss` | Close the search, close a dialog | MD-01.6c |
| `chevron-right`, `chevron-down` | A folded or unfolded branch of a tree; a select | MD-01.1, every select |
| `expand-all`, `collapse-all` | Open or close every branch of the type tree: two chevrons pointing apart, two chevrons pointing together (Product Owner, 2026-11-22) | MD-01.7 |
| `delete` | Delete a line, a type | MD-02.8, MD-03.10, MD-04.13 and every table |
| `drag-handle` | The handle of a line | MD-03.11, MD-04.14 and every ordered table |
| `reset` | Follow the parent's icon or colour again | MD-02.7 |
| `folder` | A path link | MD-03.9 |
| `link` | A URL link | MD-03.9 |
| `folder-add`, `link-add` | Add a path, add a URL: the icon with a small + at its bottom right | MD-03.6, MD-03.7 |
| `signal-add`, `command-add`, `title-add`, `paragraph-add`, `group-add` | Add an element to a faceplate: the icon of its kind, smaller, with the small + at its bottom right (Product Owner, 2026-11-22: without the +, "on ne sait pas vraiment si c'est pour ajouter") | MD-07.18, MD-07.20 |
| `full-page`, `exit-full-page` | The description on the whole editing part | MD-03.4c |
| `bold`, `italic`, `heading`, `list-bulleted`, `list-numbered`, `table`, `code`, `quote` | The formatting tool bar (content proposed) | MD-03.4d |
| `signal-input`, `signal-output` | The direction of a signal | MD-04.12, MD-07.9 |
| `quantity`, `difference` | A quantity or a difference | MD-04.9 |
| `command` | A command element | MD-07.18 |
| `title`, `paragraph` | A title element, a description element | MD-07.18 |
| `group` | A group element | MD-07.18 |
| `variable` | Take a value from a signal or a designation, as Figma's "Apply variable" | MD-07.22, MD-07.23 |
| `warning` | A warning dialog, a warning in a line | Every delete, MD-09.10 |
| `error` | A line in error | Checks and errors |
| `check` | A ticked checkbox | MD-13.8 |

## Where it is used

| Where | What it uses |
| --- | --- |
| [Components](04-components.md) | `icon-button`, `button`, `tree-row`, `table` hold these icons as instances. |
| [Screens of Metadata](../screens/metadata.md) | Every icon of the table above. |
