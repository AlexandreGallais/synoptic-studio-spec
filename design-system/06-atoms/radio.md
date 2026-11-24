# radio

> [Home](../../README.md) › [Design system](../README.md) › [Atoms](README.md) › radio

A round button to pick one option of a small exclusive set. Never alone: always in a [radio-group](../07-molecules/radio-group.md).

## Figma

| Node | Id |
| --- | --- |
| Component set | [`633:170`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=633-170) |

## Variants and states

![Table of the variants and states of radio](images/table-radio.svg)

## Inputs

| Input | Type | Default | Figma |
| --- | --- | --- | --- |
| `checked` | boolean | `false` | variant `checked` |
| `disabled` | boolean | `false` | `state=disabled` |
| `readOnly` | boolean | `false` | `state=read-only` |

## Outputs

| Output | When | Value |
| --- | --- | --- |
| `select` | A click, or Space while it has the focus, on a radio not checked. | — |

## Behaviour

- A checked radio is not unchecked by a click: another radio of its group is chosen instead.
- `read-only`: the look of every read-only control ([Components](../03-components.md#rules-for-every-component)): a ring `border-subtle`, a dot `icon-primary`.
