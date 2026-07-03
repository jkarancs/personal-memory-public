---
id: project-videolearningtool
title: VideoLearningTool - video knowledge triage
type: project
description: Desktop app that downloads, transcribes, and LLM-summarises videos for rapid watch/skip decisions.
tags: [llm, ai-engineering, python, csharp]
status: active
visibility: public
created: 2026-07-02
updated: 2026-07-03
stack: [Electron, JavaScript, Python, yt-dlp, C#, .NET 9, SQLite, OpenRouter]
url: ''
role: Sole author
related: [skill-llm-api-integration, skill-python, skill-csharp-dotnet]
source: agent
---

A personal video-knowledge-triage app in three stacks: an Electron UI (clipboard monitoring for
video links, download/delete, embedded playback), a Python pipeline (yt-dlp download, webvtt ->
transcript, LLM summarisation via OpenRouter with a structured summary/takeaways/actions/timestamps
prompt), and a .NET 9 ASP.NET Core Web API (controller + repository, EF, SQLite, Swagger) for link
storage. Working prototype with documented Electron IPC bugs; paused since 2026-06-06. Designed to
consume Phase 6 gap-analysis output (goal memories with blocking_skills) to tailor learning
material.
