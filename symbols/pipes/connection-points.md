# Connection points

> [Home](../../README.md) › [Symbols](../README.md) › [Pipes](README.md) › Connection points

Status: draft. Not validated.

A connection point is a place of a symbol where a pipe can be attached.

## Rules

- A symbol has as many connection points as it has pipe connections. A two-way valve has 2, a three-way valve has 3. A symbol with none cannot be connected.
- The user places them in the symbol editor, on the drawing, while creating the symbol.
- Each point has a **position**, and nothing else to set about the flow.
- **No direction, no inlet or outlet**: a point is as much an inlet as an outlet (Product Owner, 2026-11-25: "un point peut être autant entrant que sortant [...] la direction, pour moi, sert à rien").
- The direction of a flow is given by the **signals**, not by the points: the model sends a positive or a negative value, and the animation runs one way or the other (Product Owner, 2026-11-25; see the [catalogue of the animations](../08-animation-mode/animation-catalogue.md)).
- A connection point is not a shape: it is not drawn in the exported SVG of the symbol and it has no fill or border.
- In a synoptic, a pipe snaps to the connection points of the symbols and follows them when a symbol is moved.

## Where it is made in the editor

- The **Connection** mode of the modes menu (Product Owner, 2026-11-23), with the Select, Hand and Connection point tools.
- The **Connection point** tool works like the [pen](../04-drawing-mode/pen.md), but draws no line: **each click puts a point**, and nothing else (Product Owner, 2026-11-25: "tu peux pas faire de traits, tu peux que faire des points").
- Right-hand panel: the list of the points (no bin: the Delete key, or the − of the title of the list, as in the [point editing mode](../05-point-editing-mode/README.md#list-of-the-points)), then the name and the X and Y of the selected point (assistant's proposal).

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, sections 3.1, 3.3, 3.7, 3.15, 3.17).

- A connection point carries a **position and a direction** in Visio (inward, outward, both) and in libavoid (the visible sides of a "pin"). Confidence: high. Set aside by the Product Owner on 2026-11-25: a point has no direction here.
- A link can be **fixed** to a point or **floating** around the shape (draw.io). In draw.io a fixed link follows its symbol; in Ignition a pipe does not follow a moved component. The project wants the pipe to follow: the convention of diagram software.
- In libavoid, the connection points follow a rotation by quarter turns and a mirror of the shape.
- The inline symbols of the archived Figma page (valves, reducers, flow arrows) have two connection points. Opinion of the report: **a symbol without animation can have connection points** (a tank outline, an arrow), with names and search, no categories. Since 2026-11-15 every symbol is of the same kind, with or without a type: any symbol can have connection points.
- Name: keep **Connection point**; "anchor" is already the word for the nine anchors of a box.

## Open questions

- Whether a point carries a name (port A, port B), and whether the name is linked to Metadata (for example a signal "flow through port A").
- The size of the zone where a pipe snaps.
- What happens to a pipe when a symbol changes its connection points. Rotation by quarter turns and mirror in a synoptic: the points follow (opinion of the report), to confirm in part 3.
