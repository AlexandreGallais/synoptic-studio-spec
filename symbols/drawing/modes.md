# Modes

> [Home](../../README.md) › [Symbols](../README.md) › [Drawing](../02-drawing.md) › Modes

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

A mode is a way of working on the drawing. Each mode has its own tool bar and its own right-hand panel.

| Mode | What it is for | Tools in the tool bar | Right-hand panel |
| --- | --- | --- | --- |
| Drawing | The default mode: draw and arrange shapes. | Select, Hand, Rectangle, Ellipse, Polygon, Text, Pen | Options of the selected shape (colours, corner radius...) |
| [Point editing](mode-point-editing.md) | Edit the points of a path. | Select, Hand, Pen | Options of the selected point |
| [Alignment](mode-alignment.md) | Place shapes in relation to each other. | Select, Hand | Alignment of the selected shapes |
| Interaction | Draw the zones that react to a gesture, and link them to commands (see [Interactions](../05-interactions.md)). | Select, Hand, Interaction zone | The interactions of the selected place |
| Animation | Link the signals to the parts of the drawing (see [Animation](../04-animation.md)). | Select, Hand | The animations of the selected part |
| Run | Try the symbol with test values and see it at the size of another screen (see [Testing](../06-testing.md)). | Hand | The test values, and the simulated screen |

## Rules

- The Rectangle, Ellipse, Polygon and Text tools exist only in the drawing mode.
- The Interaction, Animation and Run modes are only for a dynamic symbol: a static symbol has no interaction, no animation and nothing to test with signals.
- The [Expert menu](expert-menu.md) can add a second tool bar on top of the current mode.
- Other modes may be added later.
