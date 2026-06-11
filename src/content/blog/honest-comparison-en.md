---
title: 'Part 4: An Honest Comparison — Pipeline vs. Agents, by the Numbers'
description: 'A side-by-side comparison of pipelines and agents: cost, speed, completeness, debuggability, and how nondeterminism compounds at scale.'
pubDate: '2026-06-08T12:00:00Z'
heroImage: '../../assets/series-04-honest-comparison-illustration.jpeg'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[Previous: Part 3B — Six “Simple” Problems That Break Agents.](/blog/agents-destroy-orchestration-en/)

[阅读中文版。](/blog/honest-comparison-zh/)

The same task costs a pipeline a couple of dollars and an agent hundreds — if the agent finishes at all.

The previous essay covered six problems that look simple: link extraction, query parameters, stopping rules, PDF handling, PDF deferral, and `robots.txt` compliance. Each one looks easy from the outside and breaks immediately on real websites. The pipeline writes the solution into code and keeps it.

The first three essays told the story: how the classifier grew seven layers (Part 2), where LLMs are irreplaceable in the 10% that needs semantic judgment (Part 3A), and how six “simple problems” become production nightmares (Part 3B).

This essay does one thing: put the two approaches side by side and compare the numbers.

Earlier essays used a brain-and-body metaphor for the pipeline. Classification is the brain. Orchestration is the body. LLM tokens are food. The human brain is only about 2% of body weight but consumes roughly 20% of its energy. The pipeline has a similar shape: the 10% classification layer consumes most of the LLM cost.

The problem is that in the agent approach, you have to feed not only the brain but every muscle in the body. And the two systems eat differently. The pipeline is disciplined: it controls the diet and counts every calorie. The agent binge-eats: it consumes context whenever it feels hungry and does not know when to put down the fork.

## Feeding the Brain

Part 2 described the seven-layer classification architecture: four-level keyword scoring, domain prefix trees, score inheritance, eleven-level PDF scoring, and iterative caches. Before anything reaches the LLM, those engineering layers filter out 80–90% of URLs.

| Cost item | Deterministic pipeline | Agent, best case |
| :-- | :-- | :-- |
| Material sent to the LLM | 30–50 ambiguous groups after six filtering layers | Hundreds to hundreds of thousands of raw URLs |
| First-round tokens | About 5–15K, ambiguous items only | Hundreds of thousands to millions |
| Second-round tokens | About 70% saved through iterative caching | Starts over and pays the full cost again |
| Third-round tokens | About 90% saved | Pays the full cost again |
| Classification cost | About $0.10–0.30 per company | Starts around $5 per company, with no clear ceiling |

Why such a large difference? Before the LLM speaks, the pipeline has already handled most URLs through the domain prefix tree, score inheritance, and scoring rules. Only the genuinely ambiguous remainder needs semantic judgment.

The agent does not have those filtering layers. It has to push all URLs, together with page context, into the model and classify them by force.

One clarification: the agent column assumes a reasonably intelligent implementation — batched URLs, a large context window, and a strong model. This is not the naive “one model call per URL” version. Even with those favorable assumptions, classification alone starts tens of times more expensive.

A small company may expose a few hundred URLs. A multinational group may expose tens or even hundreds of thousands. Agent cost grows roughly with URL count. The pipeline’s LLM cost stays almost flat because ambiguity, not volume, determines how much reaches the model.

And remember: this table compares only the brain, the cleverest 10% of the pipeline — deciding what is ESG content and what is not.

The other 90% is the physical work described in Part 3B: link extraction, parameter normalization, stopping rules, PDF handling, deferral, and `robots.txt` compliance. In the pipeline, that is deterministic code with close to zero marginal model cost. If an agent also has to cover that 90%, assuming it can, every part requires more LLM calls to “think.”

The full-process table makes the gap harder to ignore.

## Feeding the Body

The brain has eaten. The body is still hungry. The six problems from Part 3B are the body. The pipeline’s body runs on deterministic code and consumes no tokens. In an agent, every muscle needs to be fed through the LLM.

| Stage | Pipeline | Agent |
| :-- | :-- | :-- |
| Link extraction and deduplication | Deterministic code, about $0 | LLM judgment about deduplication, about $1–3 |
| Query-parameter normalization | Rule engine, about $0 | Skip it and risk loops; do it and incur model cost |
| Stopping rules | Hard-coded budgets, about $0 | No natural ceiling; runs until the budget is gone |
| PDF download and retries | Deterministic code, about $0 | Every failure requires another LLM decision |
| PDF deferral and ordering | Deterministic scheduling, about $0 | No built-in concept of deferral |
| `robots.txt` compliance | Deterministic prefilter, about $0 | Reinterpreted on every run |
| Classification | $0.10–0.30 | Starts around $5, with no clear ceiling |
| Browser scheduling and bot defenses | Preflight plus fallback cascade, about $0.20 | Independent judgment for each page |
| **Total per company** | **$0.50–2.00** | **$50–200+** |

