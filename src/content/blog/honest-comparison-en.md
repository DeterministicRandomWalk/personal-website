---
title: 'Part 4: An Honest Comparison'
description: 'A production pipeline and a general-purpose agent compared on cost, completeness, reproducibility, and compounding failure.'
pubDate: '2026-06-08T12:00:00Z'
heroImage: '../../assets/series-04-honest-comparison-illustration.jpeg'
lang: 'en'
---

> Series: What production AI needs beyond an impressive model.

[Previous: Part 3B.](/blog/agents-destroy-orchestration-en/)  
[阅读中文版。](/blog/honest-comparison-zh/)

The same task can cost a deterministic pipeline one unit and a general-purpose agent tens of units, or more, if the agent completes it at all.

The previous essays explained how the system acquired its layers: why classification needs context, why LLMs belong in the ambiguous semantic remainder, and why extraction, normalization, stopping rules, PDF handling, state, and compliance need deterministic control.

This essay puts the two approaches side by side.

The figures below are an order-of-magnitude model, not a vendor quote or a universal benchmark. The agent is given favorable assumptions: batching, a capable model, a large context window, and access to browser tools. The comparison is therefore not between a careful pipeline and a deliberately naive agent.

## The Cost of the Brain

Keyword scoring, URL-tree analysis, score inheritance, document-name signals, and iterative caches remove clear cases before an LLM is called.

| Cost dimension | Deterministic pipeline | General-purpose agent |
| :-- | :-- | :-- |
| Model input | Ambiguous remainder after filtering | Broad raw candidate set plus context |
| First pass | Small and bounded | Grows with website size |
| Later passes | Reuses path and classification memory | Often pays for context again |
| Model responsibility | Semantic judgment | Judgment, exploration, and control |
| Relative cost | 1× baseline | Often tens of times higher |

The important difference is what determines model cost. In the pipeline, cost follows ambiguity. In the agent, cost tends to follow the amount of material encountered.

A large website may expose thousands of candidate links, but only a small subset should require semantic judgment. Sending everything to the model is not intelligence. It is failure to separate known behavior from unknown meaning.

## The Cost of the Body

Classification is only the brain. The body is orchestration: extraction, deduplication, query normalization, stopping, PDF scheduling, browser fallback, state management, and compliance checks.

| Stage | Deterministic pipeline | General-purpose agent |
| :-- | :-- | :-- |
| Link extraction | Fixed parsers and normalization | Tool calls plus runtime judgment |
| Query parameters | Rules prevent duplication and loops | Missing rules can create unbounded exploration |
| Stopping | Explicit budgets and priorities | “More content exists” keeps the task alive |
| PDF handling | Specialized download and verification | Each failure creates another reasoning loop |
| Deferral | Pages first, documents later | Arrival order often becomes priority |
| Browser fallback | Test, record, and reuse | Repeated trial and error |
| Compliance | Deterministic pre-request checks | Constraints must be reinterpreted during each run |

These actions consume compute in a pipeline, but they do not need fresh model judgment. Their behavior is stable and their marginal cost is predictable.

An agentic implementation repeatedly turns bodily motion into thought. A failure creates another observation, another context update, another tool call, and another decision. Cost spreads along the failure path.

If the pipeline is normalized to `1×`, an otherwise capable agent without the specialized engineering layers can plausibly land one or two orders of magnitude higher. The exact multiplier is less important than the mechanism: repeated context, browser interaction, recovery, and rediscovery.

## Incompleteness Is More Expensive Than Tokens

The visible bill is not the main risk.

A deterministic pipeline does not merely hope that a model notices a report hidden behind a generic content path. It can propagate evidence from the page that discovered the file, preserve the parent-child relationship, and replay the decision later.

A general-purpose agent can often return useful material. But “useful material” and “systematic coverage of everything discoverable” are different products.

In an investment workflow, absence is especially dangerous. A wrong answer can be challenged. A document that was never discovered does not announce that it is missing.

## Nondeterminism Compounds

Agents can perform well on short tasks. Long workflows change the mathematics because reliability multiplies across dependent decisions.

Suppose each decision is correct 95% of the time, a generous assumption. A workflow with 100 dependent decisions has:

```text
Probability of a completely correct run = 0.95^100 ≈ 0.6%
```

This does not mean every run collapses visibly. More often, most decisions are correct and a few drift silently. Because the output remains plausible, partial failure can be harder to detect than total failure.

| Dimension | Deterministic pipeline | General-purpose agent |
| :-- | :-- | :-- |
| Consistency | Same input follows the same path | Runs may drift |
| Reproducibility | State and logs can be replayed | Identical decisions are not guaranteed |
| Debugging | Trace a rule, state, or failure point | Interpret a generated trajectory |
| Completeness | Define, measure, and regression-test it | Often settles for “looks sufficient” |
| Compliance | Apply the same check every time | Depends on the model remembering the constraint |

Parameter loops, silent document failures, and unbounded news exploration are not random anecdotes. They are structural consequences of missing state, budgets, and deterministic boundaries.

## Do Not Confuse a Request with a Production Line

“Find the latest sustainability report for this company.”

That is an excellent agent task: the target is clear, the scope is small, and a person can verify the result.

“Systematically cover discoverable disclosures across a large company universe, with auditability and reproducibility.”

That is not a request. It is a production line.

The difference is not whether the model is intelligent. It is whether the task requires experience to be converted into behavior that executes every time.

## The Useful Composition

The right architecture is not agent or pipeline. It is agent as interface, pipeline as engine.

```text
User: Run disclosure collection for this company.
Agent: Interpret the intent and prepare validated parameters.
Pipeline: Execute classification, collection, retries, state, and compliance.
Agent: Summarize results and surface failures for human judgment.
```

The agent understands intent and explains results. The pipeline performs the behavior that should not be reinvented on every run.

## “But Agents Can Write the Code”

They can, and this is one of their most valuable roles.

AI coding tools can accelerate implementation, testing, and refactoring of deterministic systems. But writing code quickly is not the same as knowing which code needs to exist.

The expensive discoveries emerge during real operation: links that appear only after rendering, nonstandard elements that contain downloads, parameters that form loops, and documents that open visually but never reach storage. Once the failure is understood and the boundary is described, AI can help implement the fix.

Code generation is becoming abundant. Identifying hidden requirements, choosing system boundaries, and deciding what must execute deterministically remain engineering judgment.

## Where Each Approach Fits

Agents fit:

- **One-off tasks**, where building a dedicated system would cost more than several model calls.
- **Exploration**, before the shape of the problem is understood.
- **Code generation**, to build and maintain deterministic systems.
- **Low-risk, high-variety work**, where a person can review the result.

Deterministic pipelines fit:

- **High-throughput processing**, where large volumes need consistent treatment.
- **High reliability**, where small error probabilities compound.
- **Stateful multi-step workflows**, where facts and decisions persist across stages.
- **Zero-tolerance constraints**, including permissions, compliance, and budgets.
- **Frequent micro-decisions**, such as batching, timeouts, retries, and rate limits.

This may not be the permanent frontier of model capability. It is the engineering boundary that reliable systems need to respect today.

Next: Part 5A — What the Research Says: The Data.

