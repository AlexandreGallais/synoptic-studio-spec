# Data model

> [Home](../README.md) › [Synoptics](README.md) › Data model · Previous: [Outputs](10-outputs.md) · Next: [Open questions](12-open-questions.md)

Status: a first sketch by the assistant. Three of its choices are settled (references, instance ID, changes from the preset, see the reading notes); the rest is not validated. Written with the conventions of the [data model of Metadata](../metadata/data-model.md), which it points to and never changes.

## Conventions

The same as in Metadata:

- `internal_id`: the UUID set by the software, version 7 (see [Rules of the schema](../metadata/data-model-notes.md#rules-of-the-schema)); every FK holds one.
- A box without `internal_id` is a part of its owner (a nested object in the JSON), never pointed to.
- `has`: one nested object; `holds`: an ordered list inside its owner.
- Every other link is a FK, labelled by the field that holds it.
- A field or a link that only exists in some cases says when: `when ...`.
- A choice of the software is an English word in the JSON (`"installation"`, `"view"`), never a number.
- A number typed for a signal is kept in the default unit of its quantity (decision 0051).

Boxes of Metadata and of the Symbol Lib (`TYPE`, `PRESET`, `SIGNAL`, `FLAG`, `DESIGNATION`, `FACEPLATE_ELEMENT`, `SYMBOL`, `CONNECTION_POINT`, `PIPE_STYLE`) are only pointed to by a FK field (`symbol`, `preset`, `flag`...); they are not drawn here.

## The schema

```mermaid
erDiagram
    SYNOPTIC {
        uuid internal_id PK
        synoptic_kind kind "installation or view"
        text name
        boolean home
        text description
    }
    FRAME {
        integer width
        integer height
        rgb background
        integer grid_step
    }
    SYMBOL_LIB_USE {
        uuid symbol_lib FK
    }
    FOLDER {
        uuid internal_id PK
        text name
    }
    PLACED_SYMBOL {
        uuid internal_id PK
        uuid symbol FK
        uuid reference FK "when it shows a placed symbol of an installation"
        uuid folder FK
        real x
        real y
        quarter_turn rotation "0, 90, 180 or 270"
        boolean mirror_x
        boolean mirror_y
        real scale
        boolean locked
        boolean hidden
    }
    IDENTITY {
        uuid preset FK
        text instance_id
    }
    DESIGNATION_TEXT {
        uuid designation FK
        text text
    }
    FLAG_ON {
        uuid flag FK
    }
    VALUE_CHANGE {
        uuid signal FK
        signal_value start_value "in the default unit"
        uuid unit FK
        integer decimals
    }
    TEXT_CHANGE {
        uuid faceplate_element FK
        text text
    }
    TEMPLATE_ITEMS {
        uuid signal FK
    }
    TEMPLATE_ITEM {
        uuid internal_id PK
        integer key
        text display_name
        text description
    }
    ON_PIPE {
        uuid branch FK
        real distance
    }
    PIPE {
        uuid internal_id PK
        uuid pipe_style FK
        text name
    }
    PIPE_BRANCH {
        uuid internal_id PK
        uuid parent FK "the branch it leaves; empty for the trunk"
        real at "distance along the parent where it leaves"
    }
    PIPE_POINT {
        real x
        real y
    }
    PIPE_END {
        pipe_end_kind kind "symbol or free"
        uuid placed_symbol FK "when kind is symbol"
        uuid connection_point FK "when kind is symbol"
    }
    CROSSING_SWAP {
        uuid over FK
        uuid under FK
    }
    ANNOTATION {
        uuid internal_id PK
        annotation_kind kind "text, area, shape, legend or value label"
    }
    LINK {
        uuid internal_id PK
        uuid target FK
        uuid target_symbol FK "when it opens on a placed symbol"
    }
    SCENARIO {
        uuid internal_id PK
        text name
    }
    SYNOPTIC ||--|| FRAME : "has"
    SYNOPTIC ||--|{ SYMBOL_LIB_USE : "holds"
    SYNOPTIC ||--o{ FOLDER : "holds"
    SYNOPTIC ||--o{ PLACED_SYMBOL : "holds"
    SYNOPTIC ||--o{ PIPE : "holds"
    SYNOPTIC ||--o{ ANNOTATION : "holds"
    SYNOPTIC ||--o{ LINK : "holds"
    SYNOPTIC ||--o{ CROSSING_SWAP : "holds"
    SYNOPTIC ||--o{ SCENARIO : "holds"
    PLACED_SYMBOL }o--o| PLACED_SYMBOL : "reference"
    PLACED_SYMBOL ||--o| IDENTITY : "has, when it is no reference"
    PLACED_SYMBOL ||--o| ON_PIPE : "has, when connected to a pipe"
    IDENTITY ||--o{ DESIGNATION_TEXT : "holds"
    IDENTITY ||--o{ FLAG_ON : "holds"
    IDENTITY ||--o{ VALUE_CHANGE : "holds"
    IDENTITY ||--o{ TEXT_CHANGE : "holds"
    IDENTITY ||--o{ TEMPLATE_ITEMS : "holds, one per signal pointing to a template"
    TEMPLATE_ITEMS ||--o{ TEMPLATE_ITEM : "holds"
    ON_PIPE }o--|| PIPE_BRANCH : "branch"
    PIPE ||--|{ PIPE_BRANCH : "holds, the trunk first"
    PIPE_BRANCH }o--o| PIPE_BRANCH : "parent"
    PIPE_BRANCH ||--|{ PIPE_POINT : "holds, two at least"
    PIPE ||--|| PIPE_END : "has, start of the trunk"
    PIPE_BRANCH ||--|| PIPE_END : "has, end"
    PIPE ||--o| IDENTITY : "has, when its style is linked to a type"
    CROSSING_SWAP }o--|| PIPE : "over"
    CROSSING_SWAP }o--|| PIPE : "under"
    LINK }o--|| SYNOPTIC : "target"
    LINK }o--o| PLACED_SYMBOL : "target_symbol"
```

## Reading notes

- **Identity is a part of its own**, so that a reference has none: a placed symbol of a view that points to a placed symbol of an installation reads the identity of that one (decided on 2026-11-20, see [Synoptics and views](01-synoptics-and-views.md#two-kinds-installation-and-view)).
- **`instance_id` is the key** of a placed symbol in the outputs, a field of its own, never one of the designation texts (decided on 2026-11-20). `internal_id` stays the key of every link inside the files.
- **A pipe linked to a type has an identity too**, the same part, so it is wired like a placed symbol (see [Pipes](05-pipes.md#a-pipe-whose-style-is-linked-to-a-type)).
- **Only what differs from the preset is kept** (`VALUE_CHANGE`: start value, unit, decimals; `TEXT_CHANGE`: texts of the faceplate), decided on 2026-11-20: a placed symbol that changes nothing holds nothing, and follows its preset when the preset changes.
- **A crossing keeps only the swaps**: the default rule (the last drawn passes over) needs nothing stored; the user's click stores which pipe passes over.
- **A pipe is one tree** (decision 0094): `PIPE` holds its style and its branches, the trunk first. Each other branch names the branch it leaves (`parent`) and where along it (`at`). **Junctions are not stored**: they are computed from `parent` and `at`.
- **Each branch has its own end**; the pipe has one start. Proposed by the assistant. No end shape is stored (decision 0098).
- A pipe that ends on another pipe has no kind of end yet: it waits for the open question of [Junctions](../symbols/pipes/junctions.md#open-questions).
- The content of an annotation (its shapes, its text, the signal of a value label) and of a scenario (its values) is not drawn yet.

## Open

- The name of `instance_id`: the research on names (T5) covered Metadata only and did not treat it.
- The names of the boxes: working names, like those of Metadata.
- Whether a synoptic file holds the computed geometry of its pipes (faster to open) or only their points (smaller, advised).
