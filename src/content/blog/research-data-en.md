---
title: 'Part 5A: What the Research Actually Says About AI Replacing Engineers'
description: 'METR’s reliability cliff and Anthropic’s labor-market research: capability is rising rapidly, but augmentation still dominates real-world use.'
pubDate: '2026-06-11T12:00:00Z'
heroImage: '../../assets/home-deterministic-random-walk-art.png'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[Previous: Part 4 — An Honest Comparison.](/blog/honest-comparison-en/)

[阅读中文版。](/blog/research-data-zh/)

Every time something moves in AI — a new model, a new agent framework, a new benchmark result — countless posts on Twitter and public feeds announce that “everything has changed.” The research says something more interesting, and more useful.

The previous essay compared pipelines and agents: costs separated by orders of magnitude, failure rates compounded exponentially, and the probability of 100 consecutive decisions all being correct fell as low as 0.6%. But what do researchers — not venture capitalists, not social media — actually say?

Everyone has an opinion. Very few people have data.

Every time the AI industry stirs — a model release, an agent framework, a benchmark climbing the leaderboard — the posts arrive on schedule: “The big one is coming.” “The world has fundamentally changed.” “The outlook for engineers is not good.” Each one sounds more apocalyptic than the last, as if every product launch were humanity’s final day at work.

It feels like the weather forecast: every week brings a “once-in-a-century storm.” After hearing enough of them, you start leaving home in shorts.

The venture-capital world says agents will take over every workflow.

Some developers are equally certain that their jobs are untouchable.

The noise is loud. The data is quiet. And the story told by the data pleases neither side, because it supports neither hype nor denial. Much like this series.

Let us look at what happened when people actually measured the claims.

## METR’s Time Horizon: The Reliability Cliff

METR — Model Evaluation & Threat Research — tracks what may be the most important measure of agent capability: at a given success threshold, how complex a task can a model complete autonomously?

They express complexity as a “time horizon”: how long the task would take a human expert. Then they ask how long a task the best models can handle at a 50% or 80% success rate.

METR’s v1.1 results, updated in May 2026, tell a story of rapid progress coexisting with a hard bottleneck. Here are selected point estimates for the 50% time horizon:

| Model | 50% time horizon |
| :-- | :-- |
| GPT-2 (2019) | About 3 seconds |
| GPT-4 (2023) | About 4 minutes |
| Claude 3.5 Sonnet, October 2024 | About 21 minutes |
| o3 (2025) | About 2 hours |
| GPT-5 (2025) | About 3 hours 23 minutes |
| Claude Opus 4.5 (2025) | About 4 hours 53 minutes |
| Claude Opus 4.6 (2026) | About 12 hours |

From 3 seconds to roughly 12 hours: an increase of more than ten thousand times in seven years. If your child grew at that rate, beginning at 50 centimeters, the result would quickly stop being a parenting problem.

The curve is not linear. It is exponential. METR v1.1 estimates an overall doubling time of about 6.2 months, accelerating to about 4.2 months when measured from 2023 onward. Anyone building production systems should take this trend seriously. The capability curve is steeper than most people imagine.

But the next set of numbers changes the discussion.

Those headline time horizons use a 50% success threshold. The model has a coin-flip chance of completing the task.

At an 80% threshold — closer to the reliability a production environment actually needs — the numbers collapse:

| Model | 50% time horizon | 80% time horizon |
| :-- | :-- | :-- |
| Claude Opus 4.5 | About 4 hours 53 minutes | About 49 minutes |
| Claude Opus 4.6 | About 12 hours | About 1 hour 10 minutes |

Read that again. Claude Opus 4.6 can handle a roughly twelve-hour task if you accept that it will fail half the time. Require an 80% success rate, and you are back to an hour-long task.

Imagine a car capable of 300 kilometers per hour whose brakes work only half the time. Would you drive it at 300? Probably not. You would stay near the speed at which you were confident it could stop. The gap between “the demo completed” and “production can depend on it” is not a small adjustment. It is an order of magnitude.

That is the reliability cliff.

METR’s own caveats matter here. The uncertainty intervals around individual model estimates are wide, especially for long tasks. The benchmark also concentrates on well-specified, automatically scored software engineering, machine learning, and cybersecurity tasks with relatively clean context. A twelve-hour time horizon does not mean twelve hours of an engineer’s real job can simply be replaced.

Even with those boundaries, the reliability cliff maps directly onto Part 4. Running a pipeline for 5,000 companies is not one hour-long task that needs to succeed once. It is thousands of tasks that all need to run reliably, with failure rates multiplying across steps. If each step succeeds 80% of the time, a ten-step workflow completes correctly only 10.7% of the time. At 50% per step, the final probability is roughly 0.1%.

It is like passing through ten security gates, each with an 80% chance of letting you through. That sounds acceptable until only one person in ten reaches the other side. Everyone else is stuck at a different gate, luggage scattered across the floor while security calls for assistance.

Our pipeline avoids this problem not because it is more intelligent, but because 90% of its steps are deterministic code. When inputs and external systems behave within known boundaries, those steps do not reconsider their behavior on every run. The LLM handles the classification step, where probabilistic output is acceptable, can be verified, and can be constrained by later mechanisms.

METR’s data explains precisely why this architecture works: confine the unreliable component to the part where uncertainty does not cause the whole system to lose control.

