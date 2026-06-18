---
title: 'Part 6: The Leverage Gap — Who Actually Benefits from AI'
description: 'AI has not made judgment less valuable. It has amplified it, and companies, engineers, and junior workers are being reordered around that new leverage gap.'
pubDate: '2026-06-18T12:00:00Z'
heroImage: '../../assets/series-06-leverage-gap-illustration.jpg'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[Previous: Part 5B — What the Research Says: The Frameworks.](/blog/research-frameworks-en/)

[阅读中文版。](/blog/leverage-gap-zh/)

The first five essays established one point: current AI cannot reliably build this kind of production system autonomously, but under expert direction it can perform a large share, sometimes most, of the execution work that can be clearly constrained.

The bottleneck is moving from coding ability toward the judgment of the person directing the AI. That creates a new gap. People with that judgment can use AI to accomplish work that once required a team. People without it may find that demand for their work is compressed by a smaller number of AI-amplified experts.

Companies are already reorganizing around this gap. Sometimes the decision rests on demonstrated productivity. Sometimes it is an advance bet on future capability. Sometimes ordinary cost cutting is simply repackaged as AI strategy.

## The Half of the Story We Have Not Told

The first five essays repeatedly emphasized what AI cannot do. This one begins with a fact they did not explore: how much work AI actually performed in the pipeline.

At runtime, the LLM handles roughly 10% of the work: link classification, relevance decisions, and content scoring. The other 90% is browser fallback, retry logic, PDF handling, state management, and error recovery.

That sounds like “AI did 10%; a person did 90%.”

That is not what happened.

Much of the deterministic 90% was also written with AI assistance: browser cascades and fallback paths, retry budgets, PDF-scoring rules, and state transitions. It was not written autonomously. It was written under the direction of an engineer with system experience:

- Which edge cases appear on the 500th company website?
- Which retry strategies collapse at scale?
- Which plausible architectural choices become technical debt months later?

AI performed the execution. Direction, constraints, stopping conditions, and architectural choices came from human judgment.

The real picture is therefore not “AI did 10%; humans did 90%.” It is:

> Under expert direction, AI completed a large share, perhaps most, of the execution work that could be clearly constrained — after someone first defined the boundaries.

That changes the equation. AI’s impact is not limited. It is enormous. But it has a precondition: the person directing it needs sufficient judgment.

Without that precondition, AI is an autocomplete system that makes confident mistakes. With it, one person plus AI can deliver outcomes that previously required a larger team.

That is the source of the leverage gap.

The question is not only whether AI can replace people. It is who can direct AI. People with that ability gain enormous leverage. Roles built mostly from standardized execution with limited contextual judgment face growing pressure.

Not because AI replaced everyone, but because it made a small number of people with judgment unusually powerful.

## Block: A Smaller Team and a Higher Share Price

In February 2026, Block announced more than 4,000 job cuts, close to 40% of its workforce.

Jack Dorsey wrote publicly:

> “A significantly smaller team, using the tools we’re building, can do more and do it better.”

The company also emphasized moving faster with smaller, more concentrated teams using AI to automate more work. After the announcement and earnings release, Block’s shares rose by roughly a quarter in after-hours trading.

The organizational language matters. It was not “the existing team plus new tools.” It was “a smaller team plus stronger tools.”

Management was reorganizing around two questions:

1. Which work can AI amplify?
2. Which judgment remains scarce?

Dorsey predicted that more companies would reach similar conclusions within a year.

## A Chain Reaction, but Not Every Layoff Is an AI Layoff

A series of related but not identical cases followed:

- **Atlassian** announced about 1,600 job cuts. Its official explanation explicitly described restructuring to self-fund investment in AI and enterprise sales while changing the skills mix and improving profitability.
- **CrowdStrike** cut about 500 roles. Its CEO called AI a “force multiplier” and said it was flattening the company’s hiring curve.
- **Chegg** announced a reduction of roughly 45% of its workforce. The company directly cited the “new realities of AI” and declining search traffic.
- **Pinterest** disclosed in an SEC filing that a restructuring would affect less than 15% of employees and explicitly reallocate resources toward AI-focused roles, teams, and product capabilities.
- **Amazon** announced organizational changes affecting roughly 16,000 roles in January 2026 while continuing major investment in strategic areas and AI infrastructure. Amazon’s official explanation emphasized reducing layers, increasing ownership, and removing bureaucracy; it did not describe those jobs simply as being directly replaced by AI.

These cases should not be compressed into one story.

Some companies tie AI directly to job cuts. Some reduce headcount while investing more in AI. Some have businesses directly disrupted by generative AI. Others are carrying out familiar organizational reductions during an AI investment boom.

The shared direction still matters. More management teams are no longer treating “the current job structure plus AI tools” as the default. They are reassessing headcount, skill mix, and organizational layers.

