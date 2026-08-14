---
id: project-videolearningtool
title: VidSavant - local-first video knowledge workspace
type: project
description: Personal local-first desktop app that turns video URLs into searchable, summarizable, chat-enabled knowledge items.
tags: [llm, ai-engineering, python, backend, testing]
status: active
visibility: public
created: 2026-07-02
updated: 2026-07-21
stack: [Python, NiceGUI, SQLite, yt-dlp, OpenRouter, FTS5, FastEmbed]
url: ''
role: Sole author
related: [skill-llm-api-integration, skill-python, skill-csharp-dotnet]
source: agent
---

VidSavant is the successor to the earlier VideoLearningTool prototype: a local-first desktop app that turns a video URL into a searchable, transcript-grounded knowledge item with template summaries, timestamp-cited chat, optional downloads, and durable background jobs. By 2026-07-21, the implementation had completed Phase 32 of the upgrade roadmap: scoped chat now supports immutable video/tag/selection/library snapshots, bounded cross-video FTS evidence, validated [V<id> MM:SS] citations with workspace deep links, degraded-member handling, explicit preflight/consent, restart-safe sessions, and snapshot-aware Markdown export. Phase 32 verification passed 805 tests (53 deselected), 51 Chromium browser tests, and ruff. The project remains personal and local-first; no live provider run was made for this phase.
