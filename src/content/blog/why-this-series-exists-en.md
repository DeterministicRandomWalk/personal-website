---
title: 'Part 0: Why This Series Exists'
description: 'An introduction to a series about combining probabilistic judgment with deterministic engineering.'
pubDate: 'Jun 04 2026'
heroImage: '../../assets/series-00-introduction-illustration.png'
lang: 'en'
---

> Series: What production AI needs beyond an impressive model.

[阅读中文版。](/blog/why-this-series-exists-zh/)

AI is reshaping every industry. That no longer needs much explanation.

But “reshaping” means very different things in different environments. Rapid prototyping and a production system that must process complex corporate disclosures reliably are much farther apart than most technology headlines admit.

This series comes from work on production-grade AI for investment workflows: data pipelines, analytical tools, and evaluation systems that have to remain consistent, auditable, and useful beyond a demo.

This is not theory, and it is not a prediction. It is a set of engineering lessons from building such systems. It does not claim to be the answer for every environment.

## The Argument in One Paragraph

Consider a production pipeline that discovers and classifies sustainability-related corporate disclosures across heterogeneous websites.

It uses LLMs only for the 10% of the work that truly requires semantic judgment: deciding whether a link is ESG-related, whether a discovered domain belongs to the same company, or whether a page is genuine disclosure rather than marketing copy.

The other 90% uses deterministic code: link extraction, browser cascades, state management, retry logic, PDF handling, and budget allocation.

Not because we are skeptical of AI. Quite the opposite. We tried multiple alternatives, and they failed on the dimensions that mattered:

- Completeness
- Consistency
- Cost
- Reliability at scale

## Core Conclusion

AI understands meaning. Code guarantees behavior. Experience knows where to use each.

All three are necessary.

The hype around agentic AI says LLMs can handle everything by themselves: just give them tools and let them figure it out. Our experience points in the opposite direction. LLMs are extraordinary at judgment and poor at control flow.

Engineers building effective AI systems are not replacing code with agents. They are combining intelligence with precision, and using hard-won experience to decide where the boundary belongs.

This is not an anti-AI argument. This project uses large language model tools every day. They are frankly wonderful. The pipeline itself is now being refactored with their help.

The argument is this: coding ability is no longer the scarce resource. Engineering judgment is. No amount of agent framework packaging changes that. Fine, let us put a time limit on the claim: at least not for the next few years.

## Series Outline

| Part | Title | Core Sentence |
| :-- | :-- | :-- |
| 1 | The Impossible Task | A large investment workflow needs complete corporate disclosures. Chatbots and regular expressions both fail. |
| 2 | Why One Classifier Became Seven Layers | Each layer is a lesson from the previous failure. |
| 3A | The 90% Agents Would Destroy, Part I | Large language models are irreplaceable for semantic judgment; the other 90% is orchestration. |
| 3B | The 90% Agents Would Destroy, Part II | Six problems that look simple, each one enough to make an agent fail. |
| 4 | An Honest Comparison | Pipeline vs. agents: cost, compounding failure, and the probability of completing a long workflow correctly. |
| 5A | What the Research Says: Data | Reliability cliffs; labor research finds augmentation, not automation. |
| 5B | What the Research Says: Frameworks | Composition, not replacement. |
| 6 | The Leverage Gap | Senior + AI = team. The first rung of the career ladder has moved higher. |
| 7 | Context Accumulation | Coding ability is solved. Engineering judgment is not. |
| 8A | The Delegation Problem | Vague goals drift silently. Tools have ceilings. Models cannot see them. |
| 8B | The Autonomy Spectrum | Even the advocates say something more complex than the headlines. The future is differentiated autonomy. |
| 9 | The Other Extreme | “LLMs are dead” and “agents will rule the world” are equally attention-grabbing. Both are wrong in the same way. |
| 10 | Two Rooms | Demo enthusiasts cannot finish it. Domain experts do not start it. The pipeline shipped because it listened to both rooms. |
| 11 | Evidence | A project initially treated as another demo became a production system. The success was not in the model; it was in the engineering. |

## Bonus Essays

| Part | Title | Core Sentence |
| :-- | :-- | :-- |
| A | Rebuttal | We ask AI to dismantle its own series. Five rounds of attack and response, answered honestly. |
| B | Understand the System Before You Delegate the System | AI lowers the cost of learning a system, but it does not remove the need to understand it. Asking questions is not a substitute for understanding. |
| C | Standing in the Middle Ground | The thought that wakes you up at midnight. Not fear, but something more complicated. |

## Who This Is For

If you are an engineer deciding where to use agents and where to use code, this is a field report from production AI work.

If you are a manager who has heard that agents can replace your engineering team, this may show you things demos do not usually show.

If you are a junior developer wondering whether AI has made your skills obsolete, Part 6 is for you. The answer is more nuanced and more honest than either the optimists or the doomers tend to suggest.

If you are curious about what it takes to build AI systems for consequential workflows, this series is for you.

Start reading: Part 1 — The Impossible Disclosure Task.

---

Chinese version: [read Part 0 in Chinese](/blog/why-this-series-exists-zh/).
