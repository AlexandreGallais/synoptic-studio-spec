# icon-picker

> [Home](../../../README.md) › [Design system](../../README.md) › [Organisms](../README.md) › icon-picker

The icons a type can take: [icon-button](../../atoms/icon-button/README.md) for each icon of the icon set, and a reset to the icon of the parent.

## Figma

| Node | Id |
| --- | --- |
| Component | [`641:1489`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=641-1489) |

## Variants and states

![Table of icon-picker](table.svg)

## Inputs

| Input | Type | Default | Figma |
| --- | --- | --- | --- |
| `icons` | the icons of the set | — | its icon buttons |
| `value` | the chosen icon, or the parent's | the parent's | the icon button in `state=selected` |

## Outputs

| Output | When | Value |
| --- | --- | --- |
| `valueChange` | An icon is chosen. | the icon |
| `reset` | The reset button: follow the parent again. | — |

## Behaviour

- The icons of the types are files of Metadata ([Icon](../../../metadata/entities/03-icon.md)), not the icons of the interface.

## Made of

| Component | Role |
| --- | --- |
| [icon-button](../../atoms/icon-button/README.md) | Each icon, and reset. |
