# Drawing mode

> [Home](../../README.md) › [Symbols](../README.md) › Drawing mode · Previous: [Editor](../03-editor/README.md) · Next: [Point editing mode](../05-point-editing-mode/README.md)

Status: draft. Not validated.

The default mode of the [editor](../03-editor/README.md): draw and arrange shapes.

## Rules

- Tool bar: [Select](../03-editor/select.md), [Hand](../03-editor/hand.md), then in this order: [Group](group.md), [Rectangle](rectangle.md), [Ellipse](ellipse.md), [Polygon](polygon.md), [Pen](pen.md), [Text](text.md). The order: groups, then the basic shapes, then the pen, then the text.
- The Group, Rectangle, Ellipse, Polygon, Pen and Text tools exist only in this mode (the Pen is also in the point editing mode).
- Right-hand panel: the options of the selected shape (colours, corner radius, effects...).
- Everything drawn becomes a path, except a text, which stays a text.
- Every shortcut has a visible equivalent (see the [editor](../03-editor/README.md)).

## Tools of this mode

| Tool | What it does |
| --- | --- |
| [Group](group.md) | Creates a group (an SVG `g`), fit to its content or with its own size, with a layout of its children. |
| [Rectangle](rectangle.md) | Draws a rectangle, with a corner radius. 4 points. |
| [Ellipse](ellipse.md) | Draws an oval or a circle. 4 points, no corner radius. |
| [Polygon](polygon.md) | Draws a polygon of 3 to 20 sides, with anchors. One point per side. |
| [Pen](pen.md) | Draws a path point by point, and lines. Two buttons: straight line, angle lock. |
| [Text](text.md) | Writes a text, written or linked to a signal or to its unit. |

## What shapes have in common

The rectangle, the ellipse, the polygon and the path share the same pages; the geometry is also the group's and the text's.

| Page | What it holds |
| --- | --- |
| [Geometry](geometry.md) | Size, position, rotation, placement in a group, and the order of the right-hand panel. Every element has them. |
| [Fill and border](fill-and-border.md) | Fills stacked (colour or gradient), border (not an SVG stroke) outside, in the middle or inside, size, dashes. A group has neither. |
| [Effects](effects-and-masks.md) | The section "Effects", its lines and editing modes; the catalogue of every effect SVG and CSS allow, and the seven entries kept for this version (2026-11-25). |
| [Clip, mask, fade](effects-clip-and-mask.md) | The clip, with its editing; mask and fade set aside. |
| [Opacity and blend](effects-opacity-and-blend.md) | The opacity of the whole object; blend mode and background blur set aside. |
| [Shadows and light](effects-shadows-and-light.md) | Set aside: drop shadow, outer glow, inner shadow, inner glow, lighting. |
| [Blur and sharpness](effects-blur-and-sharpness.md) | Set aside: blur; sharpen, edges, emboss. |
| [Colour](effects-colour.md) | Set aside: colour adjustments, colour overlay, colour map. |
| [Texture and distortion](effects-texture-and-distortion.md) | Set aside: thicken or thin, noise, distortion. |
| [Filter chain](effects-filter-chain.md) | Set aside: a filter built step by step. |
| [Paints](paints.md) | Linear and radial gradients edited on the drawing; conic gradient, pattern, image set aside. |
| [Lines and text](effects-lines-and-text.md) | The border that keeps its width; arrow heads, crisp edges, text along a path set aside. |
| [Points and handles](../05-point-editing-mode/points-and-handles.md) | In the point editing mode: corner radius or handles per point, mirroring, angle and length. |
