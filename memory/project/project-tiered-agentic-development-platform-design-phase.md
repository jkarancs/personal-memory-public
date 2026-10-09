---
id: project-tiered-agentic-development-platform-design-phase
title: AgentBosun — tiered agentic development platform
type: project
description: 'Multi-tier agentic system for building software: orchestrator, planner, workers, and memory curator with cost-matched model routing, HITL dashboard + mobile approvals.'
tags: [agentic, ai-engineering, llm, tooling]
status: active
visibility: public
created: 2026-07-11
updated: 2026-10-03
stack: [Python, LangGraph, Langfuse, LiteLLM, Postgres, Telegram Bot API]
role: Architect / author
related: [skill-llm-orchestration, skill-agentic-knowledge-base, skill-prompt-engineering, project-memoryhub]
source: agent
---

AgentBosun is an implemented multi-tier agentic development platform with cost and tracing guardrails, a sandboxed LangGraph developer worker, routing and cascade policies, and a planner–critic–human-approval workflow. Its multi-worker pipeline remains under acceptance; the design notes and build milestones below distinguish the original plan from shipped work.

**Envisaged components**
- Human interaction dashboard (workflow/agent visualization, draft plan submission) + mobile chat approvals
- Main orchestrator ("CEO") — GPT-5.6 Luna (tier 3): routes requests, escalates to Architect, dispatches tasks, triggers memory updates
- Planner/Architect — Claude Fable 5 (tier 1) drafts and critiques plans with human spec elicitation; GPT-5.6 Sol/Terra (tier 2) decomposes approved plans into tasks
- Workers — Developer (tier 2/3/4 by difficulty), Tester (tier 3/4), Code Reviewer (tier 2, different model family than developer)
- Memory Curator — DeepSeek V4 Flash (tier 5): creates/consolidates/deduplicates memories asynchronously

**Tier ladder** (July 2026 pricing per MTok in/out): T1 Claude Fable 5 ($10/$50) · T2 GPT-5.6 Terra ($2.50/$15), Claude Sonnet 5 · T3 GPT-5.6 Luna ($1/$6) · T4 GLM-5.2 ($1.40/$4.40), DeepSeek V4 Pro ($0.435/$0.87) · T5 DeepSeek V4 Flash ($0.14/$0.28)

**Key research-backed design decisions (from 2026-07-10 research session)**
- Cascade-with-escalation routing (FrugalGPT/RouteLLM pattern) instead of a-priori difficulty prediction; escalation rate as routing-quality metric
- Single-writer code changes; parallelism only for read-only work (Cognition/Anthropic findings)
- Async memory curation on cheap model + batch API (Letta sleep-time compute / Mem0 ADD-UPDATE-DELETE pattern); draft→reviewed lifecycle like MemoryHub
- Artifacts (specs, plans, diffs, test reports) in git as inter-agent communication, not chat transcripts
- Langfuse (self-hosted) as observability/eval backbone; cost-per-successful-task as north-star metric with per-role Pareto reviews
- KV-cache-friendly prompt design (stable prefixes, append-only context)
- HITL: plan approval gates + Telegram/Slack bot with inline approve/reject instead of custom mobile app; durable checkpoint/resume (LangGraph-style interrupts)

Missing pieces identified relative to original notes: eval harness, sandboxed execution, task queue with durable state, budget governor, artifact store.

**Build progress (implemented as `AgentBosun`):** foundations + measurement rails (P6, accepted 2026-07-13), sandboxed LangGraph developer worker (P7), orchestrator with routing/cascade policies (P8; A/B flipped the default to cascade-a at 71% cost saving), planner→critic→human-approval workflow on a Hetzner CX33 (P10). P11 (multi-worker pipeline) built but acceptance still open after a cost-attribution/failure-amplification remediation lane (C1–C4, 2026-07-17/18): C4's L-band validation ended in an honest refusal because the sandbox couldn't satisfy the plan's packaging demands and the killed run lost its cost ledger rows.

**Milestone 2026-07-19 — C5a shipped:** the worker environment is now a machine-readable contract generated from the enforcing code and rendered into every planner/critic/developer/tester/reviewer prompt; the sandbox honestly supports Python packaging (harness-owned offline editable installs — console scripts and importlib.metadata work with the network still off); and a zero-spend lint blocks plans whose acceptance criteria cannot execute in the declared environment (the exact C4 failure reproduced as a regression fixture). Durable lesson: the harness owns the environment; capabilities are provided or declared absent, never discovered through paid refusals.

**Milestone 2026-07-19 — C5b shipped (remediation lane complete):** zero-spend forensics on the failed C4 run proved the broken money trail was purely a durability loss — all 95 unmatched proxy rows carried correct correlation tags and were simply never persisted before the kill. Fixes landed: a refusal circuit breaker and a same-cause context-blowup cap (futile attempts abort with `environment_mismatch` and retry at the same tier, never escalating — a bigger model cannot conjure a missing binary), a run-owned wall-clock deadline with terminal `timeout`/`killed` states, graceful kill handling (nothing left `running`, no manual cleanup), and a write-ahead cost journal so attribution survives any kill. Durable lesson: money records must be write-ahead, not checkpoint-flushed — kills land exactly when the most spend is in flight. Next: a fresh P11 acceptance attempt (D-C5-3) is now proposable, pending the human's worker-image rebuild and a small optional paid kill drill.

**Milestone 2026-07-31 — AgentHelm bootstrap shipped:** created the new `AgentHelm` repository with uv/pytest/ruff foundations, validated AgentHelm and workspace model TOML loaders, and a typed subprocess driver for Herdr tab, agent, worktree, and notification commands. The repository gate passes with 8 pytest tests and clean ruff checks; the scheduler and orchestration CLI remain for later graph nodes.
