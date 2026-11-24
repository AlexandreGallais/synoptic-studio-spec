# Product Owner's words

> [Home](../README.md) › [Notes](README.md) › Product Owner's words

The citations of the Product Owner taken out of the specification on 2026-11-23, file by file: what was said, then the sentence of the specification it stood in. A note, not a specification: the specification files say what the product is, without who said it nor when.

## controls/README.md

- 2026-11-15: "des composants logiques", one per kind
  - In: The controls shared by the whole application: a number field, a text field, and the other controls that every part uses. Each one is a single component of the design system, with the same behaviour on every screen, in Metadata, in the symbol editor and in the synoptic (Product Owner, 2026-11-15: "de…

## controls/number-and-text-fields.md

- 2026-11-15
  - In: - Every number field of the application is the same component, with the same behaviour. The same holds for every text field (Product Owner, 2026-11-15).
- 2026-11-15
  - In: - With a modifier key held, they add or remove **10** (Product Owner, 2026-11-15).

## design-system/01-principles.md

- 2026-11-22: "c'est une image"
  - In: - The application is for people from 20 to 77 years old (Product Owner, 2026-11-22: "c'est une image"): everyone must be able to use it, without good eyesight or a precise hand.
- 2026-11-22: "c'est le logiciel, il est open source. Pour l'instant, il y a qu'un truc, point barre"
  - In: - One theme only, `sand`, built on the colours of the old **Warm Sand** theme (light) (Product Owner, 2026-11-22: "c'est le logiciel, il est open source. Pour l'instant, il y a qu'un truc, point barre"; "c'est warm sand").
- 2026-11-22
  - In: - The smallest window the application is designed for is **1600 × 900** (Product Owner, 2026-11-22). The screens of the Metadata page are drawn at that size.

## design-system/02-foundations.md

- 2026-11-23
  - In: The text a user writes in the visual editor of a description (markdown-editor). Its paragraph is `body`, its bold `body-strong`, its code `code`. Every heading is larger than the paragraph, down to Heading 6, so that a bold line never reads as a heading (Product Owner, 2026-11-23). Sizes proposed.

## design-system/04-figma-file.md

- : "un tableau d'états et de types [...] plutôt que plein de texte"
  - In: Since 2026-11-22 (Product Owner: "un tableau d'états et de types [...] plutôt que plein de texte"), each component is shown as a table, with no text to read around it:
- 2026-11-23: "partout en deux traits"
  - In: - **Focus in the SVG export**: Figma exports a spread shadow as an SVG filter that grows the shape pixel by pixel, from the transparency of the shape. Two faults follow, seen by the Product Owner on 2026-11-23: on a round control the focus comes out square-cornered (the radio), and on a control with…

## design-system/05-icons/README.md

- 2026-11-22
  - In: - The SVG files have no stroke: every line is turned into a filled outline, joined into one shape, filled with `currentColor` so that the code gives the colour (Product Owner, 2026-11-22). Figma keeps the lines.
- 2026-11-22
  - In: | warning | `warning` | A warning dialog, a warning in a line. The triangle is 12 high and its dot keeps the same gap to the bottom as in `error` (Product Owner, 2026-11-22). | `631:207` |

## design-system/06-atoms/README.md

- 2026-11-23
  - In: The smallest components: each does one thing and holds no other component but an icon. One sheet per atom (`<atom>.md`); the table of its variants and states, exported from Figma, is in images (`table-<atom>.svg`) (Product Owner, 2026-11-23). Only the atoms the screens of Metadata use are here (Prod…
- 2026-11-22
  - In: The smallest components: each does one thing and holds no other component but an icon. One sheet per atom (`<atom>.md`); the table of its variants and states, exported from Figma, is in images (`table-<atom>.svg`) (Product Owner, 2026-11-23). Only the atoms the screens of Metadata use are here (Prod…

## design-system/06-atoms/drag-handle.md

- 2026-11-22
  - In: - Only the handle starts a drag: pressing it turns its whole line to `dragging` (violet, `layer-selected`); a click elsewhere on the line does nothing (Product Owner, 2026-11-22).

## design-system/06-atoms/select-trigger.md

- 2026-11-22
  - In: - Opened with the keyboard (Enter, Space or the down arrow), it keeps the double focus line around the line of `open`: `open-focus`. Opened with the mouse, only the line of `open` (Product Owner, 2026-11-22).
- 2026-11-22
  - In: - The 2 px line of `open` and `error` is drawn over the padding: the text never moves (Product Owner, 2026-11-22).

## design-system/06-atoms/tooltip.md

- 2026-11-22
  - In: - It is centred on the icon it names, whatever the length of its text (Product Owner, 2026-11-22).

## design-system/07-molecules/README.md

- 2026-11-23
  - In: Components made of atoms only, for one job. One sheet per molecule (`<molecule>.md`); the table of its variants and states, exported from Figma, is in images (`table-<molecule>.svg`) (Product Owner, 2026-11-23). Only the molecules the screens of Metadata use are here (Product Owner, 2026-11-22).
- 2026-11-22
  - In: Components made of atoms only, for one job. One sheet per molecule (`<molecule>.md`); the table of its variants and states, exported from Figma, is in images (`table-<molecule>.svg`) (Product Owner, 2026-11-23). Only the molecules the screens of Metadata use are here (Product Owner, 2026-11-22).

## design-system/07-molecules/content-table.md

- 2026-11-23
  - In: - Under the mouse, two + show (Product Owner, 2026-11-23): the one of the line limit nearest to the mouse (between two lines, or under the table near the bottom edge) and the one of the column limit nearest to it (between two columns, or on the right near the right edge). `state=hover` shows the mou…

## design-system/07-molecules/menu-grouped.md

- 2026-11-22: "ftH2O touchait le bas"
  - In: - Its titles and items sit in a frame `content` that carries the padding of the top and the bottom: once scrolled to the end, the last item keeps its margin (Product Owner, 2026-11-22: "ftH2O touchait le bas").

## design-system/07-molecules/menu.md

- 2026-11-22
  - In: - Its items sit in a frame `content` that carries the padding of the top and the bottom, so the last item keeps its margin once scrolled to the end (Product Owner, 2026-11-22).

## design-system/07-molecules/segmented-control.md

- 2026-11-22, Units · temperature
  - In: - On the screens, the click of an item leads to the screen with that item selected, never to a change of the component in place: Figma keeps the hover of the clicked item after such a change (Product Owner, 2026-11-22, Units · temperature).

## design-system/07-molecules/tree-row.md

- 2026-11-22: the + must always show on hover
  - In: - On hover the + shows on the right. A selected line keeps that hover: it shows its + without any other change, `state=selected-hover` (Product Owner, 2026-11-22: the + must always show on hover). A click on a selected line does nothing.

## design-system/08-organisms/README.md

- 2026-11-23
  - In: Components made of molecules and atoms that form a whole part of a screen. One sheet per organism (`<organism>.md`); the table of its variants and states, exported from Figma, is in images (`table-<organism>.svg`) (Product Owner, 2026-11-23). Only the organisms the screens of Metadata use are here (…
- 2026-11-22
  - In: Components made of molecules and atoms that form a whole part of a screen. One sheet per organism (`<organism>.md`); the table of its variants and states, exported from Figma, is in images (`table-<organism>.svg`) (Product Owner, 2026-11-23). Only the organisms the screens of Metadata use are here (…

## design-system/08-organisms/data-table-row.md

- 2026-11-22
  - In: - `hover` lights the line; a click on the line itself does nothing: a line of a table is never selected (Product Owner, 2026-11-22).

## design-system/08-organisms/description-sample.md

- 2026-11-23
  - In: - Every heading is larger than the paragraph, down to Heading 6 (Product Owner, 2026-11-23).

## design-system/08-organisms/faceplate-element.md

- 2026-11-22: "faut que ça fasse violet que quand je clique sur le bouton pour bouger la ligne"
  - In: - `dragging` (`layer-selected`, violet): only while its handle is held, as a line of a table; a click on the element itself does nothing (Product Owner, 2026-11-22: "faut que ça fasse violet que quand je clique sur le bouton pour bouger la ligne").

## design-system/08-organisms/icon-picker.md

- 2026-11-23: "t'as juste l'impression que c'est une icône comme les autres"
  - In: - The reset is set apart from the icons, after a vertical divider, as a `quiet` icon button: it never reads as one more icon (Product Owner, 2026-11-23: "t'as juste l'impression que c'est une icône comme les autres").

## design-system/08-organisms/markdown-editor.md

- 2026-11-22
  - In: - No read-only mode (Product Owner, 2026-11-22).

## design-system/08-organisms/palette-picker.md

- 2026-11-23, said of the icon-picker
  - In: - The reset is set apart from the colours, after a vertical divider, as a `quiet` icon button: it never reads as one more choice (Product Owner, 2026-11-23, said of the icon-picker; the same here).

## design-system/10-screens/01-metadata/04-signal-settings.md

Called 06-presets.md until 2026-11-24; the first sentence below no longer holds (a signal sits on one line since then).

- 2026-11-22
  - In: Every signal in write is on two lines. The title Elements sits `spacing-03` (8) above its first element, the other blocks of the preset `spacing-05` (16) apart (Product Owner, 2026-11-22).
- 2026-11-22
  - In: The grouped list the display unit `bar` of `pressure_out` opens: a transparent frame of the size of the screen, the list right under its select. Two groups: Metric, then US customary, which holds psi, inHg, inH2O and ftH2O (Product Owner, 2026-11-22).

## design-system/skill-rules.md

- 2026-11-22
  - In: - **Rule**: the Figma file has the pages Foundations, Icons, Atoms, Molecules, Organisms, Templates, then Metadata, the screens of Metadata, in the library file itself (Product Owner, 2026-11-22).
- 2026-11-22
  - In: - **Rule**: one theme, built on the colours of the old Warm Sand theme; only the colours needed are kept (Product Owner, 2026-11-22).
- 2026-11-22
  - In: - **Rule**: dense screens, with every control larger than Figma's, for people from 20 to 77 (Product Owner, 2026-11-22). Controls 32 px high, text 14 px (proposed in Foundations).
- 2026-11-22
  - In: - **Rule**: every screen in 16:9; the smallest window is 1600 × 900, and nothing is promised below it, under the exemption of WCAG for two-dimensional layouts (Product Owner, 2026-11-22).
- 2026-11-22
  - In: - **Rule**: every component drawn whole, with its variants and its states; never an empty or hollow component (Product Owner, 2026-11-22).
- 2026-11-22: "une ligne claire et une ligne avec ton violet foncé"
  - In: - **Rule**: the keyboard focus of every component is two lines: a light one against the component, then a dark violet one around it, so it shows on a light or a dark component (Product Owner, 2026-11-22: "une ligne claire et une ligne avec ton violet foncé"). For this design system only. Its values …
- 2026-11-22
  - In: - **Rule**: every interactive component is prototyped as an interactive component of Figma (hover, press, click to the next state), before any screen is (Product Owner, 2026-11-22).
- 2026-11-22: "un tableau d'états et de types [...] plutôt que plein de texte à la con qui ne sert à rien"
  - In: - **Rule**: in the Figma file, each component is shown as a clean table: one column per state (default, hover, pressed, focus, disabled…), one line per variant, each line and each column named, so one sees at once which variant and which state each cell is. No documentation frame and no descriptive …
- the same day: "ça va remplacer tes petites fiches [...] vu que c'est en Markdown, ce sera beaucoup plus propre"
  - In: - **The sheets**: the description goes in the specification, one Markdown sheet per component, in the folder of its level (`atoms/`, `molecules/`, `organisms/`, `templates/`), beside the table exported as SVG: what it is, its inputs and outputs, its behaviour, its link in Figma, the components it is…

## metadata/documentation-plan.md

- 2026-11-22
  - In: - The writing rules of the entity files: to become the skill `write-a-metadata-entity-file` of the assistant, in `.claude/skills/` of the programme (Product Owner, 2026-11-22); until then in Writing rules.
- 2026-11-22
  - In: - The order of the missing documents after the glossary, the inheritance of types, deleting, checks and errors, identity and renaming, and units on screen, written in that order (Product Owner, 2026-11-22). Editing without versions comes next, when the specification resumes.

## metadata/units-on-screen.md

- 2026-11-22
  - In: - **The page is read only** (MD-08): it lists the quantities, one line each with the icon `quantity` and, when it has one, the icon `difference`; a quantity shows a switch Quantity | Difference when it has a difference, then its default unit and its unit systems (Product Owner, 2026-11-22); a unit s…

## screens/README.md

- 2026-11-16
  - In: Status: draft, written by the assistant on 2026-11-11 from the pages of Metadata and Symbols. It adds no rule: it only shows, screen by screen, what the specs already say. Where the specs say nothing, it says so. The only rules written here are the layout rules, which hold for every screen (Product …
- 2026-11-17: "à chaque décision qui change un écran [...] faut changer les specs et les écrans sur Figma"
  - In: - **Every decision that changes a screen changes, in the same go, the pages of the part, this inventory and the wireframe in Figma** (Product Owner, 2026-11-17: "à chaque décision qui change un écran [...] faut changer les specs et les écrans sur Figma"). Never one without the others.
- : "Preset, ça ne doit pas être le titre de toute la page. Tu dois juste mettre Preset comme titre de la liste et avoir un petit + à droite"
  - In: - The title is the title of the list, not of the whole page: the page itself has no big title that repeats it (Product Owner: "Preset, ça ne doit pas être le titre de toute la page. Tu dois juste mettre Preset comme titre de la liste et avoir un petit + à droite"). The room saved goes to the content…
- 2026-11-16, for the links: "ça va pas rapide, alors que là, tu peux faire clac-clac. C'est beaucoup plus rapide"
  - In: - When a list takes items of several kinds, there is **one small icon per kind, each with a small +**, side by side on the line of the title, rather than one + that opens a menu: two clicks at most, with no menu to read (Product Owner, 2026-11-16, for the links: "ça va pas rapide, alors que là, tu p…
- 2026-11-16
  - In: - It holds in the symbol mode and for the pipes too (Product Owner, 2026-11-16): the + that creates a Symbol Lib, a pipe style, an override of a pipe style, and a segment of a dash sequence sits on the right of the title of its list.
- 2026-11-17: "On peut pas changer l'ordre, ça me chante pas"
  - In: - Where it does not: the items of an enum (Product Owner, 2026-11-17: "On peut pas changer l'ordre, ça me chante pas").
- 2026-11-17: "c'est à la personne de savoir qu'elle supprime quelque chose et qu'il faut faire attention [...] sinon ça va le dire tout le temps et ça ne sert à rien"
  - In: - **The warning never says what the delete breaks** (Product Owner, 2026-11-17: "c'est à la personne de savoir qu'elle supprime quelque chose et qu'il faut faire attention [...] sinon ça va le dire tout le temps et ça ne sert à rien"). What is broken is listed in the symbol mode and in the synoptic …
- 2026-11-16
  - In: 1. The **logo**: a valve, like the logo already in the Figma file (Product Owner, 2026-11-16). The word "Epipasta" heard earlier was a transcription error; the wireframes said "Logo · a valve" until the Product Owner pointed to the logo of the page "Cover" (2026-11-17); since then every top bar of t…
- 2026-11-17: "il y a un espace de taré, ça fait ultra moche"
  - In: 2. Three icons, one per part: **Metadata**, **Symbols**, **Synoptic** (part 3, extrapolated on 2026-11-20, see Synoptic), **right after the logo, with the normal gap of the bar**: no wide empty space between the logo and the three parts (Product Owner, 2026-11-17: "il y a un espace de taré, ça fait …

## screens/metadata.md

- 2026-11-16
  - In: Path: on the far left of every screen of Metadata (Product Owner, 2026-11-16).
- 2026-11-22: the divider before Designations alone had no meaning, the Product Owner asked to keep it only if it had one
  - In: | MD-00.7 | Divider | — | After Types: the types on one side, what they use on the other, Units, Enums and Designations (2026-11-22: the divider before Designations alone had no meaning, the Product Owner asked to keep it only if it had one; assistant's choice). | Proposed | Layout rules |
- 2026-11-22: "quand on over une icône, [...] un petit truc qui s'affiche pour dire ce que c'est", "si on laisse hover pendant longtemps"
  - In: | MD-00.8 | Name of a button | Tooltip | When the mouse stays on an icon of the bar, a tooltip gives the name of its page, on its right: Types, Units, Enums, Designations; the parts of the top bar do the same under them: Metadata, Symbols, Synoptic (Product Owner, 2026-11-22: "quand on over une icôn…
- 2026-11-22: "deux boutons comme ça pour tout ouvrir, tout fermer"
  - In: | MD-01.7 | Open all, close all | Two buttons (icon) on the line of the title, left of the search | Open all unfolds every branch of the tree, close all folds them all, to find a type faster (Product Owner, 2026-11-22: "deux boutons comme ça pour tout ouvrir, tout fermer"). Icons `expand-all` and `c…
- 2026-11-22: "pour qu'on voie que c'est pas la même chose"
  - In: | MD-01.8 | Divider between the tree and the parts | Line | A horizontal line across the column, between the type tree and the list of the parts, so that they read as two different things (Product Owner, 2026-11-22: "pour qu'on voie que c'est pas la même chose"). | Decided | — |
- 2026-11-11, confirmed on 2026-11-16
  - In: Path: Metadata › Types › a type › General. Complete: nothing more is needed (Product Owner, 2026-11-11, confirmed on 2026-11-16).
- 2026-11-22
  - In: | MD-02.4 | Parent | — | Removed (Product Owner, 2026-11-22): General does not show the parent, which the tree already shows. The parent is set at creation and never changed (decision 0013); a wrong parent: delete the type and create it again. | Decided | Types |
- 2026-11-22
  - In: | MD-02.8 | Delete the type | Button, then a warning (dialog) | In General (2026-11-16): the only way to delete a type. A click opens a warning that asks to confirm. Refused while the type has sub-types: they are deleted first (decision 0082). The warning says "Delete centrifugal_pump?" (the ID of t…
- 2026-11-22
  - In: | MD-03.1 | Description, read only | — | Removed (Product Owner, 2026-11-22): only Visual and Markdown. | Decided | Documentation |
- 2026-11-22, questionnaire: "Oui, le garder"
  - In: | MD-03.1b | Title "Description" | Title, above the editor | Tells what the text is, as "Links" does for the links (Product Owner, 2026-11-22, questionnaire: "Oui, le garder"). | Decided | Documentation |
- 2026-11-22
  - In: | MD-03.4d | Formatting tool bar | Buttons | In Visual and in Markdown (2026-11-16). Like a word processor: heading levels, lists, tables and the rest of Markdown (proposed list in Documentation); no text colour. Bold, italic, strikethrough: toggles that show the state of the selection; the heading:…
- 2026-11-23
  - In: | MD-03.13 | Table in the visual editor | Table, with small + on hover | A table of the description shows as a table, header line first. Under the mouse, a small round + sits between two lines, on the left edge, and between two columns, on the top edge: a click inserts a line or a column there; a + …
- 2026-11-23
  - In: | MD-03.13 | Table in the visual editor | Table, with small + on hover | A table of the description shows as a table, header line first. Under the mouse, a small round + sits between two lines, on the left edge, and between two columns, on the top edge: a click inserts a line or a column there; a + …
- 2026-11-23
  - In: | MD-03.14 | Headings of the description | Text styles | Heading 1 to 6 are all larger than the paragraph, down to Heading 6, so that a bold line never reads as a heading (Product Owner, 2026-11-23). Sizes proposed: 28, 24, 20, 18, 17, 16 against 14 for the paragraph. | Decided (rule), Proposed (siz…
- 2026-11-16
  - In: The signals are shown in **one table** that takes as much room as possible: one line per signal, one column per field (Product Owner, 2026-11-16). It replaces the list on the left and its panel on the right, drawn earlier the same day. The + that adds a signal is a small icon on the right of the tit…
- 2026-11-22
  - In: | MD-04.3 | Inherited signals | Lines of the table | First, read only: the signals of the first parent at the top of the tree, then of the next parent, then the type's own (2026-11-16). Edited in the type that declares them. Drawn read only, with no handle nor delete; the line never names its parent…
- 2026-11-16
  - In: As for the signals, the commands are shown in **one table**, the kind in the first column (Product Owner, 2026-11-16). The + that adds a command is a small icon on the right of the title "Commands".
- 2026-11-17: "c'est juste pour que, visuellement, ce soit plus simple"
  - In: Path: Metadata › Types › a type › Flags, fifth part of the type, between Commands and Presets. Described by the Product Owner on 2026-11-17; name and place given by him the same day ("flag, ça me va très bien"; "la page, elle fait partie des types"). An ID and a description per flag given by him the…
- 2026-11-16, while reviewing the wireframes
  - In: The list of presets is on the left, under its title "Presets" and the small + on its right; the page has no big title. The selected preset is on the right: a **switch** between its two modes at the top, then its name, then the mode chosen (Product Owner, 2026-11-16, while reviewing the wireframes; t…
- 2026-11-22
  - In: | MD-07.12 | Display unit | Column, select | Mode Values. For every integer and real (each has a quantity, 2026-11-19, decision 0051); starts as the default unit of the quantity (Units on screen). Changing it never changes the start value: only how it is shown. Its list is grouped by unit system (Pr…
- 2026-11-22: "le groupe custom dans les unités, il n'existe pas"
  - In: | MD-07.12 | Display unit | Column, select | Mode Values. For every integer and real (each has a quantity, 2026-11-19, decision 0051); starts as the default unit of the quantity (Units on screen). Changing it never changes the start value: only how it is shown. Its list is grouped by unit system (Pr…
- 2026-11-16, the rule of the links, confirmed by the Product Owner the same day
  - In: | MD-07.18 | Add an element | Buttons (small icons with a +) | Mode Faceplate, on the right of the title "Elements": one icon per kind, a signal, a command, a title, a description, a group, no menu (2026-11-16, the rule of the links, confirmed by the Product Owner the same day). Each icon carries it…
- 2026-11-22: "tout le temps en deux lignes, peu importe ce que c'est"
  - In: | MD-07.10 | Input | Select, in a signal element | Chosen in the builder (end of 2026-11-17: "on met input number, par exemple"). Enum: radio on one line, radio on several lines, select; its items in the order of their keys (2026-11-22, MD-09.5). Number: a number field, with its bounds (MD-07.22). B…
- 2026-11-22
  - In: | MD-07.10 | Input | Select, in a signal element | Chosen in the builder (end of 2026-11-17: "on met input number, par exemple"). Enum: radio on one line, radio on several lines, select; its items in the order of their keys (2026-11-22, MD-09.5). Number: a number field, with its bounds (MD-07.22). B…
- 2026-11-22
  - In: | MD-07.21 | Delete an element, delete a preset | Button, then a warning | An element: an icon at its far right (2026-11-16). A preset: a red button "Delete the preset" on the line of its name, on the right of the field, as "Delete the type" in General; no delete on the lines of the list (Product Ow…
- 2026-11-16
  - In: **The whole page is read only** (Product Owner, 2026-11-16): the catalogue ships with the software, and contributors complete its files; no +, no field that changes the catalogue, no delete. The only field is the converter of a unit system, which tries a value and keeps nothing (2026-11-17).
- 2026-11-22
  - In: | MD-08.1 | List of quantities | List | Mass, volume, flow... One line per quantity, its difference included: its name, then the small icon `quantity`, and the icon `difference` when it has one (Product Owner, 2026-11-22; replaces the difference shown under its quantity). The difference stays a quan…
- 2026-11-22
  - In: | MD-08.15 | Quantity or difference | Switch (two buttons) | At the top of a quantity that has a difference, under its title: Quantity or Difference; the same page in both, default unit, unit systems, converter and table (Product Owner, 2026-11-22). The quantity opens first (assistant's reading). | …
- 2026-11-16
  - In: | MD-08.2 | Add a quantity, a unit system, a unit | — | Removed (Product Owner, 2026-11-16): the page is read only; a missing unit is added by a contributor to the catalogue files. | Decided | Units |
- 2026-11-22
  - In: | MD-08.7 | Table of units | Table, read only, whole width | One line per unit; a line lights on hover, to help reading it, and a click on it does nothing (Product Owner, 2026-11-22). Columns: Unit (name with its variant: US gallon), Symbol, Value, Formula. Flat units (`m³/h` is one unit). No ratio …
- 2026-11-16: "au niveau des enums [...] avec une icône", then "un petit +, une petite icône à côté du titre"
  - In: | MD-09.2 | Add an enum | Button (+), small icon | On the right of the title "Enums", above the list (Product Owner, 2026-11-16: "au niveau des enums [...] avec une icône", then "un petit +, une petite icône à côté du titre"). | Decided | Layout rules |
- 2026-11-19: "ça devrait être ID"
  - In: | MD-09.3 | ID | Text field | The public identifier of the enum, as the ID of a signal (Product Owner, 2026-11-19: "ça devrait être ID"; replaces "Name"). Unique among the enums (2026-11-22); an ID already taken is refused when typed (decision 0083). | Decided | Data model |
- 2026-11-22, Product Owner: nothing showed what a template is
  - In: | MD-09.10 | Kind: Global or Template | Choice when the enum is made (control not said) | Global: the items are written here, the same everywhere. Template: an ID and a description only, no items here; the items are completed on each placed symbol, in the synoptic, with a small warning until they ar…
- end of 2026-11-17
  - In: | MD-09.11 | Description of the enum | Text field (several lines) | What the enum is about as a whole, for a template and for a global enum alike (Product Owner, end of 2026-11-17). Plain text, never sent to the model. | Decided | Enums |
- 2026-11-16
  - In: | MD-09.4 | Kind of key | — | Removed (Product Owner, 2026-11-16): a key is always a number, there are no string keys. | Decided | Enums |
- 2026-11-22: "les trier par numéro et puis point barre"
  - In: | MD-09.5 | Items | Table | Columns in this order: Key, Display name, Description, then the delete button with no header (2026-11-17: the short field first, the long one last; replaces Key, Description, Display name of 2026-11-16). The lines are in the order of their keys, smallest first, and nothin…
- 2026-11-22: "les trier par numéro et puis point barre"
  - In: | MD-09.12 | Handle of an item | — | Removed (Product Owner, 2026-11-22: "les trier par numéro et puis point barre"): the items are in the order of their keys only. | Decided | Enums |

## screens/symbols.md

- 2026-11-16
  - In: Path: Symbols. On the far left of every screen of the symbol mode (Product Owner, 2026-11-16; changed by him at the end of 2026-11-17).
- 2026-11-15
  - In: The layout is decided (Product Owner, 2026-11-15), except the place of the tool bar (bottom or top) and of the zoom field.
- 2026-11-17
  - In: | SY-08.4b | Input range of a bounded linear | Two fields: minimum, maximum | Each a signal of the type, input or output, or a number typed (the number: to confirm); the value animated stays an output (Product Owner, 2026-11-17). | Decided (signal in or out), Proposed (number) | Animation mode |

## storage/git.md

- : "on verra ça après"
  - In: Status: noted from the Product Owner's message of 2026-11-22, for later. Not to draw nor to detail yet (Product Owner: "on verra ça après"). Not validated.
- 2026-11-22: "on ne va absolument pas gérer ça"
  - In: - **No versions managed by the application** (Product Owner, 2026-11-22: "on ne va absolument pas gérer ça"). It confirms decision 0053.

## symbols/01-libraries-and-symbols.md

- 2026-11-16
  - In: A **Symbol Lib** holds symbols. It is the only kind of library: there are no libraries of types (Product Owner, 2026-11-16). This page is about the Symbol Lib, how a symbol is created, and what happens to a symbol when Metadata changes.
- 2026-11-15
  - In: - **One list of symbols only** (Product Owner, 2026-11-15). There is no "static" or "dynamic" kind: every symbol is the same kind of object, and a symbol simply has a type or not yet. The Product Owner settled it so that the software is simpler to understand at first.
-
  - In: - Why (Product Owner): the pipes are no longer mixed with the symbols, the libraries are only on the left, and the pages sit under them; "c'est plutôt simple à comprendre".
- 2026-11-15
  - In: | Symbols | A search field (a small magnifier), a **+** button to create a symbol, then the list; a click on an item opens the symbol in the editor. Under it, the **layers** of the open symbol: see Layers (Product Owner, 2026-11-15). |
- 2026-11-15
  - In: - The **+** of the symbol list creates a symbol. The type, and the preset, **can** be chosen at creation, among all the types of Metadata, but nothing is imposed (Product Owner, 2026-11-15).
- 2026-11-17: "si ça casse, ça ne dit pas forcément, parce que sinon ça va le dire tout le temps et ça ne sert à rien. Par contre, une fois qu'on est en mode synoptique ou symbole, là, il y a une liste des choses cassées"
  - In: - **Metadata never warns about what a change breaks**; the symbol mode and the synoptic mode show **a list of what is broken** (Product Owner, 2026-11-17: "si ça casse, ça ne dit pas forcément, parce que sinon ça va le dire tout le temps et ça ne sert à rien. Par contre, une fois qu'on est en mode s…

## symbols/02-type-and-faceplate.md

- 2026-11-15
  - In: - A symbol has at most one type, among all the types of Metadata (no library of types since 2026-11-16). The type is never imposed: it can be chosen when the symbol is created, or later, and changed afterwards (Product Owner, 2026-11-15). Both happen in the symbol editor and only there (see Types). …
- 2026-11-15
  - In: - The type and the preset are chosen in the **right-hand panel** of the editor (Product Owner, 2026-11-15). Assumption of the assistant: the panel shows them when no shape is selected, as the settings of the symbol itself.

## symbols/03-editor/README.md

- the Product Owner's leaning: "for people, the bottom will be better"
  - In: | Tool bar | A floating bar over the drawing area, with the tools of the current mode. Its place is open: at the **bottom** (the Product Owner's leaning: "for people, the bottom will be better") or at the top. |
- 2026-11-11
  - In: - **Same keys on every platform** (Product Owner, 2026-11-11). Windows, macOS and Linux behave the same. Only keys that exist on all three are used: Shift, Ctrl and Alt (the Option key on a Mac), with letters, digits, arrows and function keys. No Command, Option or Windows key in the specs. Whenever…
- dropped by the Product Owner on 2026-11-15: one kind of symbol
  - In: | Static, dynamic | Keep (dropped by the Product Owner on 2026-11-15: one kind of symbol) | Same words in the archived Figma file |

## symbols/03-editor/expert-menu/README.md

- 2026-11-15
  - In: - A button of the floating tool bar shows or hides a **second bar**, just above the tool bar, with **all** the advanced tools (Product Owner, 2026-11-15). It replaces the menu with three small dots.

## symbols/03-editor/layers.md

- 2026-11-15
  - In: - It works like the layers panel of Figma and like the file tree of a code editor (Product Owner, 2026-11-15).

## symbols/03-editor/precise-move.md

- 2026-11-15
  - In: - While the user drags a marker with the mouse (a point, a curve handle, and the like), holding a modifier key makes the move **precise**: the marker moves slowly, and can be placed pixel by pixel of the symbol (Product Owner, 2026-11-15).
-
  - In: - The key is not chosen yet: Shift, Alt or Ctrl, "to find" (Product Owner). It follows the rule of the editor: the same key on Windows, macOS and Linux.
-
  - In: | Point of a path | Yes (Product Owner) |
-
  - In: | Curve handle | Yes (Product Owner) |

## symbols/04-drawing-mode/rectangle.md

- the Product Owner chooses among those
  - In: - Keys must be the same on every platform (Shift, Ctrl, Alt only: see the rule in the editor). Keys in other software (research report; the Product Owner chooses among those): square with Shift in Figma, Sketch and Illustrator, with Ctrl in Inkscape and CorelDRAW; from the centre with Alt (Option) i…

## symbols/07-interaction-mode/README.md

- the Product Owner wants more than these three
  - In: - Several gestures are possible on a place: left click, right click, double click, and others (the Product Owner wants more than these three; the list is to settle).
- decided by the Product Owner, 2026-11-11
  - In: - **opening the faceplate** of the element (decided by the Product Owner, 2026-11-11): the user says "this opens the faceplate of the element" (see Type, preset and faceplate).

## symbols/08-animation-mode/README.md

- 2026-11-16, accepting the assistant's proposal
  - In: - Since commands always send a fixed value (2026-11-16, see Commands), this text **writes an input signal of the type directly**, with the same checks as a write entry of the faceplate: conversion from the display unit, enum item, and the bounds of the number field, typed by hand or taken from a sig…
- 2026-11-18
  - In: - **No text input** (Product Owner, 2026-11-18): a signal is never a text (see Signals).
- : "pour les bornes, on pourra choisir soit un in, soit un out"
  - In: - Each of the two can be **a signal of the type**, an input or an output (Product Owner: "pour les bornes, on pourra choisir soit un in, soit un out"). Example: the maximum taken from `speed_setpoint_max`, an input.
- : "il n'y a que la valeur qui change qui devrait être obligatoirement out"
  - In: - **The value that drives the animation is always an output** of the model (Product Owner: "il n'y a que la valeur qui change qui devrait être obligatoirement out"), as for every animation.

## symbols/09-run-mode/README.md

- decided by the Product Owner, 2026-11-11
  - In: - The control depends on the type (decided by the Product Owner, 2026-11-11):
- assumed by the assistant, the Product Owner named only the two above
  - In: | A boolean | A switch (assumed by the assistant, the Product Owner named only the two above). |

## symbols/10-open-questions.md

- the Product Owner's leaning
  - In: | Place of the floating tool bar: bottom or top of the drawing area. | Editor | Bottom, centred (the Product Owner's leaning). |
- 2026-11-18
  - In: | The list of faults of the application: what puts a symbol in fault, how it shows, how it is repaired (Product Owner, 2026-11-18). | Sub-symbols | Start from the small red mark of a broken link. |

## symbols/11-enums-of-a-symbol-lib.md

- 2026-11-17: "dans chaque lib, tu auras une petite page enum"
  - In: - **One Enums page in each Symbol Lib** (Product Owner, 2026-11-17: "dans chaque lib, tu auras une petite page enum"). It opens from the navigation bar, as the second page of the selected library, after General (Product Owner, end of 2026-11-17; see Libraries and symbols).
- the Product Owner's examples
  - In: - a **kind of value**, chosen in a list: colour, text, number (the Product Owner's examples; "peu importe", the full list is open).
- : "son background color utilise la propriété color de l'enum qu'on a créé côté symbole"
  - In: - In the Animation mode, the user picks an output signal of the type enum, then a property of the drawing (background colour, text...), then **the column of the enum** that gives its value (Product Owner: "son background color utilise la propriété color de l'enum qu'on a créé côté symbole").
- end of 2026-11-17
  - In: Noted, not to be asked again in the chat (Product Owner, end of 2026-11-17): they will come up when the Product Owner gets to them.

## symbols/12-sub-symbols.md

- 2026-11-18: "t'as un symbole parent et tu peux créer un sous-symbole [...] ça prend [ce] qui a été fait pour le symbole, et tu peux rajouter [...] en plus"
  - In: A symbol can have a **parent symbol**, as a type of Metadata has a parent type (see Types). A **sub-symbol** starts from everything made for its parent, and the user adds more on top of it (Product Owner, 2026-11-18: "t'as un symbole parent et tu peux créer un sous-symbole [...] ça prend [ce] qui a …
- 2026-11-18
  - In: - A sub-symbol takes what was made for its parent symbol, then the user adds to it: shapes, and the links of these shapes to the signals and commands (Product Owner, 2026-11-18).
- 2026-11-18
  - In: - A sub-symbol can itself have sub-symbols: the example below has three levels (Product Owner, 2026-11-18).
- 2026-11-18
  - In: - **The changes of the parent reach its sub-symbols** (Product Owner, 2026-11-18): a sub-symbol is linked to its parent, never a copy made once. The valve is corrected once, and the motorised valve and the motorised valve with command follow. It is the inheritance of Metadata, applied to symbols.
- 2026-11-18
  - In: - **A sub-symbol only adds** (Product Owner, 2026-11-18): what it takes from its parent is read only in it, as the inherited signals of a type are (see Signals). It cannot change it, move it or hide it. To change it, the user opens the parent.
- 2026-11-18
  - In: - **Its type is the type of its parent, or a sub-type of it** (Product Owner, 2026-11-18). So the animations and interactions taken from the parent keep their signals and commands. In the example, the motorised valve with command can have a sub-type of the valve's type that adds the commands open an…
- 2026-11-18: "oui, tout pareil"
  - In: - **It takes everything from its parent** (Product Owner, 2026-11-18: "oui, tout pareil"): the drawing, the animations, the interactions, the **preset** and the **connection points** of its pipes. "If the parent already has a type, the sub-symbol can only take the same type or a sub-type, and it tak…
- 2026-11-18
  - In: - **The list of symbols of a Symbol Lib is a tree, as in Metadata** (Product Owner, 2026-11-18): a sub-symbol sits under its parent. It replaces the flat list decided on 2026-11-11 (decision 0045, accepted on 2026-11-18, which changes decision 0010). The list of pipe styles stays flat.
- 2026-11-18: "un parent peut-il être dans une autre Symbol Lib ? Non"
  - In: - **The parent is always in the same Symbol Lib** as its sub-symbol (Product Owner, 2026-11-18: "un parent peut-il être dans une autre Symbol Lib ? Non").
- 2026-11-18: "dans la logique, oui"
  - In: - **Parent without a type**: the sub-symbol can take **any type** (Product Owner, 2026-11-18: "dans la logique, oui"), since there is nothing to keep.
- 2026-11-18: "on met tout le monde en défaut et on le dit"
  - In: - **The parent changes type, or loses it**: **every sub-symbol goes into fault, and the application says so** (Product Owner, 2026-11-18: "on met tout le monde en défaut et on le dit"). Nothing is repaired by itself. How a fault shows and how the user repairs it come with the list of faults (see Ope…
- 2026-11-18: "oui, on peut"
  - In: - **A parent that has sub-symbols can be deleted** (Product Owner, 2026-11-18: "oui, on peut").
- 2026-11-18, answer to the questionnaire: "supprimés avec lui"
  - In: - **Its sub-symbols are deleted with it**, at every level below it (Product Owner, 2026-11-18, answer to the questionnaire: "supprimés avec lui"; decision 0046, accepted on 2026-11-18). In the example, deleting the valve deletes the motorised valve and the motorised valve with command.
- 2026-11-18: "on verra ça après, quand je passerai sur la page symbole"
  - In: Left for the review of the Symbols part: the Product Owner settles them then, and they are not asked before (Product Owner, 2026-11-18: "on verra ça après, quand je passerai sur la page symbole"). The assistant's reading of "l'IA" also waits for that review.
- 2026-11-18: "il faudra faire une liste des défauts"
  - In: - **The list of faults.** A sub-symbol goes into fault when its parent changes type or loses it (Product Owner, 2026-11-18: "il faudra faire une liste des défauts"). The list of every fault of the application is to write: what puts a symbol in fault, how it shows (the small red mark of a broken link…

## symbols/README.md

- 2026-11-15
  - In: There is one list of symbols and one kind of symbol (Product Owner, 2026-11-15): no "static" or "dynamic" symbol any more.
- 2026-11-16
  - In: The only kind of library is the **Symbol Lib**, which sorts symbols. There are no libraries of types (Product Owner, 2026-11-16): a symbol picks its type among all the types of Metadata.

## symbols/pipes/README.md

- decided by the Product Owner, 2026-11-11
  - In: - **Everything lives in the pipe style** (decided by the Product Owner, 2026-11-11): the junctions, the crossings and the start and end shapes are parts of the pipe style, not separate lists of the Symbol Lib. They are computed, not edited by hand: the user chooses one style for a pipe, and the styl…

## symbols/pipes/crossings.md

- decided by the Product Owner, 2026-11-11
  - In: - The user chooses the **type of crossing** in the **base pipe style**, and a pipe style can override it (see Pipe styles); it is not a separate list of the Symbol Lib (decided by the Product Owner, 2026-11-11):

## symbols/pipes/ends.md

- decided by the Product Owner, 2026-11-11
  - In: - End shapes are parts of the base pipe style, and a pipe style can override them (see Pipe styles); they are not a separate list of the Symbol Lib (decided by the Product Owner, 2026-11-11). In the synoptic, each end of a pipe offers the shapes of its style, or none (as in the archived Figma page).

## symbols/pipes/junctions.md

- decided by the Product Owner, 2026-11-11
  - In: - The look of a junction is set in the **base pipe style** of the Symbol Lib, and a pipe style can override it (see Pipe styles); it is not a separate list of the Symbol Lib (decided by the Product Owner, 2026-11-11). It is computed; the user does not edit it by hand.
- 2026-11-11
  - In: - **Propagation** (Product Owner, 2026-11-11): when the dashes of a pipe move, the movement goes on through the junction into the branches, following the flow (see Pipe styles).

## symbols/pipes/pipe-styles.md

- decided by the Product Owner, 2026-11-11
  - In: - Junctions, crossings and end shapes are parts of the style, not separate lists of the Symbol Lib (decided by the Product Owner, 2026-11-11). They are computed from the style; the user never draws them on each pipe.
- 2026-11-11
  - In: - It is not a hard requirement (Product Owner, 2026-11-11): where a dash cuts a little oddly in a corner, it is accepted as it is.
- 2026-11-16
  - In: - The type is chosen among all the types of Metadata, as for a symbol: there are no libraries of types (Product Owner, 2026-11-16).
- 2026-11-11
  - In: - The report advised a separate native stroke for the flow dashes. **Superseded**: the dashes are now a fill of the body or of the border, computed (Product Owner, 2026-11-11).

## symbols/research-brief.md

- the Product Owner decides, on the report and the POC
  - In: The code, the performance measures (they come from the POC), the geometric engine and the intersection calculations (another research), the SaaS, phones and tablets, and the final choice of effects (the Product Owner decides, on the report and the POC).

## synoptics/04-placed-symbol-panel.md

- 2026-11-21: "Sur tous les symboles placés"
  - In: - **Every required designation** is shown on every placed symbol, whether or not the faceplate of its preset uses it, and marked as required (Product Owner, 2026-11-21: "Sur tous les symboles placés").
- 2026-11-21: "Avertir sans bloquer"
  - In: - **A required text left empty warns, never blocks** (Product Owner, 2026-11-21: "Avertir sans bloquer"): the field is marked, the section shows the small warning mark, the placed symbol is listed in the faults as a warning, and the synoptic is saved anyway.

## synoptics/05-pipes.md

- the Product Owner wants a path by clicks
  - In: - Should the editor route a pipe around symbols by itself? Not in the first version (the Product Owner wants a path by clicks).

## synoptics/10-outputs.md

- 2026-11-22
  - In: Once the synoptics are done, the editor writes, for the models, a kind of interface description document (IDD): for each type used in the project, it shows every signal of the type, and says which ones the project really needs, given how its symbols are used in the synoptics (Product Owner, 2026-11-…

## synoptics/12-open-questions.md

- 2026-11-20: "les modeleurs [...] vont avoir les vues synoptiques en mode readonly. Quand ils cliqueront sur un symbole, ils auront les informations, des fiches récapitulatives en fonction des symboles [...] on verra ça plus tard"
  - In: - **A read-only way in for model authors** (Product Owner, 2026-11-20: "les modeleurs [...] vont avoir les vues synoptiques en mode readonly. Quand ils cliqueront sur un symbole, ils auront les informations, des fiches récapitulatives en fonction des symboles [...] on verra ça plus tard"): the synop…

## Dated quotes

### screens/metadata.md

- 2026-11-18: "C'est une page de type unit enum version"
  - In: | MD-00.6 | Designations | Button (icon) | Opens MD-13. A page of the bar, like Units and Enums (2026-11-18: "C'est une page de type unit enum version"). Last, after Enums: assistant's reading. Named Designations on 2026-11-22 (decision 0064), "Identifiers" until then. | Decided (page of the bar, na…
- 2026-11-22: "y a pas de petit + dessus [...] on ne sait pas vraiment si c'est pour ajouter"
  - In: | MD-07.18 | Add an element | Buttons (small icons with a +) | Mode Faceplate, on the right of the title "Elements": one icon per kind, a signal, a command, a title, a description, a group, no menu. Each icon carries its small + at its bottom right, as the icons of Links, so that it reads as "add" (…
- end of 2026-11-17: "on met input number, par exemple"
  - In: | MD-07.10 | Input | Select, in a signal element | Chosen in the builder (end of 2026-11-17: "on met input number, par exemple"). Enum: radio on one line, radio on several lines, select; its items in the order of their keys (2026-11-22, MD-09.5). Number: a number field, with its bounds (MD-07.22). B…
- end of 2026-11-17: "c'est read write pour un input et read override pour un output"
  - In: | MD-07.11 | Read or write, read or override | Radio, in a signal element | Input: read or write. Output: read or override (end of 2026-11-17: "c'est read write pour un input et read override pour un output"; corrects the single "read or override" written earlier that day). Write or override: a pers…
- 2026-11-22: "le min max, j'ai l'impression qu'ils sont pas la même taille"
  - In: | MD-07.22 | Minimum, maximum of a number field | Number field each, with a small icon inside to pick a signal | On the second line of the signal element, after the kind of input, both of the same width (2026-11-22: "le min max, j'ai l'impression qu'ils sont pas la même taille"; two lines: assistant…
- end of 2026-11-17: "il y a déjà les poignées là"
  - In: | MD-07.17 | Order | Rule | Mode Values: the order of Signals, no handle, no sort. Mode Faceplate: the order of the builder, moved with a handle (end of 2026-11-17: "il y a déjà les poignées là"). | Decided | Presets |
- 2026-11-17: "ça sert à rien de remettre le nom juste en dessous"
  - In: | MD-08.12 | Name of the quantity | Title | The title of the quantity's column; not written again under it (2026-11-17: "ça sert à rien de remettre le nom juste en dessous"). | Decided | Units |
- 2026-11-17: "je mets 1 kg et [...] je vois combien de pounds ça fait et combien d'ounces"
  - In: | MD-08.13 | Converter | Number field | At the top of the unit system, in the default unit of the quantity, 1 to start with (2026-11-22, decision 0085). Its value is converted on every line of the table; nothing is kept (2026-11-17: "je mets 1 kg et [...] je vois combien de pounds ça fait et combien…
- 2026-11-19: "C'est plus simple comme ça"
  - In: | MD-08.7 | Table of units | Table, read only, whole width | One line per unit; a line lights on hover, to help reading it, and a click on it does nothing. Columns: Unit (name with its variant: US gallon), Symbol, Value, Formula. Flat units (`m³/h` is one unit). No ratio column (2026-11-17: the rati…
- 2026-11-18: "faire un tableau"
  - In: | MD-13.1 | Table of designations | Table, whole width | One line per designation (2026-11-18: "faire un tableau"). Columns in this order: the handle with no header, ID, Required, Description, then the delete button with no header (order: assistant's reading; the order of the fields of a designation…
- 2026-11-18: "Il faut pouvoir leur donner un ordre"
  - In: | MD-13.3 | Handle of a line | Grip, dragged, no header | The user chooses the order (2026-11-18: "Il faut pouvoir leur donner un ordre"). | Decided | Layout rules |
- 2026-11-22: "Unique, pour les enums et les désignations"
  - In: | MD-13.4 | ID | Text field | The key. Always editable, followed through its internal ID when renamed (assistant's reading of the general rule). Unique among the designations (2026-11-22: "Unique, pour les enums et les désignations"); an ID already taken is refused when typed (decision 0083). | Deci…
- 2026-11-21: "on va dégager display name [...] on voit que l'ID"
  - In: | MD-13.5 | Display name | — | Removed (2026-11-21: "on va dégager display name [...] on voit que l'ID"): the ID is shown where the designation is picked and filled. | Decided | Designation |
- 2026-11-18: "expliquer ce que c'est"
  - In: | MD-13.6 | Description | Text field, takes the room left | What the designation is (2026-11-18: "expliquer ce que c'est"). Optional: assistant's reading. | Decided (field), Proposed (optional) | Identifiers (draft) |
- 2026-11-21: "Le booléen required, ce serait genre false"
  - In: | MD-13.8 | Required | Checkbox, narrow column, between ID and Description | Checked: every placed symbol must have the text of this designation (a control ID), whether or not its faceplate shows it; left empty, a warning, never a block. Unchecked: it may stay empty (a location). Product Owner, 2026…
- 2026-11-18: "et les supprimer"
  - In: | MD-13.7 | Delete a designation | Button (icon), then a warning | At the far right of the line, with no header (2026-11-18: "et les supprimer"; layout rules). Deleting one still used is allowed: the titles and paragraphs of the faceplate that show it are flagged in error (decision 0082). | Decided …
