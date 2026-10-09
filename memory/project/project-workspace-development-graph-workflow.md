---
id: project-workspace-development-graph-workflow
title: Workspace development graph workflow
type: project
description: A dependency-graph workflow for planning, implementing, testing, and human feedback across personal repositories.
tags: [agentic, ai-engineering, tooling, knowledge-base]
status: active
visibility: public
created: 2026-07-30
updated: 2026-09-24
stack: [Markdown, Python, Typer, CLI]
role: Author and maintainer
related: [project-memoryhub, skill-agentic-knowledge-base]
source: self
---

On 2026-07-29 I completed the workspace migration to a dependency-graph development workflow. The
`agent-memory` store (plan: `specs/graph-workflow-plan.md`) is authoritative for migrated work: new
work starts exclusively with `/create-plan`, which decomposes an intent into single-agent nodes, and
existing work is inspected with `hub graph status` and taken with the skill matching each node's
status. The old `specs/` ledgers are frozen — pointers and acceptance contracts, not work tracking.
Migrated tracks include VidSavant hardening and commercialization, PowerCoach v1, the AI roadmap's
remaining phases, WeightLifting's human items, PersonalSite's post-launch phases, MemoryHub's Phase
6 acceptance, and the workflow itself.

**Node lifecycle:** `/implement` → `/test` issues the verdict (done · rejected · needs-feedback ·
replan) → `/replan` replaces a node whose plan turned out wrong. Graph verdicts, not agent prose,
signal the next phase.

**Human decisions are a two-step loop**, so a blocked node never costs the user the whole analysis:
an agent *preps* it with `/prep-feedback` (`needs-feedback` → `feedback-ready`, writing a decision
payload of context, choices with a recommendation, and/or a playbook), then the user answers in the
Bridge's Feedback view and the answer routes to the tier that can finalize it — accepted fix →
implement, playbook done → test, replan or custom text → replan, approve → done. `/feedback` is the
same loop without the console. The payload schema and routing table live in `agent-memory/PROTOCOL.md`.

**Audit layer** (added after the initial migration): `/validate-intent` re-reads a supernode that
reached `done` against the intent recorded in its own body — technical acceptance is not evidence
that what the user asked for was built — and `/audit-run` reads a finished orchestration's ledger,
journal, and evidence and files each *harness* defect as an ordinary `planned` node for the next
window. Both extend the graph rather than reporting into prose.

Durable lesson: a summary is a question never answered. There is no human in the loop mid-run, so
anything needing the user has to become a node with a decision payload the Bridge can show.