More than 90% of the pipeline’s $0.50–2.00 is cloud compute and browser resource cost. The LLM is a small part. The agent’s $50–200+ estimate is still optimistic: it assumes no parameter loop, no silent PDF failure, and no endless collection of news pages.

The query-parameter loop on a large enterprise website described in Part 3B burned for several days in a single task. Its LLM-call cost exceeded the rest of the tasks combined.

Now multiply by 5,000 companies:

| Portfolio scale | Pipeline | Agent |
| :-- | :-- | :-- |
| Total cost for 5,000 companies | $2,500–10,000 | $250,000–1,000,000+ |
| Total time | 1–2 weeks in parallel | Months, if it finishes |

These numbers are not invented from nowhere. The pipeline order of magnitude comes from actual cloud-provider bills. The agent estimate extrapolates reasonably from the failure modes in Part 3B: query-parameter loops, silent PDF failures, and unbounded news collection.

## But the Real Cost Is Not Money

The deterministic pipeline does not merely hope that the LLM notices `/content/dam/2024/report-en.pdf` is ESG content even though its path is a generic content-management path.

It knows because the sustainability page that linked to it propagated its classification. Score inheritance. Deterministic. Reliable.

An agent looking at 1,000 flat URLs has to work that relationship out from scratch. And it probably will not. The portfolio manager’s chatbot experiment in Part 1 already showed the problem: it retrieves what is easy to find, not what is complete.

That is the real cost. The only reason this project exists is to let an institutional investor see the complete ESG information for every company and make better investment decisions.

An agent will probably give you something. But completeness can never be guaranteed. When managing portfolios worth billions or tens of billions, missing a key sustainability report or overlooking a material environmental-risk disclosure has a hidden cost far greater than any LLM bill.

The difference between $0.50 and $2 is just a number. The loss from one wrong investment decision is an order of magnitude.

## Nondeterminism Compounds at Scale

For one company, an agent may perform fairly well. Across 5,000 companies, the difference is not additive. It is multiplicative.

Assume each agent decision has a 95% probability of being correct. That is already generous. A single company’s collection flow contains roughly 100 decision points: link classification, parameter handling, PDF decisions, stopping time, and so on.

```text
Probability of a perfect run: 0.95^100 ≈ 0.6%
```

That means only about 30 out of 5,000 companies would be processed without any error.

The Part 3B examples make the mathematics concrete:

- A query-parameter loop can trap the agent on any run.
- A PDF can fail silently while the agent believes it was collected.
- News collection has no brake and continues until the budget is exhausted.

These are not occasional mistakes. They are structural defects. Every run has some probability of triggering them, and when they occur, you may not know.

The deterministic pipeline behaves differently: same input, same behavior. Logic that works on the first company works the same way on the 5,000th.

| Dimension | Pipeline | Agent |
| :-- | :-- | :-- |
| Consistency | Same input → same behavior | Each run may differ |
| Reproducibility | 100% | Cannot be guaranteed |
| Debugging | Read logs and trace code | “Why did the agent skip this link?” |
| Completeness | More than 98% of discoverable pages | Unknown and not reproducible |

For ESG data that drives institutional investment decisions, “we probably collected most of it” is not a product. The portfolio manager’s conclusion in Part 1 was completeness, consistency, auditability, and reliability. The chatbot failed on all four. Agents inherit the same problems.

## Compare It with the Most Popular Agent

OpenClaw — one of the most popular AI-agent projects on GitHub — includes browser control, code execution, and messaging integrations. It is a useful benchmark for the agent approach.

Do not misunderstand the argument. OpenClaw can be a very good productivity tool for software engineers. It augments people who already know what they need and how to verify it.

The Part 3A metaphor was that the LLM is the expensive consultant and the engineer is the project manager. OpenClaw can double the project manager’s productivity. But the project manager cannot be absent.

The problem begins when someone claims it can replace the pipeline. Look at the numbers:

