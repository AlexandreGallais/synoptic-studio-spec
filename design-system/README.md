# design-system

> [Home](../README.md) › Design system

Status: first draft, drawn in Figma (foundations, icons, atoms, molecules, organisms, prototyped, each shown as a table of its variants and states; the template of the screens; the screens of Metadata with their content states and their prototype). The icons are validated; the rest is not. The values marked "proposed" are to review on screen, in Figma.

What the design system of Synoptic Studio is made of, and how it is drawn in the Figma file (https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL). The design system is reusable outside Synoptic Studio; its code is the library of the repository `synoptic-studio-design-system`.

## What it contains

Files and folders are numbered in reading order.

| File or folder | What it holds |
| --- | --- |
| [01 · Principles](01-principles.md) | Who it is for, how dense and how large, the one theme, the size of the screens. |
| [02 · Foundations](02-foundations.md) | The tokens: colours, typography, spacing, sizes, radii, borders, shadows. |
| [03 · Components](03-components.md) | The levels, what a sheet holds, and the rules every component follows. |
| [04 · Figma file](04-figma-file.md) | The pages, variables and styles of the Figma file, how a page shows its components, the exports, and the ways of Figma to keep in mind. |
| [05 · Icons](05-icons/README.md) | The icons of the interface, each exported as SVG. |
| [06 · Atoms](06-atoms/README.md) | One sheet per atom; the tables of their variants and states in its folder `images`. |
| [07 · Molecules](07-molecules/README.md) | One sheet per molecule, tables in its folder `images`. |
| [08 · Organisms](08-organisms/README.md) | One sheet per organism, tables in its folder `images`. |
| [09 · Templates](09-templates/README.md) | The layout of the screens. |
| [10 · Screens](10-screens/README.md) | One folder per part of the application, its screens as drawn, with their ids: [Metadata](10-screens/01-metadata/README.md) for now. |
| [Skill rules](skill-rules.md) | What this design system adds to, or changes in, the design-system skills of the assistant. |
| [Open questions](open-questions.md) | What is left to decide. |

Only the components the screens of Metadata use have a sheet for now.

## The pages of the Figma file

The pages of the old design system stay as they are, for inspiration only; nothing is copied from them.

```mermaid
flowchart LR
    F["Foundations"] --> I["Icons"] --> A["Atoms"] --> M["Molecules"] --> O["Organisms"] --> T["Templates"] --> MD["Metadata: the screens of Metadata"]
    %% link I 05-icons/README.md
    %% link A 06-atoms/README.md
    %% link M 07-molecules/README.md
    %% link O 08-organisms/README.md
    %% link T 09-templates/README.md
    %% link MD 10-screens/01-metadata/README.md
```

| Page | What it holds |
| --- | --- |
| Foundations | The variables and the styles of [Foundations](02-foundations.md), shown with their names. |
| Icons | One component per icon of [Icons](05-icons/README.md). |
| Atoms | The atoms, each with its variants and its states. |
| Molecules | The molecules, made of atoms only. |
| Organisms | The organisms, made of molecules and atoms. |
| Templates | The layout of the screens without their content: window, top bar, left column, main area, drawn once at 1600 × 900 and reused by every screen. |
| Metadata | The screens of Metadata (`MD-00` to `MD-13` of [Screens of Metadata](../screens/metadata.md)), made of instances of the templates and components only, each with its content states. |

The screens of Metadata stay in the library file, not in a product file of their own: see [Skill rules R1](skill-rules.md#r1--the-pages-of-the-library).

## Where it is used

| Where | What it uses |
| --- | --- |
| [Screens](../screens/README.md) | Every control of every screen is a component of this design system. |
| [Controls](../controls/README.md) | The shared number and text fields are the components `number-input` and `text-input`. |
| Repository `synoptic-studio-design-system` | The same components and tokens, in code, with the same names, inputs and outputs; the icons from the SVG files of [Icons](05-icons/README.md). |
