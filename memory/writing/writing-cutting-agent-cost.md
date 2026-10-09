---
id: writing-cutting-agent-cost
title: Cutting agent cost
type: writing
description: Cascade-a reduced measured coding-task cost by 70.5% on 13 golden tasks, with the crucial limit that escalation was never exercised.
tags: [writing, ai-engineering, llm, agentic, testing]
status: active
visibility: public
created: 2026-10-03
updated: 2026-10-06
related: [project-agentkeel, project-tiered-agentic-development-platform-design-phase]
source: agent
---

Once I had a way to measure agent jobs, I wanted to see what happened when the model choice became a routing policy. AgentBosun can start a coding task on a cheaper tier and escalate when it needs to. The useful measure for me is what it costs to solve the task.

In the policy comparison run on 2026-07-14, cascade-a cut cost per 1,000 tasks from $45.339 to $13.374 compared with all-tier2. That's a 70.5% reduction. Both solved all 13 golden tasks.

There's a substantial caveat next to that result: **escalation was 0%**. The starting tier solved every task in the cascade-a run, so this set never exercised the escalation ladder.

## The policy comparison

The stored run, `bosun-policies-bcf872fbadeb`, compared four policies on the same 13 coding tasks in the `bosun-coding` suite. All four solved 13/13.

| Policy | Cost per 1,000 tasks |
|---|---|
| all-tier2 | $45.339 |
| static | $29.006 |
| cascade-b | $15.904 |
| cascade-a | $13.374 |

[![Coding policy costs at equal measured quality: all-tier2 costs $45.339 per 1,000 tasks, static $29.006, cascade-b $15.904 and cascade-a $13.374; each solves all 13 tasks](/figures/cutting-agent-cost/chart-policy-cost.svg)](/figures/cutting-agent-cost/chart-policy-cost.svg)

These are the measured task costs normalized to 1,000 tasks, not the cost of a thousand-task experiment. They describe that run's recorded model spend, not the full operating cost of the platform.

Cascade-a started at tier4, and every task finished there. The experiment therefore supports starting these tasks on that cheaper tier. It doesn't establish how much a cascade saves when tasks fail, how reliably escalation recovers them, or how the result changes on harder work.

## What changed

The result was enough to make cascade-a the default for this tested workload. The routing and escalation mechanisms are implemented; the evidence for the ladder itself still needs tasks that force it to operate.

I find that distinction useful. A lower bill at the same measured pass rate is worth keeping, but 13 tasks are a small basis for a general claim. If I call this a successful cascade without mentioning the zero escalation rate, I hide the most important limit of the experiment.

Next I want to test tasks that require escalation and account for the failed attempts as well as the successful one. That's the comparison that will tell me whether the cheaper starting point remains cheaper through the whole run.

The implementation is in [AgentBosun](https://github.com/jkarancs/AgentBosun), with the eval results stored through [AgentKeel](https://github.com/jkarancs/AgentKeel).
