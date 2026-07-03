---
id: preference-notebook-learning-style
title: Notebook-first, summary-first learning style
type: preference
description: Skim/summary-first triage, hands-on notebooks, build-it-yourself checkpoints.
tags: [learning]
status: active
visibility: public
created: 2026-07-03
updated: 2026-07-03
related: [preference-learning-by-implementation, preference-math-forward-learning, preference-learning-cadence]
source: agent
---

Skims ideas first and rarely commits to hour-long videos: needs a summary up front, then decides
whether to go deep. A resource is worth the time when it solves an immediate problem and is
straight to the point. Very hands-on - works best with runnable notebooks, often built with AI.

Notebook design rules (verbatim from the WeightLifting CLAUDE.md, for any tool generating
learning material):
- **Lead with the map.** Open with the big picture - where the concept fits and the one question
  it answers - before any detail.
- **Make it visual.** Ground each idea in a plot, distribution, or diagram. Pair every formula
  with a runnable numerical example and a visualization; always label plot axes.
- **Decompress, don't abstract.** Build up from the smallest concrete case - small dimensions,
  explicit arrays to inspect - instead of the general symbolic form.
- **Make me build and explain.** Leave the core mechanism as a stub to implement, with the
  reference solution after it, not before; add checkpoints to predict or explain back.
- **Keep it runnable.** Toy scale, mechanisms from scratch rather than hidden in library calls,
  tight prose - let the code and plots carry the explanation.
