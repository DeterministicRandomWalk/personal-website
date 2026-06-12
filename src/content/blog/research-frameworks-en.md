---
title: 'Part 5B: What the Research Actually Says About AI Replacing Engineers'
description: 'Software 1.0/2.0/3.0, verifiability, context engineering, jagged intelligence, and SWE-CI: frameworks that explain the data.'
pubDate: '2026-06-12T12:00:00Z'
heroImage: '../../assets/series-05b-research-frameworks-illustration.jpg'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[Previous: Part 5A — What the Research Says: The Data.](/blog/research-data-en/)

[阅读中文版。](/blog/research-frameworks-zh/)

The data showed a reliability cliff and a world in which augmentation still outweighs automation. Now we need the frameworks that explain those results, and what they mean for engineering.

Part 5A covered METR’s reliability cliff: the gap between a demo and production is close to an order of magnitude. Anthropic’s labor-market research found that real-world AI use is still dominated by augmentation rather than automation, with no systematic increase in unemployment yet observed.

The data is on the table. Now let us understand what it means.

## The 30-Second Version

1. AI works best on tasks whose outputs you can verify quickly, such as classification. Architectural decisions have feedback loops that are too slow to hand over directly.
2. A working demo is not a working product. Autonomous-driving demonstrations were impressive more than a decade ago; crossing the long tail of reliability is still ongoing.
3. AI capability is jagged. It can outperform an expert on one task and make an elementary mistake on the next, and you cannot reliably predict which will be which.
4. On long-term code maintenance, even the strongest models sustain zero regressions only around half the time. Fixing one feature may break another.
5. Benchmarks measure whether a model can write code. The hard part of engineering is knowing what should be written, and what should not.

## Deterministic Logic or AI Judgment? Three Software Paradigms

Andrej Karpathy has spent several years developing a useful framework for understanding AI’s role in software.

Software 1.0 is explicit code: you write the rules, and the computer follows the recipe step by step.

Software 2.0 is learned weights: you organize data and define an objective, and an optimizer discovers the rules.

Software 3.0 is the term Karpathy used in his 2025 YC AI Startup School talk for programming LLMs through natural language: prompts, system instructions, and tool definitions become a form of code.

The framework does not require 3.0 to replace 1.0 and 2.0. The three paradigms coexist, and engineers decide which belongs in each part of a system. In engineering language, the question becomes: which parts require deterministic guarantees, and which are better served by AI’s semantic judgment?

Our pipeline combines all three:

```text
Software 1.0 (code):    batching, retries, escalation, tracking  -> guarantee behavior
Software 2.0 (weights): pretrained semantic understanding       -> under the hood
Software 3.0 (prompts): "Is this URL related to ESG?"            -> direct the model
```

Strictly speaking, we do not train the model ourselves. We use someone else’s 2.0 model and direct it with 3.0 instructions. At the application layer, the pipeline is essentially a 1.0 + 3.0 system.

The LLM is irreplaceable. No pile of regular expressions matches its ability to judge whether a sustainability-report link leads to genuine disclosure or greenwashing copy. But most of the system’s value comes from Software 1.0: control, recovery, deduplication, budgets, and traceability.

## What Goes to AI and What Stays in Code? Verifiability

Once we have three paradigms, the next question is practical: how do we decide which one a task needs?

Karpathy’s essay “Verifiability” offers a highly useful criterion: how easy is it to verify the output?

Software 1.0 automates what is **specifiable**. You can write the exact rule.

Software 2.0 and 3.0 are strongest where the answer is **verifiable**. You may not be able to write the complete rule, but you can quickly inspect the result: Is this a cat? Does this translation sound right?

The difficult remainder contains tasks that are neither easy to specify nor easy to verify. Much of real engineering lives there.

Apply this criterion to our system.

Was this URL classified correctly? Verifiable. A person can inspect it in seconds, so using an LLM for classification works.

Is the architecture of the pipeline correct? Not easily verifiable. You may need to run all 5,000 companies, then compare cost, completeness, and failure rates over several weeks. An architectural decision is not complete merely because an LLM produced a plausible explanation.