Anthropic’s labor research has not found a systematic increase in unemployment, but it identified an early signal worth watching: entry into AI-exposed occupations may be becoming harder for workers aged 22–25. The authors explicitly call it suggestive evidence and note several alternative explanations.

The pattern is not simply “AI replaces humans.” It is a more specific filter:

> Is your work primarily the independent execution of standardized tasks, or contextual judgment under uncertainty?

The first category has always faced pressure. Outsourcing did it. Process automation did it. AI has increased the acceleration by an order of magnitude.

## Oracle: When Capital Reallocation Becomes the Story

Oracle requires more careful language.

Analysts and media reports in early 2026 estimated that potential job cuts could reach 20,000 to 30,000 as the company sought cash flow for intensive AI data-center investment. Later reporting confirmed that large-scale reductions were occurring, but Oracle did not publicly confirm a final total. The highest estimate should not be treated as established fact.

Even with that uncertainty, the case exposes a mechanism deeper than “AI directly replaced these jobs.” A company can reduce labor costs and reallocate capital toward AI infrastructure.

That is not evidence that a model has already taken over every affected employee’s work. It is a capital-allocation bet on future productivity:

- reduce current organizational cost;
- increase data-center, compute, and AI-product investment;
- bet on higher output per employee in the future.

Rather than saying employee cost was directly replaced by AI, it is more accurate to say the financial capacity released by the cuts was redirected toward an AI bet.

That is an inference from external reporting and analyst estimates, not Oracle’s own official wording.

This looks less like a temporary adjustment and more like a structural change in the definition of productivity. Companies are not only using AI to support existing teams. They are rebuilding organizations around a new leverage ratio: fewer people, each amplified more heavily, selected for judgment rather than pure execution volume.

## From Assistant to Executor

AI in 2023 looked more like an assistant. You wrote code; it suggested completions. A junior employee plus GPT-4 was still mostly a faster junior employee.

With stronger reasoning and coding models, the change has gradually become qualitative. AI no longer only completes. It implements:

- you describe the architecture; it generates code;
- you specify constraints; it proposes a solution;
- you review, test, correct, and iterate.

Compress the change into one sentence:

> AI is pushing organizations from “many people execute instructions” toward “fewer people set direction while tools perform more of the execution.”

For some standardized, repeatable software work that can be described through explicit constraints — maintenance scripts, standard CRUD applications, typical front-end pages, template-driven mobile apps — organizations are already treating AI as a reason to compress pure execution roles.

These are real jobs held by real people. The important variable is not only technical capability. It is management’s belief about which execution can be absorbed by tools, and that belief is not always correct.

When the next headline says that a company cut 500 engineers, first ask which roles were cut, what reason the company gave, and whether AI has actually assumed the work or merely supplied the strategic narrative.

The shift is not simply from “people write code” to “AI writes code.” It is from “many people execute instructions” to “a smaller number set direction and AI executes.” That changes which roles are central to an organization, and it will not wait for everyone to be ready.

## Rewriting Headcount Arithmetic

The pipeline itself is evidence of the leverage gap. With AI assistance, one person with judgment can handle a volume of work that previously needed broader team coordination.

The issue is not merely fewer people. Direction becomes the new bottleneck. People who can provide it gain leverage; people who cannot are more substitutable.

The gap also exists inside organizations, between “official automation” and the complexity of the real problem.

### The Institution’s Alternative

To put the pipeline into production, the project needed a managed environment capable of stable browser automation. An internal platform function suggested evaluating an existing, governance-approved visual automation tool and arranged a product demonstration.

It quickly became clear that the two systems solved different problems.

The tool was a proprietary graphical programming environment. Users assembled visual modules that navigated stable pages, clicked elements in fixed patterns, and saved results to specified locations.

For its intended purpose — repeatable, predictable workflows against stable internal pages — it was useful.

It was not designed to:

- discover and classify links across thousands of unfamiliar domains;
- handle heterogeneous anti-automation defenses;
- manage retry budgets and recoverable state;
- prioritize PDFs by relevance;
- fall back across browser paths;
- make semantic decisions in ambiguous cases.

This story is not told to mock the internal platform team. They offered a governed tool that solved a real problem, and it was reasonable within its operating boundary.

The story matters because it reveals another side of the leverage gap: many institutions’ approved toolboxes have not caught up with the complexity of the problems their business teams are trying to solve.

The outside world says agents will replace everything. Inside enterprises, official tools often remain reliable only for fixed, predictable workflows.

The people who fall into this gap — whose problems are too complex for institutional tools but who lack the engineering ability to build a system — are precisely the people most likely to reach for a general agent and hope.

## The Leverage Equation

Imagine a spectrum. One end contains data, quantitative methods, and engineering toolchains. The other contains domain knowledge, industry experience, and business judgment.