| Dimension | Pipeline | OpenClaw |
| :-- | :-- | :-- |
| Pages per company | 300+ through systematic traversal | Context fills after roughly 20–30 pages |
| Concurrency | 15–100 parallel requests | One page at a time |
| Bot-defense handling | Preflight plus Playwright/Chrome cascade | One browser, no fallback |
| State | Persists across iterations | Lost when context overflows |
| Stopping strategy | 200-news-item cap plus adaptive thresholds | None; runs until the budget is gone |
| PDF handling | Deferred, ordered, atomically saved, retried | Click the link and hope it lands |
| `robots.txt` | Preflight check for every URL | Not checked, or reparsed each time |
| Cost per company | $0.50–2.00 | $50–200+ |
| Completeness | More than 98% of discoverable pages | Unknown and not reproducible |

The $50–200+ estimate is not sensational. Part 3B explains the mechanism:

- No parameter normalization → loops that burn tokens.
- No stopping rules → unbounded news collection.
- Silent PDF failure → repeated retry and verification loops.
- No deferral strategy → too many PDFs consume the budget too early.

Each one can add another $5–30 by itself. Together, they reach this order of magnitude.

## One-Off vs. Systematic

“What is Shell’s latest sustainability report?”

OpenClaw can answer in 30 seconds. This is exactly what agents are made for, and they do it well.

“Systematically extract every ESG page from 5,000 corporate websites with more than 98% completeness, auditability, and reproducibility.”

That is not a question. It is a production line.

The distinction is exactly what the portfolio manager discovered in Part 1: for one company and one document, it feels like magic. Across thousands of companies, completeness, consistency, and cost all collapse.

## The Right Composition

It is not “agent versus pipeline.” Part 3B already made the point: the agent is the interface; the pipeline is the engine.

```text
You in WhatsApp: “Run the ESG collector for Saint-Gobain.”
OpenClaw → calls: python run_one_company.py --name "SAINT-GOBAIN"
OpenClaw → “Done. 312 pages, 18 PDFs. 2 failures (IP blocked).”
```

The agent understands intent, formats the command, and reports the result. The pipeline executes tens of thousands of lines of deterministic code. Nobody loses. Both sides win.

## “But Agents Can Write the Code”

This is the most common objection, and it deserves a serious answer.

In fact, most of this pipeline’s code was written with Claude Opus. Development productivity increased by roughly 5–10 times. If every line had been written manually, the project would have taken much longer. AI’s ability to write code is no longer scarce.

But the biggest lesson is precisely this: AI does not automatically see all the details.

None of the Part 3B problems — JavaScript rendering on certain sites, nonstandard link tags, the parameter loop on a large enterprise website, silent PDF failure — was discovered by Claude on its own.

The pipeline first failed on a real company. Then the developer described the problem clearly enough for Claude to write the fix. Hidden requirements, unspoken edge cases, and problems that appear only after running real data are invisible to AI, or prohibitively expensive for it to discover independently.

This is close to the lesson behind OpenAI’s harness engineering and Karpathy’s autoresearch: AI still needs to be harnessed by people. The quality of the harness shapes the quality of the output.

And the complexity of this project means that harnessing it requires more than general programming skill. It requires domain experience, frontier knowledge, and intuition accumulated through hundreds of failures.

Claude writes code quickly. The decision about what code needs to exist is still made by a human today.

## Where Each Approach Fits

Looking back across the series, the boundary is fairly clear.

Agents fit:

- **One-off tasks:** “Summarize this page.” “Find the CEO’s name.” Cases where building a pipeline costs more than a few LLM calls.
- **Exploration:** “What ESG information is on this website?” The discovery stage before a systematic method exists.
- **Code generation:** Agents write deterministic pipeline code rather than replacing it at runtime. Claude Code wrote much of this pipeline, but the runtime does not need it.
- **Low-risk, high-variety work:** Customer service, drafting, and code review, where 95% accuracy may be acceptable.

Agents do not fit:

- **High-throughput data pipelines:** Hundreds of thousands of pages need deterministic processing. Each of Part 3B’s six problems requires a deterministic solution.
- **Reliability above 99%:** Nondeterminism compounds. The mathematics above already shows it.
- **Stateful multi-step workflows:** Agents lose context; state machines do not. PDF deferral requires state across the entire collection cycle.
- **Zero-tolerance compliance:** `robots.txt` is not “try to comply.” Legal needs 100% auditability.
- **Microsecond decisions:** Batch size, timeouts, and retries. Code executes in microseconds; an LLM round trip takes seconds.

Everything above comes from code written in practice and failures encountered firsthand. What does the research community — not social media, not venture capital — say about it?

Next: [Part 5A — What the Research Actually Says About AI Replacing Engineers.](/blog/research-data-en/)
