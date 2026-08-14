---
id: skill-fine-tuning
title: LLM fine-tuning (LoRA/QLoRA)
type: skill
description: Parameter-efficient fine-tuning of open models.
tags: [fine-tuning, llm, machine-learning]
status: active
visibility: public
created: 2026-07-02
updated: 2026-07-15
proficiency: beginner
related: []  # 1 link(s) to non-exported memories removed by `hub export`
source: agent
---

Learning parameter-efficient fine-tuning (LoRA/QLoRA, PEFT, bitsandbytes 4-bit) on the current learning roadmap: local runs on a 6GB card, then a portfolio-grade 7-8B fine-tune on a rented GPU published to the HF Hub. In progress, not yet a shipped artifact.

Evidence (2026-07-15): implemented LoRA from scratch in WeightLifting (roadmap P5) — hand-rolled `LoRALinear` (ΔW = B·A scaled by α/r, B zero-initialized), in-place injection into an own 10.8M-param char transformer, merge/unmerge for zero-overhead inference, adapter-only checkpoints (~225 KB vs 40+ MB), and a char-level vocab bridge for cross-domain transfer; verified on the 6 GB card that switching adapters off recovers the base model's val loss exactly (catastrophic-forgetting probe). No peft/bitsandbytes used — implementation from first principles.