Is the browser fallback strategy optimal? The feedback loop may take weeks. An LLM cannot patiently remain inside that loop. Its patience resembles that of a three-year-old waiting at a supermarket checkout.

> **Takeaway:** Give AI tasks whose outputs can be verified quickly. Keep slow-feedback decisions, whose mistakes propagate over time, inside deterministic systems and human judgment.

## Once You Choose AI, How Do You Use It? Context Engineering

After deciding which tasks belong to the LLM, the next question is how to delegate them well.

Software 3.0 can sound like “just write a prompt.” Public discussion quickly moved toward the broader idea of context engineering. In 2025, Tobi Lütke helped popularize the phrase, and Karpathy described it as the art and science of filling a limited context window with exactly the right information for the model’s next step.

Software 3.0 is the paradigm. Context engineering is one of the core crafts required to implement it.

In our pipeline, context engineering is concrete engineering work. We have three different LLM calls, each serving a different purpose and therefore receiving different material:

- When evaluating a path, the LLM sees the URL path plus signals aggregated from page context.
- When evaluating a cross-path link, it sees the link and the high-confidence ESG parent page where the link was discovered.
- When evaluating deep child pages, it receives a batch of URLs and instructions designed for pattern recognition across the batch.

Three calls. Three contexts. Three sets of constraints. They answer three different questions.

This is not prompt cleverness. It is system design.

> **Takeaway:** The prompt is only the entry point. The real Software 3.0 skill is context engineering: assembling exactly the signals each LLM call needs, neither more nor less.

## Even Then, Where Is the Boundary? The Demo Gap and Jagged Intelligence

We now have a framework, a selection criterion, and an implementation practice. Two traps remain in real-world AI performance.

### The Gap from Demo to Product

Agent enthusiasts often assume Software 3.0 can carry the system all the way. Autonomous driving is the best warning. Early demonstrations were impressive more than a decade ago, but production still has to cross the long tail of reliability.

Making one perfect dish for Instagram is a demo. Running a restaurant kitchen every night for a year is a product.

Karpathy’s writing and talks about Autopilot, partial autonomy, and human-machine collaboration repeatedly return to the same warning: producing the demo does not mean the long tail and the reliability threshold have been crossed. His timeline for agents is similarly cautious. He has called this the “decade of agents,” not the “year of agents.”

### Jagged Intelligence

Even within areas where AI is strong, performance is not uniformly reliable. The capability boundary is jagged: superhuman on one task, suddenly brittle on a neighboring one.

A Harvard Business School and BCG study quantified the same pattern with 758 consultants. On tasks inside the AI frontier, people using AI completed 12.2% more tasks, worked 25.1% faster, and produced higher-quality results. On a complex business task deliberately placed outside the frontier, AI users were 19 percentage points less likely to reach the correct answer.

In practice, the model may write flawless data-processing logic and then cite a regulation from the wrong jurisdiction with such confidence that you will not question it unless you already know the field.

It may recommend an architecture that works perfectly across ten companies and quietly collapses at 5,000 because some anti-automation defenses appear only after request volume accumulates.

Intelligence is jagged: spiky and unpredictable.

That is why “give it more autonomy” is not a complete strategy. Our pipeline confines the LLM to a narrow band where its semantic judgment consistently beats rules. Everything else sits inside deterministic code, where the jagged boundary cannot destabilize the system.

> **Takeaway:** The distance from demo to product is measured in years. AI’s capability boundary is not smooth; it is jagged and difficult to predict.

## How Hard Is Long-Term Maintenance? The SWE-CI Benchmark

These frameworks explain where AI hits boundaries. Two questions remain: how hard is long-term system evolution, and why is engineering judgment difficult to automate?

SWE-CI does not show that models cannot write code. It shows that long-term evolutionary stability is much harder than producing a single patch.

Released in March 2026, SWE-CI measures something most coding benchmarks ignore: long-term code maintenance.

The question is not whether a model can write the code once. It is whether repeated changes make a system progressively better rather than progressively worse. Can an agent behave like a developer working through continuous integration, iterating on a living codebase without breaking existing behavior?

