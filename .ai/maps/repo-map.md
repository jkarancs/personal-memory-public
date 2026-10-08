---
description: Public export structure — generated memory content, read-only configuration, and maintained agent docs.
status: reviewed
---
# Repo Map

> Parent: [../CONTEXT.md](../CONTEXT.md)

```text
personal-memory-public/
  AGENTS.md          — agent entry point; maintained outside the export
  RTK.md             — command-output instructions imported by AGENTS.md
  hub.toml           — read-only store configuration; not regenerated each run
  README.md          — generated memory index; regenerate instead of hand-editing
  memory/            — generated public active memories; skip for documentation work
  .ai/               — maintained knowledge layer; outside the export's managed paths
    CONTEXT.md       — complete knowledge index
    manifest.yaml    — generator resolutions
    maps/            — regenerable repository inventory
```

The exporter writes `README.md` and selected memories, removes stale files only below the destination content root, and creates `hub.toml` only when absent (`../../../MemoryHub/src/memoryhub/export.py` · `export_store`, `_dest_content_root`). Root `.ai/` and agent documentation survive exports.
