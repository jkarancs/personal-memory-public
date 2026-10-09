---
id: project-agenthelm-orchestration-platform
title: AgentHelm orchestration platform
type: project
description: Deterministic scheduler between the workspace development graph and its terminals — windows become slots, each claiming the top actionable node and spawning its skill through Herdr; plus the Bridge console and the orc doctor unattended preflight.
tags: [agentic, ai-engineering, tooling, devops]
status: active
visibility: public
created: 2026-08-05
updated: 2026-09-24
stack: [Python, Typer, Herdr, AgentHelm]
role: Author / maintainer
related: [project-tiered-agentic-development-platform-design-phase, project-workspace-development-graph-workflow]
source: agent
---

AgentHelm is the deterministic scheduler between the workspace's
development graph and its terminals. A **window** — a start time plus a duration that may exceed a
day — becomes a fixed number of **slots**; each slot claims the highest-priority actionable node
from the `agent-memory` graph and spawns, through Herdr, the skill that node's *status* calls for
(`/implement`, `/test`, `/prep-feedback`, `/replan`, `/validate-intent`). It owns no work of its
own: the graph supplies the node and writes the verdict, Herdr owns the tabs and worktrees,
AgentHelm is the policy in between. Priorities live in `helm.toml` `[priorities]`.

**Surfaces**
- `orc plan | run | status | adjust | cancel | summary` — the CLI; `/orchestrate` is the skill
  wrapper over `plan` + `run`. `hub` is not on `PATH`, so every call carries `--hub`.
- `orc bridge` — loopback-only console (127.0.0.1:8737) with a Feedback view over the graph's human
  decision queue and a Helm view that plans, starts, and monitors the day's run. It adds no policy;
  it shells the same `hub` and `orc` the CLI does, so there is exactly one launcher path.
- `orc doctor` — inspection-only preflight that answers whether a window can run *unattended*,
  which is a property of the environment rather than of the schedule. Six preconditions: `hub`
  resolvable at the path `orc` will use, host headroom, Codex hook trust, loopback MCP endpoints
  answering, Herdr reachable, and an open Herdr workspace for every leftover
  `<repo>/.worktrees/<node>`. It exits non-zero naming each remediation. The host check is the one
  dynamic question — a machine can satisfy every static precondition and still be unusable — and
  the same floor is re-sampled between slots, so a night that goes bad ends on the machine rather
  than on four innocent nodes.

**Milestone 2026-07-31 — bootstrap shipped:** repository created with uv/pytest/ruff foundations,
validated AgentHelm and workspace model TOML loaders, and a typed subprocess driver for Herdr tab,
agent, worktree, and notification commands.

**Milestone 2026-08-05 — stale worktree recovery:** preflight now reopens each existing checkout
through Herdr and verifies a fresh workspace listing, refusing only when recovery genuinely fails.
Previously a worktree whose Herdr workspace had been closed blocked the window outright. Green on
the full 329-test suite and lint at that date.

Durable lesson: unattended means the harness proves the environment before spending a slot on it —
a precondition discovered mid-run is a wasted night, not a warning.
