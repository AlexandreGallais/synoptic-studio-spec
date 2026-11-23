# Files and conflicts

> [Home](../README.md) › [Storage](README.md) › Files and conflicts

Status: draft. Nothing here is validated.

The open source application has access to a folder. Everything it generates (types, Symbol Libs, and the rest) is saved as files in that folder. All reading and writing goes through the server, never through the browser's file loading.

## The folder

- The user points the application to a folder.
- The folder can be a shared one: people may choose a public shared folder and work on the same files at the same time.
- Types and Symbol Libs generate files, and these files must be saved somewhere in that folder.

## Saving

- **Each change is written to its file as it is made** (Product Owner, 2026-11-23): there is no Save step and no Save button anywhere, in Metadata, the symbol mode or the synoptic; what is in the file is what the user sees.
- **The application may also keep a memory while it runs**, never written to a file: the values of an enum column under its earlier kinds, so the user can switch and go back (see [Changing the kind](../symbols/11-enums-of-a-symbol-lib.md#changing-the-kind), decision 0092).
- **Closing the application forgets that memory**; reopening shows what the files hold.

## Undo history

- **Every action is kept in a history**, in every part of the application: the user can always go back, whatever was done (Product Owner, 2026-11-23, decision 0093).
- **The history, not a warning, protects from a mistake.** So nothing asks to confirm, except deleting a whole thing (see [Delete: a warning only for a whole thing](../screens/README.md#delete-a-warning-only-for-a-whole-thing)).
- **Undo and redo** use the usual keys.

```mermaid
flowchart LR
    A["An action: a line deleted, a kind changed, a field typed"] --> F["Written to its file at once"]
    A --> H["Kept in the history"]
    H -->|"undo"| B["The action is taken back, and the file written again"]
```

## Avoiding conflicts

As soon as something changes, the application must be able to check that the file it saves to is the same one that was loaded. This avoids two people overwriting each other.

- An option, to be ticked, makes the application check before saving that the file has not changed since it was loaded.
- An option makes the application refresh the folder before saving.
- Whether these are options or always on is not decided yet.

```mermaid
sequenceDiagram
    actor A as Person A
    actor B as Person B
    participant F as Shared folder
    A->>F: loads the file
    B->>F: loads the same file
    B->>F: saves a change
    A->>F: saves: the application checks the file is still the one loaded
    F-->>A: the file changed since it was loaded
    A-->>A: the application warns instead of overwriting
```

## Open questions

- Are the check and the refresh options, or always on? Open.
- What does the application do on a conflict: warn and stop, or offer to reload? Open.
- How far back does the undo history go, and does it survive closing the application? Decision 0053 refused a history kept in files for the versions of Metadata. Open.
- One history for the whole application, one per part, or one per file (the synoptic editor proposed one per open synoptic)? Open.
- Is the memory of the earlier kinds of an enum column a part of the history? Open.
- Which files are generated and under which names and sub-folders? To be specified. JSON files with no database are a leaning, not settled; for Metadata, see [Data model](../metadata/draft.md#as-json).
