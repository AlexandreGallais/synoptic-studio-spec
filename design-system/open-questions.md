# Open questions

> [Home](../README.md) › [Design system](README.md) › Open questions

What is left to decide on the design system. A question answered leaves this file; its answer goes where the concept is written.

## Foundations

- The colour values taken from Warm Sand, and the two new ones (`text-placeholder`, `text-inverse`): to review on screen.
- The sizes proposed (controls 32 px, text 14 px, rows 36 px): to review on screen, now with IBM Plex Sans.
- The sizes of the headings of a description, Heading 1 to 6: 28, 24, 20, 18, 17, 16 (proposed, 2026-11-23).

## Components

- How the selected part of a type is marked in its list ([MD-01](../screens/metadata.md#md-01--types-the-tree-and-the-type-editor)).
- The window buttons on macOS and in a browser ([Top bar](../screens/README.md#top-bar-of-the-window)); the macOS buttons are drawn with `danger`, `warning` and `success` for now.
- How a line is moved without dragging (with the keyboard, or by single clicks): WCAG 2.2 asks for a way without dragging (criterion 2.5.7); the specs only give the drag of the `drag-handle`.
- The `toggle` off, in `hover` and `pressed`: its track turns almost black, much darker than at rest; seen in its table on 2026-11-22, to review on screen.
- The control that chooses Global or Template on an enum: drawn as a `segmented-control` (proposed).
- The highest size of a list that opens, 280 px: to review on screen.
- A field placed `filled` has no hover of its own: add a state `filled` with a hover?
- The thumb of the scrollbar of `menu-grouped` is 24 high in the component, where the component `scrollbar` draws it 56: Figma refuses to change it in the instance. Does 24 suit?
- Other components may keep a raw colour under their variable, as `colour-swatch` did: to review them all?
