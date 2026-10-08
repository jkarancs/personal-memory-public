# AGENTS.md

> **Project:** personal-memory-public — the generated public export of the private `personal-memory` store, produced by the MemoryHub engine.
> **Core constraints:** Regenerate `memory/` and `README.md` through `hub export`; hand edits are overwritten. This repo holds exported content, no engine code or private content. `hub.toml` sets `allow_agent_writes = false`, so store reads work and agent writes refuse.

## Commands
Run these from this repo's root; the CLI comes from the private store's uv-managed venv and resolves the local `hub.toml` from cwd.

| Intent | Command | Authority |
|---|---|---|
| Validate the public store | `../personal-memory/.venv/bin/hub validate` | `hub.toml`, read-only `personal` profile |
| Preview the next export | `cd ../personal-memory && .venv/bin/hub export --dest ../personal-memory-public --dry-run` | Source store's `hub.toml`; changes nothing |

## Regenerating
Run from the private content repo, then review the diff here before committing or pushing:

```bash
cd ../personal-memory
.venv/bin/hub export --dest ../personal-memory-public
cd ../personal-memory-public
git diff
git diff --cached
```

The export selects only `visibility: public` + `status: active` memories. It strips `related` links to non-exported memories and annotates the `related:` line with the removed count. It is deterministic: a second run produces zero diff. Source validation failures refuse the export; email, phone, and API-key patterns require confirmation (`--yes` accepts warnings non-interactively). These behaviors are defined in `../MemoryHub/src/memoryhub/export.py` · `export_store`, `_select`, `_render`, `_scan`.

## Conventions
- Work tracking: development graph, scope `workspace-agent-docs` · Branch: `main`, direct commits · Commit: one-line summary with a conventional prefix, no body — on the user's behalf; amend-on-fix ok.

## Judgment Boundaries
**NEVER**
- Commit or push before the user reviews the exact diff — this is the final gate for public content, and also applies to documentation-only changes.
- Write secrets, tokens, or credentials into files or work records — reference names and their store instead.

**PROCEED**
- Edit agent documentation outside `memory/` and `README.md` when the task calls for it; the exporter leaves these paths alone.

**ALWAYS**
- Preserve export changes outside the task's scope, including changes already staged, when preparing a documentation commit.
- Run the public-store validation and read its output before calling the work done.

Workspace layer: [../AGENTS.md](../AGENTS.md) — cross-repo conventions, graph workflow, and personal-memory rules.

## Knowledge Layer
Before exploring the repo or editing anything, read [.ai/CONTEXT.md](.ai/CONTEXT.md). It is the complete knowledge index. Read the smallest file that answers the task; stop when the next action is clear.

@RTK.md
