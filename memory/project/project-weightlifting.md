---
id: project-weightlifting
title: WeightLifting - transformer from scratch
type: project
description: Decoder-only char-level transformer (~10.8M params) built and trained from scratch in PyTorch.
tags: [pytorch, transformers, deep-learning, machine-learning]
status: active
visibility: public
created: 2026-07-02
updated: 2026-07-03
stack: [PyTorch, CUDA, Weights & Biases]
url: https://github.com/jkarancs/WeightLifting
role: Sole author
related: [skill-pytorch, skill-transformers, skill-model-training, skill-experiment-tracking]
source: agent
---

A nanoGPT-style decoder-only transformer (~10.8M params: 384 embedding / 6 heads / 6 layers, block
size 256) implemented from scratch in PyTorch and trained on HuggingFace's megaGymDataset on a
6GB GTX 1660 Ti. Mixed-precision (AMP), gradient clipping, checkpoint/resume of model and optimizer
state, a CLI generation script (temperature/top-k), 11 tests, clean src/ layout, and W&B tracking.
Trained to step 5000 (val loss 3.68 -> 0.063, ~6h). "I trained a model from scratch" artifact.
