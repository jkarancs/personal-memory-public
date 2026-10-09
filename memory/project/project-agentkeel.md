---
id: project-agentkeel
title: AgentKeel
type: project
description: OpenRouter chat client with tool calls, structured outputs, a model registry, per-call cost telemetry, and an eval harness for price/performance.
tags: [python, llm, ai-engineering, agentic, tooling]
status: active
visibility: public
created: 2026-09-23
updated: 2026-10-06
stack: [Python, httpx, Pydantic, Typer, SQLite, matplotlib, pytest]
url: https://github.com/jkarancs/AgentKeel
role: Author
related: [project-memoryhub, skill-llm-orchestration]  # 1 link(s) to non-exported memories removed by `hub export`
source: agent
---

The keel of a small agent platform: an OpenRouter chat client for Python (also any
OpenAI-compatible endpoint) with retries, streaming, tool calls, structured outputs validated
into Pydantic models, a curated model registry (context window, $/Mtok, tiers), and per-call
cost telemetry in SQLite. Agent loops, eval runners, and routers bolt onto it.

Its eval harness (`agentkeel evals`) measures price/performance per agent job — quality x cost x
latency — across three suites with mixed scoring (deterministic dedupe F1, schema-valid-JSON
compliance, and LLM-as-judge summarization). The judge-calibration work exposed poor agreement on near-tied summaries (judge-human
Cohen's kappa -0.216 initially and +0.122 after rubric revision; the intended 0.4 gate did
not pass). Pairwise judging in both display orders feeds a Bradley-Terry ranking. In the
stored comparison, inter-judge ranking correlation was 0.40 and non-contradiction was 90%,
including ties; exact verdict agreement was 46.7%. These are limited comparison signals,
not evidence of a calibrated absolute judge.

The platform also includes a draft-only memory curator, JobScout job scoring, and a loop
demo connecting MemoryHub recall, AgentBosun routing, judge-gated escalation, and an
OpenTelemetry timeline. JobScout can export work for an agent to score and import the
answers without an OpenRouter call.

https://github.com/jkarancs/AgentKeel