Most people spend much of their careers on one end because the barrier in the middle is high. An engineer who wants to understand ESG disclosure rules needs long exposure to the field. An investment professional who wants to build a production browser cascade has to begin with programming fundamentals.

AI is lowering the barrier.

It does not replace either end. It becomes a bridge between them:

- an engineer who understands architecture can use AI to explore a new disclosure framework quickly;
- a domain expert can use AI to translate intuition into executable code constraints.

Both sides move toward the middle.

Leverage is not simply “AI makes you faster.” That is acceleration. The real leverage is the ability to span both sides of the spectrum while someone else remains on one. The wider the span, the more AI can amplify.

But spanning the spectrum does not happen automatically. An engineer with years of production-incident experience knows how systems fail silently, but does not automatically know where an LLM is reliable. That is another form of judgment and requires deliberate investment.

The people who gain leverage are those who have depth on one side and use AI as a bridge to explore the other.

## An Uncomfortable Simplified Calculation

Consider a deliberately simplified example intended only to show the mechanism:

- the total cost of one senior engineer equals the cost of five junior employees;
- the senior writes down architecture, constraints, and design decisions, and AI executes;
- the five juniors use the same AI but may not know what to request or how to judge whether the output survives production.

In 2023, junior employees were still doing much of the typing. By 2026, more code can be generated by AI while senior people direct and review. The traditional junior task of “execution under guidance” is precisely the part AI is improving at most quickly.

The calculation is uncomfortable, but versions of it have probably entered many management discussions.

There is also a counterintuitive fact. In the short term, AI can flatten some skill differences. Give a junior worker a good tool, and on tasks where AI is strong they may approach senior-level performance.

That does not necessarily help the labor market in the same way. If a senior person plus AI can deliver the result that once required a team, the team positions may never open.

### The Other Side of the Calculation

One senior person plus AI does not scale without limit.

The senior becomes the bottleneck:

- review capacity is finite;
- context switching has a cost;
- decision fatigue accumulates;
- one person cannot carry all institutional memory forever.

Eventually, the company needs more senior people. Senior people do not appear from nowhere. They grow from junior employees who receive opportunities to build judgment through real work.

Eliminate every junior role and you optimize this quarter’s margin by sacrificing the talent pipeline five years from now.

The tension — optimize today or preserve future capability — has no clean answer. More mature companies will keep some junior positions and redefine them:

not “type what I tell you to type,” but “learn alongside someone who already knows how to direct, verify, and constrain AI.”

## What If Every Company Does It?

The previous sections concerned events that have occurred: company announcements, regulatory filings, analyst estimates, and labor data.

The next section is a thought experiment. The evidence is different and should be read differently.

### Macro Consequences: Rational Decisions, Irrational Outcome

One company reduces headcount and improves margins. Rational. Every company does it at once. The system may have a problem.

Citrini Research’s *The 2028 Global Intelligence Crisis* models this as a fictional future macro memo. It is not a prediction and not empirical evidence. It is a stress test asking what happens if every company makes the same individually rational choice.

Each decision looks reasonable:

- reduce team size;
- increase AI investment;
- raise output per employee;
- improve margins.

The collective result may form a negative feedback loop:

1. companies shrink teams and margins improve;
2. displaced workers reduce consumption and demand falls;
3. revenue comes under pressure, leading to more cuts and automation;
4. the loop repeats.

Citrini calls it an intelligence-displacement spiral. The unsettling part is that every step may be individually correct. No decision maker makes an obvious error; the system still produces a bad outcome.

The scenario assumes that the top 10% of earners drive more than half of consumer spending, and that a 2% decline in white-collar employment could produce a 3%–4% hit to discretionary spending, delayed by the savings buffers of higher earners.

Again: these are assumptions and figures inside the scenario, not observed facts and not this essay’s forecast.

The structural logic beneath them — the fallacy of composition, where what is good for each part can be bad for the whole — is a genuine economic problem.

## What About the Individual?

Return from companies and macroeconomics to the individual. If the leverage gap is real, where is the path?

### Is There Still a Path for Junior Workers?

The path is not closed. It is narrower and points in a different direction.

A company that once hired 100 junior employees may hire 40. The threshold cannot become ten years of domain experience, but it can rise toward the ability to collaborate with AI rather than merely work through AI.

The distinction matters.

**Working through AI** means treating it as advanced autocomplete: paste in the problem, copy out the answer, continue.

**Collaborating with AI** means understanding what it does well, what it does badly, and how to verify the difference.

Research has repeatedly found that people who trust AI blindly can perform worse than people with calibrated skepticism. As models become stronger and their outputs more plausible, the trap becomes harder to see.

The junior workers most likely to gain opportunities may not be those best at generating answers with AI. They may be those who develop calibrated trust early: knowing when to rely on the model and when to challenge it.

