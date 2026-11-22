# Skill rules

> [Home](../README.md) › [Design system](README.md) › Skill rules

What the Product Owner adds to the design-system skills of the assistant, or changes in them, for Synoptic Studio. Started on 2026-11-22. Once the round of Metadata is done, these rules go back into the skills themselves.

## How this file works

- The assistant follows its design-system skills.
- When a request of the Product Owner contradicts a skill, the assistant says so before acting: what the skill says, what is asked, its advice.
- If the Product Owner keeps the request, it wins over the skill, and it is written here.
- A rule the Product Owner adds that no skill holds is written here too.

Each rule: what it says, the skill it adds to or contradicts, its status.

| Status | Meaning |
| --- | --- |
| Added | No skill says it; it adds to them. |
| Kept over the skill | It contradicts a skill; the Product Owner kept it. |
| Asked | It contradicts a skill; the Product Owner has not answered the challenge yet. |

## Rules

### R1 · The pages of the library

- **Rule**: the Figma file has the pages Foundations, Icons, Atoms, Molecules, Organisms, Templates, then Metadata, the screens of Metadata, in the library file itself (Product Owner, 2026-11-22).
- **Skill**: `name-and-organise-components-layers-and-pages` asks for the pages Foundations, Atoms, Molecules, Organisms, Templates, and puts screens in **product files**, one page per flow, outside the library.
- **Differences**: a page Icons (adds to the skill); the screens of Metadata in the library file, not in a product file.
- **Status**: Kept over the skill.

### R2 · One theme, on Neutral Fog

- **Rule**: one theme, built on the colours of the old Neutral Fog theme, not on Neutral Graphite; only the colours needed are kept (Product Owner, 2026-11-22).
- **Skill**: `layer-tokens-primitive-semantic-component` puts the themes as modes of the semantic collection: one mode `fog` here.
- **Status**: Added.

### R3 · Dense, but larger than Figma

- **Rule**: dense screens, with every control larger than Figma's, for people from 20 to 77 (Product Owner, 2026-11-22). Controls 32 px high, text 14 px (proposed in [Foundations](02-foundations.md#sizes)).
- **Skill**: `check-accessibility-in-the-design` asks for targets of at least 24 × 24 px: the rule asks for more.
- **Status**: Added.

### R4 · Screens in 16:9, at least 1600 × 900

- **Rule**: every screen in 16:9; the smallest window is 1600 × 900, and nothing is promised below it, under the exemption of WCAG for two-dimensional layouts (Product Owner, 2026-11-22).
- **Skill**: `check-accessibility-in-the-design` asks that every screen works at **320 px wide** without horizontal scrolling (WCAG 2.2, criterion 1.4.10 Reflow). WCAG exempts what needs a two-dimensional layout, such as an editor or a data table.
- **Status**: Kept over the skill.

### R5 · Every component with its states

- **Rule**: every component drawn whole, with its variants and its states; never an empty or hollow component (Product Owner, 2026-11-22).
- **Skill**: the same as `build-a-new-component-bottom-up` and `document-every-component-and-its-states`.
- **Status**: Added (confirms the skills).

### R6 · No Carbon

- **Rule**: the design system is made from zero; it does not follow IBM Carbon.
- **Skill**: `lay-out-templates-on-the-carbon-2x-grid` and `theme-with-carbon-tokens-as-modes` hold only for a design system built on Carbon, as they say themselves; `check-accessibility-in-the-design` cites Carbon's focus token, read here as the token `focus` of [Foundations](02-foundations.md#colours).
- **Status**: Added.