- 100 long-horizon evolution tasks.
- An average historical span of about 233 days.
- Up to 20 iterative rounds per task.
- Roughly 10 billion tokens consumed across the evaluation.

In the official experiments, 10 of 12 frontier models had a zero-regression rate below 0.25. Only Claude Opus 4.5 and Claude Opus 4.6 exceeded 0.50.

Even the strongest models sustained zero regressions only around half the time under an evaluation designed around long-term stability. That remains far from unsupervised delegation.

What does the benchmark show? Long-term maintenance and continuous-integration-style evolution are much harder than writing a function once. The direction is persuasive: agents struggle not only with individual tasks, but with keeping systems stable as they change. Production code must change every week.

What does it not show? The benchmark is anchored to historical repository tasks, reference commits, and tests. It primarily measures correctness along an established evolution path. An agent that finds a different but equally valid architecture may still fail the reference tests. The benchmark does not prove that models can never maintain code, nor that every deviation from the historical path is inferior.

Our pipeline has gone through dozens of evolution cycles. PDF handling was redesigned three times. Score inheritance arrived months later. Query-parameter normalization emerged from a specific production failure. Every change required understanding the full system state, and the sequence was not designed in advance. It emerged from production feedback.

SWE-CI is trying to measure precisely this kind of evolutionary stability, and even the strongest models remain far from fully dependable.

> **Takeaway:** Writing code once and keeping a living system healthy are different jobs. Even the strongest models sustain zero regressions only around half the time. “Can write” does not mean “can raise.”

## Knowing What to Write Is Harder Than Writing It

Engineering judgment is difficult to automate not because code is difficult to type, but because feedback is slow, context is thick, and mistakes propagate through time.

This is the key point most benchmarks ignore. Coding benchmarks ask whether a model can write a function. SWE-bench asks whether it can fix a bug. METR asks whether it can finish a task. They do not directly ask whether it knows which function should exist, which bugs matter, or which task deserves priority.

It is like testing whether someone can swing a hammer and concluding that they can build a house. Or watching a robot execute a choreographed dance and assuming it can enter a kitchen tomorrow, wash dishes, and handle every unplanned event on a factory floor. The dance is choreographed. Kitchens and factories are not.

Our pipeline was difficult to build not because each function was complex. Any senior Python developer could write most of the functions in isolation. The difficult part was knowing:

- Browser handling needed several distinct paths rather than one generic strategy, because production websites use more anti-automation patterns than expected.
- Score inheritance through the domain tree would remove roughly 60% of LLM calls, because ESG content clusters along high-confidence paths.
- PDF handling should be deferred instead of mixed into page discovery, because downloading during crawling saturates connections and interrupts the discovery loop.
- Query-parameter normalization can reduce hundreds of apparent URLs to the genuinely distinct pages, because some enterprise sites attach temporary session parameters to every link.

Then there is the “boring” code that exists only for the final 5% of edge cases: age-gate detection, cookie-wall handling, PDF filename scoring, and query-parameter normalization.

The first 80% is easy. The next 15% is hard. The final 5% decides whether a production system can be trusted.

The 2025 Stack Overflow Developer Survey reflects the same tension. Eighty-four percent of respondents use or plan to use AI tools, yet 46% distrust the accuracy of AI output, compared with 33% who trust it. Adoption is rising while the trust gap remains.

These are engineering judgments. For context-heavy trade-offs with long feedback loops, general models have not been trained or evaluated on data perfectly aligned with your objective function. They may have seen fragments of the relevant patterns, but they were not optimized for the complete trade-off involved in collecting ESG disclosures from 5,000 companies at institutional scale.

This is the gap revealed by METR’s numbers. A model may complete a twelve-hour benchmark task with roughly a 50% chance of success. Engineering judgment is not the completion of one task. It is hundreds of architectural decisions made over months, each interacting with the others. One bad decision can propagate through the entire system.

You need near-perfect judgment on decisions that may not appear in any training set.

> **Takeaway:** Benchmarks measure whether the model can swing the hammer. Building the house depends on knowing which wall should go up first. Engineering judgment has feedback loops measured in months, and that remains one of AI’s largest blind spots.