This is not merely a statistical curiosity. An agent that processes 80% of companies correctly but silently fails on the other 20% may be worse than useless for institutional work, because you do not know which 20% failed. The point of a production system is to succeed verifiably or fail explicitly: graceful degradation, not silent corruption.

The gap between 50% and 80% is the difference between an excellent demo and “I can entrust critical business data to this.”

## Two Anthropic Studies Both Say: Not Yet

Anthropic published two related labor-market studies across 2025 and 2026. They point in the same direction while measuring different things.

### Study One: Mapping Economic Tasks

The first study used millions of real Claude conversations to map how AI was actually being used across the economy. Its central findings:

**AI remains far below its theoretical ceiling.** Even computer programmers — among the occupations with the highest measured AI coverage, at roughly 75% of tasks — still had about a quarter of their tasks untouched. Most occupations were below one-third.

**57% augmentation, 43% automation.** The dominant pattern in professional AI use was collaboration between people and AI, not AI autonomously executing complete tasks. The “agent replaces the person” pattern was the minority, not the norm.

In other words, most people use AI as the prep cook chopping ingredients, not as the person left alone to run the entire kitchen.

### Study Two: A New Measure and Early Employment Evidence

The second study, *Labor Market Impacts of AI: A New Measure and Early Evidence*, was published on March 5, 2026. It introduced “observed exposure,” combining theoretical LLM capability with real usage data, then compared that measure with employment outcomes.

The headline result: from late 2022 through the study period, unemployment did not systematically increase in highly exposed occupations. The estimated employment effect was statistically indistinguishable from zero.

That does not mean AI has had no effect. The paper explicitly warns that enterprise adoption may lag, public usage data does not capture every internal deployment, and the available evidence remains an early signal.

For a general reader, the more important message is structural: higher exposure is associated with pressure on employment prospects, but not with a single uniform outcome.

On average, more exposed occupations have weaker projected employment growth. Individual occupations still diverge. Some roles look more directly substitutable and may feel pressure earlier. Others use AI to amplify output and may retain positive growth even with substantial exposure.

That is the heart of the leverage gap: high exposure does not imply one shared destiny. The question is not only whether you use AI. It is whether AI replaces your core value or amplifies it.

One terminology point matters. In the US Bureau of Labor Statistics occupational system, “computer programmers” and “software developers” are separate occupations. Programmers appear highly exposed in the research; software developers are a different category, and the two results should not be blended together.

Even within software development, the variance is large. Standardized implementation work performed against a fixed specification is more exposed. Work depending on domain context, architectural trade-offs, and expert judgment is less exposed.

There is another early signal worth watching, but it needs careful language. Within highly exposed occupations, the employment entry rate for workers aged 22–25 was roughly 14% below its pre-ChatGPT trend, while older workers did not show the same clear change. The paper stresses that the estimate is imprecise, may reflect different pre-existing trends, and cannot establish that AI caused the decline.

Still, the possibility deserves attention: AI may not have replaced experienced engineers, but it may be reducing the opportunities through which new engineers become experienced. Part 6 will return to this.

Taken together, the two studies offer one key insight: autonomous task execution — the mode promised by agents — is still not the dominant pattern of professional AI use today. Augmentation is.

That puts the pipeline discussed in this series in an interesting position. The engineer designing the architecture is augmentation. The LLM performing classification inside that architecture is automation applied to the one task where it fits.

More interestingly, high exposure may mean not only higher substitution risk but stronger augmentation leverage. The important work is the architecture around the AI, not the AI alone.

That is what the data says. But which frameworks explain why the numbers look this way? Karpathy’s Software 1.0/2.0/3.0, the SWE-CI long-term maintenance benchmark, and the long-tail problem all point in the same direction.

Next: Part 5B — What the Research Actually Says: The Frameworks.

## Series Map

| Part | Core idea |
| :-- | :-- |
| 00 — Introduction | Why this series exists |
| 01 — The Impossible Task | Where everything started |
| 02 — Where 7,400+ Lines Came From | How the pipeline snowballed |
| 03A — Brain and Body | LLM = 10% brain, code = 90% body |
| 03B — Six Simple-Looking Problems | Edge cases that break agents |
| 04 — An Honest Comparison | Pipeline vs. agents, by the numbers |
| **05A — What the Research Says: Data** | **You are here** |
| 05B — What the Research Says: Frameworks | The “why” behind the data |
| 06 — The Leverage Gap | Who benefits from AI, and who does not |
| 07 — Context Accumulation | What agents never learn |
| 08A — The Delegation Problem | Why you cannot simply throw it over the wall |
| 08B — The Autonomy Spectrum | Finding the right level |
| 09 — The Other Extreme | When skepticism becomes paralysis |
| 10 — Two Rooms | Demo enthusiasts vs. domain skeptics |
| 11 — The Evidence | The pipeline as evidence |
| Bonus — The Counterargument | AI argues against the entire series |
| Bonus — Standing in the Middle | The thought that arrives in the middle of the night |

## References

1. METR. [“Measuring AI Ability to Complete Long Tasks.”](https://metr.org/time-horizons/) v1.1, updated May 2026.
2. Handa, K. et al. [“Which Economic Tasks are Performed with AI? Evidence from Millions of Claude Conversations.”](https://arxiv.org/abs/2503.04761) arXiv:2503.04761, 2025.
3. Massenkoff, M. & McCrory, P. [“Labor Market Impacts of AI: A New Measure and Early Evidence.”](https://www.anthropic.com/research/labor-market-impacts) Anthropic, 2026.
