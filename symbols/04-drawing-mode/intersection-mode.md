# Intersection mode

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing mode](README.md) › Intersection mode

Status: draft. Asked by the Product Owner on 2026-11-25. Not validated.

The mode of the [editor](../03-editor/README.md) in which the user builds a **new shape** from several shapes and from their intersections. Example: the outlet of a pump cut along the outline of its casing.

## Rules

- **A mode of the modes menu**, right after [Clip](clip-mode.md) (Product Owner, 2026-11-25: "un nouveau mode après le mode clip"). It goes in the group of Clip, with no separator between the two (assistant's choice; see [Modes](../03-editor/README.md#modes)).
- **Tools**: [Hand](../03-editor/hand.md) and **Shape builder**, active when the mode opens. No Select: the shapes are chosen in the layers (assistant's proposal). "Shape builder" is the name of the same tool in Figma and Illustrator; a working name.
- **Choosing the shapes**: in the [layers](../03-editor/layers.md), on the left, as many shapes as wanted (Shift or Ctrl and a click add one). On the drawing, the chosen shapes are put forward; the rest of the symbol is translucent (Product Owner, 2026-11-25).
- **The regions**: the chosen shapes cut each other into regions: the part of each shape that no other covers, and each intersection.
- **Selecting regions with the Shape builder**: a click on a region selects it; a click on it again unselects it, as many times as wanted (Product Owner, 2026-11-26: "quand tu cliques sur une intersection, ça l'ajoute, et quand tu recliques dessus, ça l'enlève, et comme ça à l'infini"). A selected region is filled; the others show only their outline. The region under the mouse is highlighted (assistant's proposal).
- **No list of the regions** in the panel (Product Owner, 2026-11-26: "région casing alone, outlet alone [...] ça, non, ça, je veux pas"): the regions are chosen on the drawing only.
- **Right-hand panel**: the title "Intersection", the chosen shapes, then the line **"Create a shape from the selection"** with a small **+** on its right, enabled as soon as one region is selected, at any moment (Product Owner, 2026-11-26: "tu fais un petit +, la forme, elle se crée, puis point barre"). No Validate nor Cancel: leaving the mode creates nothing.
- **One shape, never several**: the + creates **one** shape from all the selected regions, even when they do not touch each other (Product Owner, 2026-11-26: "ça en crée pas plusieurs, ça en crée une qui est un peu bizarre, et puis basta"). No option to create one shape per region: the user selects and clicks + again for each shape wanted (Product Owner, 2026-11-26: "au pire, le gars, il fait ça plusieurs fois [...] pas d'option, une seule forme, et puis basta").
- **After the +**: the new shape is in the layers, the selection of regions is emptied, the mode stays open (assistant's proposal).
- **The new shape** is a path (a free form, see [Point editing mode](../05-point-editing-mode/README.md)), put in the layers above the highest chosen shape, with the look of the first chosen shape (assistant's proposal, as the research advised for boolean operations).
- **The chosen shapes stay** as they were: the mode adds a shape, it destroys none (assistant's reading, to confirm).

```mermaid
flowchart LR
    S["Shapes chosen in the layers"] --> R["Regions: each shape alone, each intersection"]
    R -->|"Shape builder: a click selects, a click again unselects"| K["Selected regions"]
    K -->|"the + of the panel"| N["One new shape, a path"]
```

### What it does compared with the boolean operations

The four boolean operations of the [advanced tools](../03-editor/expert-menu/boolean-operations.md), set aside in this version, are particular choices of regions:

| Operation | Regions selected, for two shapes A and B |
| --- | --- |
| Union | A alone, B alone, A and B |
| Intersect | A and B |
| Subtract | A alone |
| Exclude | A alone, B alone |

### Computing

Cutting shapes into regions is a computation of intersections: it belongs to the geometry engine (`synoptic-studio-geometry`), measured by the research before development (criteria C7 and C16 of the project).

## Where it is used

| Screen | Element |
| --- | --- |
| [SY-03](../../screens/symbols.md#sy-03--symbol-editor-what-every-mode-shares) | SY-03.1, the modes menu |
| [SY-14](../../screens/symbols.md#sy-14--intersection-mode) | The Intersection mode |
| [Figma](../../design-system/04-figma-file.md#mode-screens) | The id of its screen |

## Open questions

- The name "Intersection": the mode also makes unions and differences.
- The chosen shapes kept (proposal), or replaced by the new shape?
- The look of the new shape: that of the first chosen shape (proposal)?
- Its place in the menu: in the group of Clip (proposal), or a group of its own?
- Can a group, a text or an open path be chosen?
- The name "Shape builder", and no Select in this mode (proposal)?
