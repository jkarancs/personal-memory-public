---
id: writing-what-legacy-code-taught-me-about-learning-ai-from-scratch
title: What Legacy Code Taught Me About Learning AI From Scratch
type: writing
description: LinkedIn post on what CERN legacy code taught me about durability, and building a transformer from scratch to learn AI fundamentals.
tags: [writing, ai-engineering, machine-learning, pytorch, cern, learning]
status: active
visibility: public
created: 2026-07-05
updated: 2026-07-05
related: [project-weightlifting, skill-pytorch, skill-transformers, project-cms-pixel-detector]
source: agent
---

I recently looked through some of the code I developed during my time at CERN. I still get GitHub PR notifications for those repositories to this day, which got me thinking: what does "legacy code" actually mean?

To me, legacy code means you built something that keeps being useful. It wasn't the most elegant C++ or Python — I'd certainly write it better today — but it worked, and it's still running. The ultimate proof isn't how clean the code looks; it's that no one has bothered to rewrite it from scratch.

That question — what makes something durable enough to outlive its author's involvement — is what pulled me into a recent deep dive into AI fundamentals. Plenty of tools let you build with AI without understanding it, but I wanted to go back to basics: how a Transformer actually works, how to train a model with PyTorch, how loss gets minimized and weights get optimized. Reading raw source code takes you back to first principles. You're not building anything novel, but mastering the fundamentals is what lets you build things that last.

Inspired by Andrej Karpathy, I did exactly that. I built my first model from scratch, trained it on a fitness dataset, and ran it locally on my laptop. Today, it predicts the next character or sequence when fed the name of an exercise — feed it "What is Close-Grip Bench Press?" and it outputs "A: The close-grip bench press is a compound exercise targeting the triceps and chest."

If you want to check out the implementation, take a look at my [WeightLifting repository](https://github.com/jkarancs/WeightLifting), or check out [Karpathy's excellent explanations on YouTube](https://www.youtube.com/watch?v=kCc8FmEb1nY).

Next up: training LoRAs on existing small language models. Once you understand the foundations, you can reach your goals much faster by standing on the shoulders of giants — and maybe build something that's still running in ten years, legacy PRs and all.

*Originally posted on [LinkedIn](https://www.linkedin.com/feed/update/urn:li:share:7479623509048987648/).*
