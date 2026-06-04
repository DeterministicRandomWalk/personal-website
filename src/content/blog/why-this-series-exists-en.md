---
title: 'Part 0: Why This Series Exists'
description: 'An introduction to the series: “We built a pipeline with tens of thousands of lines of code. Why agents could not do it.”'
pubDate: 'Jun 04 2026'
heroImage: '../../assets/series-00-introduction-illustration.png'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[阅读中文版。](/blog/why-this-series-exists-zh/)

AI is reshaping every industry. That no longer needs much explanation.

But “reshaping” means very different things in different environments. A startup using agents to prototype quickly and an institutional investor using AI to process ESG data from thousands of companies are much farther apart than most technology headlines admit.

This series comes from the perspective of a quant developer. The core goal of my department is to help investment teams modernize their investment processes and decision-making. Day to day, that means building data pipelines, analytical tools, and evaluation frameworks for portfolio managers, analysts, and risk teams.

This is not theory, and it is not a prediction. It is a field report from building production AI systems in this specific context. It does not claim to be the answer for every other environment.

## The Argument in One Paragraph

We built a production pipeline with tens of thousands of lines of code that can retrieve complete ESG information from corporate websites around the world.

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
| 1 | The Impossible Task | Portfolio managers need ESG data from 5,000 websites. Chatbots and regular expressions both fail. |
| 2 | Where 7,400 Lines Came From | Seven layers of classification, each one a lesson from the previous failure. |
| 3A | The 90% Agents Would Destroy, Part I | Large language models are irreplaceable for semantic judgment; the other 90% is orchestration. |
| 3B | The 90% Agents Would Destroy, Part II | Six problems that look simple, each one enough to make an agent fail. |
| 4 | An Honest Comparison | Pipeline vs. agents: 3–10 times more expensive, exponential failure rates, and a 0.6% chance of perfect execution. |
| 5A | What the Research Says: Data | Reliability cliffs; labor research finds augmentation, not automation. |
| 5B | What the Research Says: Frameworks | Composition, not replacement. |
| 6 | The Leverage Gap | Senior + AI = team. The first rung of the career ladder has moved higher. |
| 7 | Context Accumulation | Coding ability is solved. Engineering judgment is not. |
| 8A | The Delegation Problem | Vague goals drift silently. Tools have ceilings. Models cannot see them. |
| 8B | The Autonomy Spectrum | Even the advocates say something more complex than the headlines. The future is differentiated autonomy. |
| 9 | The Other Extreme | “LLMs are dead” and “agents will rule the world” are equally attention-grabbing. Both are wrong in the same way. |
| 10 | Two Rooms | Demo enthusiasts cannot finish it. Domain experts do not start it. The pipeline shipped because it listened to both rooms. |
| 11 | Evidence | The credit team thought it was another demo. They got a production system. The success was not in the model; it was in the engineering. |

## Bonus Essays

| Part | Title | Core Sentence |
| :-- | :-- | :-- |
| A | Rebuttal | We ask AI to dismantle its own series. Five rounds of attack and response, answered honestly. |
| B | Understand the System Before You Delegate the System | AI lowers the cost of learning a system, but it does not remove the need to understand it. Asking questions is not a substitute for understanding. |
| C | Standing in the Middle Ground | The thought that wakes you up at midnight. Not fear, but something more complicated. |

## Who This Is For

If you are an industry engineer deciding where to use agents and where to use code, this is a field report from a developer inside an investment institution.

If you are a manager who has heard that agents can replace your engineering team, this may show you things demos do not usually show.

If you are a junior developer wondering whether AI has made your skills obsolete, Part 6 is for you. The answer is more nuanced and more honest than either the optimists or the doomers tend to suggest.

If you are simply curious about what it feels like to build AI application systems inside an investment institution in 2026, welcome.

Start reading: Part 1 — The Portfolio Manager’s Impossible Task.

---

Chinese original: [第0篇：这个系列为什么存在——它讲什么](/blog/why-this-series-exists-zh/).

Originally published externally: [source article](https://mp.weixin.qq.com/s/qw-Ie9LnVovSIEnW4x83GA).
