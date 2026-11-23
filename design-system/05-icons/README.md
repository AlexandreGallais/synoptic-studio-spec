# Icons

> [Home](../../README.md) › [Design system](../README.md) › Icons

The icons of the interface, each exported from Figma as an SVG beside this file: the code reuses these files. Status: validated.

Figma: page Icons (`630:104`), one component `icon/<name>` each, section Icons (`656:7343`).

## Rules

- One component per icon, named `icon/<name>`, drawn on a 16 px grid and scaled to 20 px without a second drawing.
- Drawn in lines in Figma: a stroke of 1.5 px, round ends and round corners, no fill; the drawing stays inside the 16 px square, its line included, and two lines never touch where they should not.
- The SVG files have no stroke: every line is turned into a filled outline, joined into one shape, filled with `currentColor` so that the code gives the colour. Figma keeps the lines.
- An icon "-add" is its icon, smaller, in the top left, with a + in the bottom right, both inside the 16 px square.
- An icon takes its colour from a token (`icon-primary`, `icon-secondary`, `accent`, `danger`), never a fixed colour.
- An icon alone on a button always has an accessible name and a [tooltip](../06-atoms/tooltip.md).
- The icons of the interface are not the icons of the types: those are files of Metadata ([Icon](../../metadata/entities/03-icon.md)).

## Parts and window

| Icon | Name | Meaning | Figma |
| --- | --- | --- | --- |
| ![app-mark](app-mark.svg) | `app-mark` | The logo, a valve: two triangles meeting at their tips, without the stem on top. | [`631:8`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-8) |
| ![metadata](metadata.svg) | `metadata` | The Metadata part. | [`631:14`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-14) |
| ![symbols](symbols.svg) | `symbols` | The Symbols part. | [`631:19`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-19) |
| ![synoptic](synoptic.svg) | `synoptic` | The Synoptic part. | [`631:24`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-24) |
| ![minimise](minimise.svg) | `minimise` | Minimise the window. | [`631:27`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-27) |
| ![maximise](maximise.svg) | `maximise` | Maximise the window. | [`631:30`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-30) |
| ![close](close.svg) | `close` | Close the window. | [`631:38`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-38) |

## Pages of Metadata

| Icon | Name | Meaning | Figma |
| --- | --- | --- | --- |
| ![types](types.svg) | `types` | Page Types. | [`631:45`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-45) |
| ![units](units.svg) | `units` | Page Units. | [`631:51`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-51) |
| ![enums](enums.svg) | `enums` | Page Enums. | [`631:57`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-57) |
| ![designations](designations.svg) | `designations` | Page Designations. | [`631:61`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-61) |

## Actions

| Icon | Name | Meaning | Figma |
| --- | --- | --- | --- |
| ![add](add.svg) | `add` | The small + of a title, the + on hover of a type. | [`631:65`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-65) |
| ![search](search.svg) | `search` | Search in the type tree. | [`631:69`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-69) |
| ![dismiss](dismiss.svg) | `dismiss` | Close the search, close a dialog. | [`631:73`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-73) |
| ![chevron-right](chevron-right.svg) | `chevron-right` | A folded branch of a tree. | [`631:76`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-76) |
| ![chevron-down](chevron-down.svg) | `chevron-down` | An unfolded branch; a select. | [`631:79`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-79) |
| ![expand-all](expand-all.svg) | `expand-all` | Open every branch of the type tree: two chevrons pointing apart. | [`699:13751`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=699-13751) |
| ![collapse-all](collapse-all.svg) | `collapse-all` | Close every branch: two chevrons pointing together. | [`699:13755`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=699-13755) |
| ![duplicate](duplicate.svg) | `duplicate` | Duplicate a preset of a parent into the type: two squares, one over the other. | [`748:2060`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=748-2060) |
| ![delete](delete.svg) | `delete` | Delete a line, a type. | [`631:86`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-86) |
| ![drag-handle](drag-handle.svg) | `drag-handle` | The handle of a line. | [`631:94`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-94) |
| ![reset](reset.svg) | `reset` | Follow the parent's icon or colour again. | [`631:98`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-98) |
| ![folder](folder.svg) | `folder` | A path link. | [`631:101`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-101) |
| ![icon of a URL link](link.svg) | `link` | A URL link. | [`631:105`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-105) |
| ![folder-add](folder-add.svg) | `folder-add` | Add a path. | [`673:13125`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=673-13125) |
| ![link-add](link-add.svg) | `link-add` | Add a URL. | [`673:13131`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=673-13131) |
| ![full-page](full-page.svg) | `full-page` | The description on the whole editing part. | [`631:111`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-111) |

