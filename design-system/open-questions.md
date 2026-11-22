# Open questions

> [Home](../README.md) › [Design system](README.md) › Open questions

What is left to decide on the design system. A question answered leaves this file; its answer goes where the concept is written.

## Foundations

- The colour values taken from Warm Sand, and the two new ones (`text-placeholder`, `text-inverse`): to review on screen.
- The sizes proposed (controls 32 px, text 14 px, rows 36 px): to review on screen, now with IBM Plex Sans.

## Components

- How the selected part of a type is marked in its list ([MD-01](../screens/metadata.md#md-01--types-the-tree-and-the-type-editor)).
- How Global and Template are told apart on an enum ([MD-09.10](../screens/metadata.md#md-09--enums)).
- The look of an inherited line (greyed, with the name of its parent: [MD-04.3](../screens/metadata.md#md-04--signals)).
- The window buttons on macOS and in a browser ([Top bar](../screens/README.md#top-bar-of-the-window)); the macOS buttons are drawn with `danger`, `warning` and `success` for now.
- How a line is moved without dragging (with the keyboard, or by single clicks): WCAG 2.2 asks for a way without dragging (criterion 2.5.7); the specs only give the drag of the `drag-handle`.
- The mark of the selected part in the top bar: the nav-rail-item puts its accent bar on the left, as in the rail; at the bottom may read better in a horizontal bar.
