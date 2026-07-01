# personal-memory-public (generated)

**This repository is generated — do not edit by hand.**

It is the public export of a private memory store. In Phase 5, the [MemoryHub](../MemoryHub)
engine runs an export step over [`personal-memory`](../personal-memory) and writes the subset of
items marked `visibility: public` here. Editing files directly will be overwritten on the next
export.

## What lives here

- A generated tree of `visibility: public` memories (markdown + frontmatter).
- A generated `frontmatter.schema.json` for editor validation.

## What does NOT live here

- No engine code (that is in `MemoryHub`).
- No private content (anything `visibility: private` stays in `personal-memory`).

## Regenerating (Phase 5)

```bash
# from the private content repo, using the engine's export step (Phase 5)
hub export --to ../personal-memory-public
```

Until Phase 5 lands, this repo is an empty scaffold.
