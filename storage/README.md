# storage

> [Home](../README.md) › Storage

How the application reads and writes its files. It is not about metadata: it holds for everything the application saves.

Status: draft, written from the Product Owner's oral description on 2026-11-10. Nothing here is validated.

## What it contains

| File | What it holds |
| --- | --- |
| [`files-and-conflicts.md`](files-and-conflicts.md) | The folder the application points to, the files it generates, and how conflicts between people working on the same folder are avoided. |
| [`git.md`](git.md) | One Git repository per project for all its files, and a simple Git page to commit, push and create branches; noted for later. |

## See also

- [Metadata](../metadata/README.md): types are saved as files through this storage.
- [Symbols](../symbols/README.md): Symbol Libs are saved as files through this storage.
