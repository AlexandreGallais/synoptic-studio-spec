# Point editing mode

> [Home](../../README.md) › [Symbols](../README.md) › Point editing mode · Previous: [Drawing mode](../04-drawing-mode/README.md) · Next: [Alignment mode](../06-alignment-mode/README.md)

Status: draft. Not validated.

The mode of the [editor](../03-editor/README.md) in which the points of a path are edited.

## Rules

### Tool bar

- [Select](../03-editor/select.md), [Hand](../03-editor/hand.md) and [Pen](../04-drawing-mode/pen.md).
- The Group, Rectangle, Ellipse, Polygon and Text tools disappear.

### Which points are shown

- Every shape has points that can be edited here: a [rectangle](../04-drawing-mode/rectangle.md) has 4, an [ellipse](../04-drawing-mode/ellipse.md) has 4, a [polygon](../04-drawing-mode/polygon.md) has one per side, a path drawn with the pen has its own.
- **On the canvas**, clicking a shape shows the points of that shape only, and of no other. The canvas stays readable.
- **In the right-hand panel**, a list shows all the points, shape by shape. A point is reached from the list without clicking its shape first, which spares the user from hunting for a small shape or a point hidden under another.
- Selecting a point in the list selects it on the canvas, and the other way round.

### Select

- Select picks points and handles, one or several, and moves them (several points can be selected as in the [editor](../03-editor/select.md): Shift or Ctrl, or a selection rectangle).
- Points can be added and removed.
- **Two points selected**: an option adds a new point in the middle of the two. It is offered in the right-hand panel, as a button (like every action, see the rule on visible equivalents in the [editor](../03-editor/README.md)).

### Right-hand panel

- The list of the points (above).
- The options of the selected point or handle (see [Points and handles](points-and-handles.md)).
- The actions on the selection: remove, add a point between two.

### Pen

- The Pen starts from an existing point to trace another one.
- This works on **any** shape: the user clicks the shape, its points appear, takes the Pen, clicks a point and draws a line from it. A rectangle can therefore be drawn over to become a free form.

### A shape that receives points becomes a free form

- When points are added to a rectangle, an ellipse or a polygon (with the Select tool or the Pen), the shape becomes a free form: a path.
- It **loses nothing** of what it had (fill, border, effects, position); it is only now a free form, whose points are all editable.
- The path now follows its points, not the options of the former shape.
- The same holds when a point is **removed**: a rectangle that loses a point becomes a triangle, as a free form. Moving the points of a rectangle also makes it a free form.

### The ellipse

- An ellipse is, at its base, only a shape with handles: its 4 points have handles and no corner radius mode (see [Points and handles](points-and-handles.md)).
- When a point is added to it or removed from it, it becomes a free form. Its points then gain the corner radius mode, like the points of any other path. It is not applied by itself: the points keep their handles, and the user switches a point to the corner radius mode when they want it.
- How the roundings are edited precisely (a point switched to the corner radius mode, its radius) is not detailed yet: to be settled later.

```mermaid
flowchart LR
    R["Rectangle, 4 points"] -->|"Pen: a point is added"| F["Free form, 5 points"]
    F --> K["Fill, border and effects kept"]
```

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, section 3.15).

- In a boolean group of Figma, each shape keeps its dimensions, position, rotation and corner radius. Opinion of the report: a free form keeps fill, border and effects; the options proper to the former shape (number of sides, box of the ellipse) leave the panel; the global corner radius becomes a radius per point.
- Points list: no source read. Opinion of the report: the points of the selected shapes; all the shapes, folded, when nothing is selected.
- Name: the report proposes **Path** instead of "free form" (the word of SVG).

## Open questions

- Options that belong to the former shape (the corner radius of a rectangle, the number of sides of a polygon, the box of an ellipse): once the shape is a free form, are they gone from the panel, or kept as shortcuts? Nothing is lost, but these options describe a shape that no longer has a fixed geometry.
- Precise editing of the roundings (corner radius mode of a point): to be detailed later.
- The list of the right-hand panel: all the points of all the shapes of the symbol, or only those of the selected shapes (all shapes when nothing is selected)? The spec above assumes all shapes, grouped by shape, to confirm.