## Where the Evidence Converges

Eight lines of evidence converge on the same conclusion.

| Source | Key finding | Pipeline implication |
| :-- | :-- | :-- |
| METR | The reliability gap between 50% and 80% is close to an order of magnitude | Confine the LLM to steps where local failure can be detected and absorbed |
| Anthropic | Professional AI use is dominated by augmentation, not automation | Build a system around the LLM rather than asking the LLM to be the whole system |
| Karpathy’s 1.0/2.0/3.0 | The answer is composition: deterministic code, learned weights, and natural-language instructions | The deterministic 90% is not overhead; it is the product |
| Karpathy on verifiability | Tasks with quickly verifiable outputs fit AI best | Give classification to the LLM; leave architecture to long feedback loops and human judgment |
| The demo gap | Reliable products must cross the long tail | An agent is a component, not a complete system |
| Harvard/BCG | Strong gains inside the frontier; 19-point accuracy loss outside it | Keep the LLM where its capability spikes work in your favor |
| SWE-CI | The strongest models achieve zero-regression rates around one half | Long-term production evolution still needs human judgment |
| Production experience | Engineering feedback loops are measured in months | The final 5% determines whether the system truly works |

None of this research says agents are useless. Together, the evidence suggests that agents are components, not yet systems.

They are powerful components. The LLM classification inside our pipeline is genuinely irreplaceable. No amount of engineering matches its semantic judgment.

But a component without a surrounding system is a demo. A system without the right component is incomplete. Both have to be built, and engineers have to know which is which.

Putting an engine in a car does not mean you have built a car. But without an engine, the car is going nowhere.

At this point, the frameworks and the data point to the same conclusion: AI and engineering must coexist. Deterministic structure constrains probabilistic judgment and makes randomness reliable. That is the practical engineering meaning of “Deterministic Random Walk.”

The name has another layer too. The turns in life that appear random may still be governed by something more stable underneath. At least, I choose to believe they are.

The gap between people who can combine AI and engineering and people who know only one side is not shrinking. It is widening faster. And this is not merely a technical question. The research points toward a larger one: in an era of rapidly changing tools, what should we embrace, and what should we preserve?

That is the real leverage gap.

Next: Part 6 — The Leverage Gap: Who Actually Benefits from AI.

## Series Map

| Part | Core idea |
| :-- | :-- |
| 00 — Introduction | Why this series exists |
| 01 — The Impossible Task | Where everything started |
| 02 — Where 7,400+ Lines Came From | How the pipeline snowballed |
| 03A — Brain and Body | LLM = 10% brain, code = 90% body |
| 03B — Six Simple-Looking Problems | Edge cases that break agents |
| 04 — An Honest Comparison | Pipeline vs. agents, by the numbers |
| 05A — What the Research Says: Data | METR’s reliability cliff and Anthropic’s labor research |
| **05B — What the Research Says: Frameworks** | **You are here** |
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

1. Karpathy, A. [“Software 2.0.”](https://karpathy.medium.com/software-2-0-a64152b37c35) 2017.
2. Karpathy, A. [“Verifiability.”](https://karpathy.bearblog.dev/verifiability/) 2025.
3. Karpathy, A. [“Software Is Changing (Again).”](https://www.youtube.com/watch?v=LCEmiRjPEtQ) YC AI Startup School, 2025.
4. Zan, D. et al. [“SWE-CI: A Benchmark for Long-Term Code Maintenance in Real-World Software Repositories.”](https://arxiv.org/abs/2603.03823) 2026.
5. Dell’Acqua, F. et al. [“Navigating the Jagged Technological Frontier.”](https://www.hbs.edu/ris/Publication%20Files/24-013_d9b45b68-9e74-42d6-a1c6-c72fb70c7282.pdf) Harvard Business School, 2023.
6. Willison, S. [“Context Engineering.”](https://simonwillison.net/2025/Jun/27/context-engineering/) 2025.
7. Stack Overflow. [“2025 Developer Survey.”](https://survey.stackoverflow.co/2025/ai) 2025.