## Formatting

| Icon | Name | Meaning | Figma |
| --- | --- | --- | --- |
| ![bold](bold.svg) | `bold` | Bold. | [`631:121`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-121) |
| ![italic](italic.svg) | `italic` | Italic. | [`631:126`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-126) |
| ![list-bulleted](list-bulleted.svg) | `list-bulleted` | A bulleted list. | [`631:139`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-139) |
| ![list-numbered](list-numbered.svg) | `list-numbered` | A numbered list. | [`631:146`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-146) |
| ![table](table.svg) | `table` | Insert a table. | [`631:152`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-152) |
| ![code](code.svg) | `code` | Code. | [`631:157`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-157) |
| ![quote](quote.svg) | `quote` | A quote. | [`631:163`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-163) |

## Signals and faceplate

| Icon | Name | Meaning | Figma |
| --- | --- | --- | --- |
| ![signal-input](signal-input.svg) | `signal-input` | A signal in input. | [`631:168`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-168) |
| ![signal-output](signal-output.svg) | `signal-output` | A signal in output. | [`631:173`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-173) |
| ![quantity](quantity.svg) | `quantity` | A quantity. | [`631:178`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-178) |
| ![difference](difference.svg) | `difference` | A difference. | [`631:181`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-181) |
| ![command](command.svg) | `command` | A command element. | [`631:184`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-184) |
| ![title](title.svg) | `title` | A title element. | [`631:188`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-188) |
| ![description](description.svg) | `description` | A description element: a pilcrow, named after the word of the screens, not the kind `paragraph` of the data model. | [`631:193`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-193) |
| ![group](group.svg) | `group` | A group element. | [`631:198`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-198) |
| ![signal-add](signal-add.svg) | `signal-add` | Add a signal element. | [`680:12952`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=680-12952) |
| ![command-add](command-add.svg) | `command-add` | Add a command element. | [`680:12964`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=680-12964) |
| ![title-add](title-add.svg) | `title-add` | Add a title element. | [`680:12974`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=680-12974) |
| ![description-add](description-add.svg) | `description-add` | Add a description element. | [`680:12985`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=680-12985) |
| ![group-add](group-add.svg) | `group-add` | Add a group. | [`680:12997`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=680-12997) |
| ![variable](variable.svg) | `variable` | Take a value from a signal or a designation, as Figma's "Apply variable". | [`631:202`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-202) |

## Status

| Icon | Name | Meaning | Figma |
| --- | --- | --- | --- |
| ![warning](warning.svg) | `warning` | A warning dialog, a warning in a line. The triangle is 12 high and its dot keeps the same gap to the bottom as in `error`. | [`631:207`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-207) |
| ![error](error.svg) | `error` | A line in error. | [`631:212`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-212) |
| ![check](check.svg) | `check` | A ticked checkbox, the chosen item of a menu. | [`631:215`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=631-215) |

## Left out

Drawn in Figma but on no screen of Metadata, so not exported for now: `restore`, `exit-full-page`, `heading`.

## Drawn for Symbols, not exported yet

The first screens of the symbol mode use three new icons, drawn with the same rules; their SVG files come with the export of the Symbols screens.

| Name | Meaning | Figma |
| --- | --- | --- |
| `libraries` | The Libraries button: books on a shelf, the last one leaning. | [`757:9`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=757-9) |
| `pipes` | The page Pipes of a Symbol Lib: a pipe with an elbow. | [`757:17`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=757-17) |
| `chevron-up` | The arrow back to the previous part of a list of the rail. | [`757:3`](https://www.figma.com/design/2hW8t5CgVru1VFbQZ1yETL/?node-id=757-3) |

The page Enums of a Symbol Lib reuses `enums`, the page Symbols reuses `symbols`, the arrow to the next part reuses `chevron-down`.