How can someone build that ability without experience? The pipeline’s development process suggests a few practices:

1. **Use AI as an exploration tool, not a substitute for understanding.** Ask it to explain the answer. Try to break it. Build a mental model of why it works.
2. **Build things that expose real constraints.** Judgment rarely comes from tutorial projects. It comes from edge cases, failure modes, and actual users.
3. **Run small tests on your own problem.** Try 100 cases and count the errors. That builds calibration faster than marketing material.
4. **Write boundaries, stopping rules, budgets, and exceptions clearly.** The difference between “write me a crawler” and “collect these pages under these stopping conditions, retry budgets, and compliance rules, and flag exceptions” is the difference between a demo and a system.

Project instruction files are not magic. They are accumulated engineering judgment written down.

Competition has moved earlier. A degree followed by learning everything on the job is no longer as secure a path as it once was. That is not despair. It is a different path.

Junior workers who arrive having built real systems, measured AI failure modes, and developed an instinct to question plausible output may have more advantage than they expect. Directing AI is becoming more valuable than acting as AI’s extension.

This advice is not only for junior workers.

Self-directed learning may be the most underestimated variable in the leverage gap. AI dramatically lowers the cost of experimentation across the spectrum. It does not make learning automatic. It shifts the barrier from access to knowledge toward the curiosity and discipline required to acquire and calibrate it.

The pipeline is evidence for this spectrum model.

A purely software perspective does not know which ESG disclosures matter and collects the wrong documents. A purely domain perspective cannot independently build browser fallback and retry budgets and returns to manual work.

The system exists because engineering ability, domain judgment, and AI formed a composition.

In an environment where AI amplifies cross-domain ability, the risks of saying “I do not need to understand the business” or “I do not need to understand the technology” are rising. AI replaces neither side, but gives increasing advantage to people who can cross between them.

The career ladder has not disappeared. Its first rung is higher, the ladder is shorter, and it no longer rises in a straight line through one discipline. It bends between disciplines.

The path from “can write code” to “can architect a system that solves a domain problem” is becoming more important and more highly rewarded.

The pipeline took nine months. During that time, it accumulated something an agent does not naturally possess at the beginning: context.

Next: Part 7 — Context Accumulation: What Agents Do Not Naturally Possess.

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
| 05B — What the Research Says: Frameworks | Karpathy, SWE-CI, the long tail, and convergence |
| **06 — The Leverage Gap** | **You are here** |
| 07 — Context Accumulation | What agents do not naturally possess |
| 08A — The Delegation Problem | Why you cannot simply throw it over the wall |
| 08B — The Autonomy Spectrum | Finding the right level |
| 09 — The Other Extreme | When skepticism becomes paralysis |
| 10 — Two Rooms | Demo enthusiasts vs. domain skeptics |
| 11 — The Evidence | The pipeline as evidence |
| Bonus — The Counterargument | AI argues against the entire series |
| Bonus — Standing in the Middle | The thought that arrives in the middle of the night |

## References

1. Block. [Q4 2025 Shareholder Letter.](https://s29.q4cdn.com/628966176/files/doc_financials/2025/q4/Q4-2025-Shareholder-Letter_Block.pdf)
2. Atlassian. [“An Important Update on Our Team.”](https://www.atlassian.com/blog/company-news/atlassian-team-update-march-2026) 2026.
3. Pinterest. [Form 8-K: Global Restructuring Plan.](https://www.sec.gov/Archives/edgar/data/1506293/000150629326000009/pins-20260122.htm) 2026.
4. Chegg. [“Chegg to Remain a Standalone Public Company.”](https://investor.chegg.com/Press-Releases/press-release-details/2025/Chegg-to-Remain-a-Standalone-Public-Company-to-Maximize-Shareholder-Value/default.aspx) 2025.
5. Amazon. [“Update on Our Organization.”](https://www.aboutamazon.com/news/company-news/amazon-layoffs-corporate-jan-2026) 2026.
6. Massenkoff, M. & McCrory, P. [“Labor Market Impacts of AI.”](https://www.anthropic.com/research/labor-market-impacts) 2026.
7. Citrini Research. [“The 2028 Global Intelligence Crisis.”](https://www.citriniresearch.com/p/2028gic) 2026.
8. CrowdStrike. [Form 8-K and Employee Communication.](https://ir.crowdstrike.com/static-files/355578e9-a500-4a76-b6b2-9d61a92a5a95) 2025.
9. CIO / TD Cowen. [“Oracle May Slash Up to 30,000 Jobs to Fund AI Data-Center Expansion.”](https://www.cio.com/article/4125103/oracle-may-slash-up-to-30000-jobs-to-fund-ai-data-center-expansion-as-us-banks-retreat.html) 2026.
