# CLAUDE.md — personal-memory-public (generated)

**Generated — do not edit content by hand.** This is the public export of
[`personal-memory`](../personal-memory): only `visibility: public` + `status: active` items,
produced by the [MemoryHub](../MemoryHub) engine's `hub export`. Manual edits to `memory/` or
`README.md` are overwritten on the next export.

- No engine code and no private content here.
- `hub.toml` (committed, not generated per run) makes this a valid **read-only** hub store:
  `allow_agent_writes = false`, so `hub validate` / `hub list` / `hub get` work but writes refuse.
- `related` links to non-exported (private/inactive) memories are stripped on export, with an
  inline `# N link(s) … removed` comment on the `related:` line.

## Regenerating (manual flow — a human diff review before publishing is a feature)
```bash
# 1. run from the private content repo
cd ../personal-memory
hub export --dest ../personal-memory-public          # add --dry-run to preview
# 2. review the diff here — check nothing private/sensitive slipped through
cd ../personal-memory-public && git diff
# 3. commit and push
```
The export is deterministic: running it twice produces zero diff. It refuses to run while
`hub validate` fails in the source repo, and prompts on email/phone/API-key-shaped content
(`--yes` to accept the warnings non-interactively).
