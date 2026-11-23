# nav-rail-library

> [Home](../../README.md) › [Design system](../README.md) › [Molecules](README.md) › nav-rail-library

A Symbol Lib in the navigation bar of the symbol mode ([SY-00.3](../../screens/symbols.md#sy-00--navigation-bar-of-the-symbol-mode)): its initials in a square, and its hidden [tooltip](../06-atoms/tooltip.md) with its name. With `content=add`, the same square holds the icon `add`: the small + that creates a Symbol Lib ([SY-00.1](../../screens/symbols.md#sy-00--navigation-bar-of-the-symbol-mode)), square like the libraries under it (Product Owner, 2026-11-23). The look of a library is a proposal of the assistant, to confirm.

## Figma

| Node | Id |
| --- | --- |
| Component set | [`757:656`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=757-656) |

## Variants and states

`content`: `initials`, `add`. `state`: `default`, `hover`, `selected` (`initials` only), `tooltip`. The table of the variants is not exported yet.

## Inputs

| Input | Type | Default | Figma |
| --- | --- | --- | --- |
| `content` | `initials`, `add` | `initials` | variant `content` |
| `initials` | text, two letters | — | text property `initials`, `content=initials` only |
| `name` | text | — | the text of its tooltip, and its accessible name |
| `selected` | boolean | `false` | `state=selected` |

## Outputs

| Output | When | Value |
| --- | --- | --- |
| `click` | A click, or Enter or Space, on a library not selected. | — |

## Behaviour

- The item is as big as a [nav-rail-item](nav-rail-item.md) of the rail; the square inside is `size-control-md`, `radius-sm`, a `border-strong` line of `border-width`, the initials in the text style `caption`.
- `content=add`: the icon `add`, 20 px, centred in the square; its tooltip says "Create a Symbol Lib"; it is never selected.
- `hover`: the `layer-hover` background. `selected`: the `layer-selected` background and an `accent` line.
- After 0.8 s of hover, `tooltip`: the name of the library, on the right, as a nav-rail-item.

## Made of

| Component | Role |
| --- | --- |
| [tooltip](../06-atoms/tooltip.md) | The name of the library, after 0.8 s. |
