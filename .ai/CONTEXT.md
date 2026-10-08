---
description: Public export orientation — source store, consumer, export boundaries, and repository map.
status: reviewed
---
# Context

> Parent: [../AGENTS.md](../AGENTS.md)

## Snapshot
PersonalSite consumes this public export through its `content/store` submodule (`../../PersonalSite/.gitmodules`).

## Mental model
```mermaid
flowchart LR
  P[personal-memory] -->|MemoryHub hub export| E[personal-memory-public]
  E -->|human diff review and publish| G[Git remote]
  G -->|content/store submodule| S[PersonalSite]
```

## Navigation
| Need | Open |
|---|---|
| Repo structure and generated-file boundaries | [maps/repo-map.md](maps/repo-map.md) |
| Exported memory index | [../README.md](../README.md) |
| Read-only store configuration | [../hub.toml](../hub.toml) |
| Source store instructions | [../../personal-memory/AGENTS.md](../../personal-memory/AGENTS.md) |
| Engine instructions | [../../MemoryHub/AGENTS.md](../../MemoryHub/AGENTS.md) |
| Knowledge profile and cached resolutions | [manifest.yaml](manifest.yaml) |
