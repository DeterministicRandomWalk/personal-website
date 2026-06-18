---
title: 'Part 6: The Leverage Gap — Who Actually Benefits from AI'
description: 'AI cannot build systems autonomously, but under expert direction it gives a small number of people with judgment enormous leverage.'
pubDate: '2026-06-18T12:00:00Z'
heroImage: '../../assets/series-06-leverage-gap-illustration.jpg'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[Previous: Part 5B — What the Research Says: The Frameworks.](/blog/research-frameworks-en/)

[阅读中文版。](/blog/leverage-gap-zh/)

The first five essays proved one thing: AI cannot autonomously build systems, but under expert direction it can complete a large share, perhaps even most, of the execution work that can be clearly constrained. The bottleneck is not AI capability. It is the human judgment directing it. That creates a new gap: people who possess that judgment can use AI to leverage work that once required an entire team; people who lack it find themselves being replaced by a smaller number of AI-amplified people. Companies are reorganizing around this gap — sometimes based on sound judgment, sometimes based on overestimating the technology.

Previous: Part 5B — What the Research Says: The Frameworks. METR’s reliability cliff, Anthropic’s own data, Karpathy’s composition framework, SWE-CI’s evolutionary failures — six lines of evidence, one conclusion: at least under current LLM architectures, agents are components, not systems.

The first five essays explained why AI cannot build systems autonomously. It is roughly 10% of the complete solution and cannot independently handle architectural decisions, edge cases, or trade-offs across components. It would be easy to conclude that if AI is only 10%, its impact must be limited. That conclusion misses the other half of the story.

## The Unfinished Story

The first five essays repeatedly emphasized what AI cannot do. This essay begins with a fact they did not explore: how much did AI actually do in this pipeline?

On the surface, the LLM handles only about 10% of the work — link classification, relevance judgment, and content scoring. The other 90% is browser cascades, retry logic, PDF handling, state management, and error recovery. That sounds like “AI did 10%; a person did 90%.”

That is not what happened.

Most of the code in that 90% — the seven levels of browser degradation, exponential backoff for retry budgets, heuristic PDF-scoring rules — was also written by AI. Not autonomously, but under the direction of an engineer with system experience: which edge cases would explode on the 500th company website, which retry strategies would collapse at scale, which apparently reasonable architectural choices would become technical debt three months later. AI performed the execution, but direction, constraints, stopping conditions, and architectural choices came from human judgment.

So the real picture is not “AI did 10%; a person did 90%.” It is this: under expert direction, AI completed a large share, perhaps even most, of the execution work that could be clearly constrained — provided that someone first thought through the boundaries and constraints.

That changes the entire equation. AI’s impact is not limited. It is enormous. But that impact has a precondition: the person directing it needs sufficient judgment. Without that condition, AI is an autocomplete tool that makes confident mistakes. With it, one person plus AI can deliver an outcome that previously required a team.

This is where the leverage gap comes from. The gap is not “can AI replace people?” The first five essays already established that it cannot do so autonomously. The gap is “who can direct AI?” People with that ability gain enormous leverage. Roles whose work is easier to standardize and requires less judgment face increasing pressure — not because AI has replaced everyone, but because AI has made a small number of people with judgment extraordinarily powerful.

Companies are already making decisions around this gap. Sometimes they are making the right judgment. Sometimes they are running ahead of the technology. Let us look at what is happening.

## Block Cut Nearly 40% of Its Workforce. The Share Price Rose About 24%

February 2026. Block — Jack Dorsey’s fintech company — cut more than 4,000 employees, roughly 40% of its workforce.

Dorsey said the quiet part aloud: “A significantly smaller team, using the tools we’re building, can do more and do it better.”

CFO Amrita Ahuja was more precise: *“We see an opportunity to move faster with smaller, highly talented teams using AI to automate more work.”*

Ahuja’s wording matters. She did not emphasize “the existing team plus new tools.” She emphasized “smaller, highly talented teams.” The leverage gap is almost written directly into the organizational language. Management is already dividing roles according to which work can be amplified by AI and which judgment remains scarce.

## The Chain Reaction

In this wave of restructuring, some companies have tied AI directly to layoffs: Atlassian cut 1,600 jobs and said explicitly that the move would self-fund AI investment and reshape its skills mix; CrowdStrike’s CEO called AI a “force multiplier” that helped flatten the hiring curve; Chegg cut 45% of its workforce and directly cited AI and changes in search traffic. Other companies have moved layoffs, organizational slimming, and AI investment forward together: Pinterest cut close to 15% of employees and wrote in an SEC filing that resources would be reallocated toward AI; Amazon cut roughly 16,000 roles while increasing AI investment, although its official explanation emphasized reducing layers, increasing ownership, and removing bureaucracy rather than claiming the jobs had been directly replaced by AI.

Dorsey’s prediction: “Within the next year, I believe the majority of companies will reach the same conclusion and take similar structural actions.”

The public language used by these companies points in a shared direction. They no longer treat “the current job structure + AI tools” as the default combination. They are reshaping the skills mix and prioritizing people who can work with AI, direct it, and exercise judgment at critical points. Anthropic’s labor-market research found no systematic rise in unemployment, but it identified an early signal worth watching: entry into occupations with higher AI exposure may be becoming harder for younger workers. The authors explicitly call it suggestive evidence and note several alternative explanations — younger people may be staying in existing jobs, moving into other occupations, or returning to education. The discussion is especially relevant to workers aged 22–25, who traditionally perform “execution under guidance,” but the signal remains marginal and requires continued observation.

This pattern is not “AI replaces humanity.” It is a more specific structural filter: does your work consist of independently executing standardized tasks, or making context-dependent judgments under uncertainty? The first category has always faced risk — during outsourcing waves and process automation too. AI has increased the acceleration by an order of magnitude.

## Oracle: When the Pattern Is Pushed to an Extreme

Only a few months after that prediction, Oracle appeared to push the pattern toward an extreme. Analysts estimated that potential cuts could affect twenty to thirty thousand people. That number remains an analyst and media estimate; Oracle has not confirmed a final total.

Oracle deserves separate attention because it reveals a mechanism deeper than “AI replaces jobs.”

Oracle has reported strong profit growth in recent quarters. This is not an unprofitable company cutting jobs to survive. Broad reporting and analyst estimates suggest that Oracle is freeing cash flow through large-scale reductions to support intensive AI infrastructure investment — tens of billions of dollars in AI data-center construction. Follow the external reporting and estimates, and a deeper mechanism appears: this is not merely “layoffs + AI investment.” It looks more like converting cost capacity previously allocated to people into capital expenditure for AI infrastructure — financing an AI-infrastructure bet that has not yet paid off.

Public reporting indicates that cuts span multiple business lines, but the company has not published a complete distribution. What can be confirmed is that the reductions are not limited to one type of role. What cannot be confirmed directly is whether employees were selected precisely along a line between standardized execution and non-modular judgment.

This echoes Dorsey’s phrase “highly talented teams.” Without exaggerating too much, the jobs are not only being “cut”; the cost capacity they release is being redirected into AI infrastructure. That is not Oracle’s own wording. It is an interpretation that follows from external reporting and analyst estimates.

This does not look temporary. It looks more like a structural shift in the definition of productivity. Companies are not merely using AI to help existing teams. They are rebuilding organizations around a new leverage ratio — fewer people, each with a greater AI multiplier, selected for judgment rather than volume of output.

## A Change of Era: From Assistant to Executor

AI in 2023 looked more like an assistant. You wrote code; it suggested completions. A junior employee plus GPT-4 was still a junior employee, just a faster one.

By the Claude Opus 4 generation, the shift looked more qualitative than quantitative. AI no longer only autocompletes. It implements. You describe an architecture; it writes the code. You specify constraints; it produces a solution. You review and iterate. Compress the change of the past two years into one sentence: AI is pushing many organizations away from “many people execute instructions” and toward “a small number set direction while tools perform more of the execution.”

This series will not pretend not to see the reality: for at least some standardized, repeatable software work that can be described through explicit constraints — maintenance scripts, standard CRUD applications, typical front-end pages, template-driven mobile apps — many organizations have begun treating AI as a reason to compress pure execution roles. These are real jobs held by real people. What matters is not only technical capability, but management’s judgment about which execution can be absorbed by tools. The next time a headline says “Company X cuts 500 engineers,” look at what was cut before reaching a conclusion.

The transition is not from “people write code” to “AI writes code.” It is from “many people execute instructions” to “a small number set direction and AI executes.” This will gradually change which roles matter most inside organizations — and it is unlikely to wait until everyone is ready.

What this shift means for the person who built the pipeline — both the excitement of acceleration and the anxiety of uncertainty — receives a more personal treatment in the bonus essay, *Standing in the Middle*.

## Rewriting the Arithmetic of Headcount

The pipeline itself is living evidence of the leverage gap. With AI assistance, one person with judgment can process a volume of work that once required a larger team. The issue is not simply “fewer people.” Direction becomes the new bottleneck. People who have it gain multiplied leverage. People who do not become more replaceable.

The leverage gap exists not only in corporate layoff tables and macro scenarios. It also exists inside organizations, between “official automation” and the complexity of real problems. In other words, this essay is not only about who gets replaced. It is also about which problems organizations take seriously enough to automate properly, and which still need people with high judgment to provide the backstop.

### The Institution’s Alternative

To put the pipeline into production, the developer needed a managed environment capable of supporting large-scale browser automation. An internal group suggested trying the organization’s existing visual automation solution and arranged a demonstration.

The answer became clear quickly. The tool was a proprietary graphical programming environment. You dragged visual modules around a canvas, asked them to navigate to a website — mostly an internal system — click links according to a fixed pattern, and save the result to a shared location. A robust, click-based automation playground. For its intended use — repeatable, predictable tasks against stable internal pages — it worked.

What it could not do was classify links across thousands of unfamiliar domains, handle anti-bot challenges, manage retry budgets, score PDFs by relevance, degrade through a browser cascade, or make decisions requiring judgment. The engineering problems described in Part 3 — browser cascades, retry logic, PDF scoring — were largely implemented by AI under human expert direction, but they required someone to know what needed to be built. That lay entirely outside the tool’s world.

This story is not told to mock the people behind the tool. It solves a real problem — automation for predictable workflows. The story matters because it reveals the other side of the leverage gap. AI is amplifying individual engineers, while many organizations’ institutional toolboxes have not kept pace with the complexity of the problems their business teams are trying to solve. The hype world outside says agents will replace everything. Inside enterprises, the official automation offering is often a click recorder.

The gap is not only between companies that have adopted AI and companies that have not. It is between what AI can make possible and what institutions actually provide. The people who fall into that gap — their problem is too complex for institutional tools, but they lack the engineering ability to build a solution — are exactly the people most likely to grab a general agent and pray that it works.

## The Leverage Equation

Imagine a spectrum. At one end are data, quantitative methods, and engineering toolchains. At the other are domain knowledge, industry experience, and business judgment. Most people spend their careers at one end because the barrier in the middle is high. An engineer who wants to truly understand ESG disclosure rules used to need years immersed in the field. An investment manager who wanted to write a production browser cascade had to learn programming from scratch.

AI is tearing down that barrier. It does not replace either end of the spectrum. It becomes a bridge between them — an engineer who understands architecture can use AI to work through an entire CSRD framework in an afternoon; an investment manager can use AI to translate domain intuition into executable code constraints. Both sides move toward the middle. Leverage is not “AI helps you work faster.” That is merely acceleration. Leverage is the ability to span both ends of the spectrum while someone else remains on one. The wider you span, the more AI can amplify.

But spanning the spectrum does not happen automatically. An engineer who has spent more than a decade debugging systems and fighting production incidents has deep intuition about what will quietly break in production. That does not automatically mean they know where an LLM is reliable and where it fails. That is another form of judgment and requires additional investment. The people who gain leverage are those with depth on one side who are willing to use AI as a bridge into the other.

The pattern applies in every industry. But to make the arithmetic concrete, use software engineering:

You pay one senior engineer $500,000 a year. Five junior employees cost $100,000 each. The total is the same. But:

- The senior writes `CLAUDE.md` — architecture, constraints, design decisions — and AI executes. The output is production-grade because the direction is production-grade.
- Five junior employees use the same AI but cannot write that direction. They do not know what to ask for, cannot judge whether the output will survive production, and are more likely to accept plausible but incorrect results.
- In 2023, junior employees were at least typing the code. In 2026, AI types the code and the senior directs it. “Execution under guidance,” the role juniors traditionally performed, is exactly what AI is becoming increasingly good at.

The arithmetic is uncomfortable. Whether or not people say it publicly, versions of it have probably entered many CTO and management discussions. A counterintuitive fact makes it harder to dismiss: AI really does flatten part of the skill gap in the short term. Give a junior employee a good AI tool and, on tasks where AI is strong, they can approach senior-level performance. That does not necessarily help the employment market in the same way. If a senior person plus AI can deliver what once required a team, those team positions may never open.

But the arithmetic has another side. One senior person plus AI does not scale infinitely. The senior becomes the bottleneck — review capacity, context-switching costs, decision fatigue. At some point, you need more senior people, and senior people do not appear from nowhere. They grow from junior employees who received opportunities to build judgment through real work. Cut every junior position, and you optimize this quarter’s margin by sacrificing the talent pipeline five years from now.

The tension — optimize now versus preserve future capability — has no clean answer. Companies that handle it well will retain some junior roles and redefine them: no longer “type what I tell you to type,” but “learn to direct AI alongside someone who already knows how.”

## What Happens If Every Company Does It?

The previous sections describe things that have happened — company announcements, analyst estimates, and labor data. The next section is a thought experiment that extends the trend to the system level. The evidence is different. Read it differently.

### Macro Consequences: Rational Decisions, Irrational Results

One company shrinks its team and improves margins — a smart decision. Every company does it at once — now there is a problem.

Citrini Research’s *The 2028 Global Intelligence Crisis* models this scenario as a thought experiment. It is not a prediction and not evidence. It is a fictional macro memo set in June 2028, a scenario asking what happens at the system level if every company makes the same rational decision. Its value is not prophecy. It is that the structure is identical to the problem this series has described: individually correct decisions accumulate into a broken system.

Each company’s decision looks rational on its own:

- Block cuts more than 4,000 people. The share price jumps about 24%.
- Atlassian cuts 1,600 people, aiming to strengthen its financial profile.
- Oracle may cut tens of thousands — analysts do not argue that AI has already replaced all the work, but that the cuts release cash flow for an AI-infrastructure bet.
- Every CFO sees the same spreadsheet: smaller team + AI = higher margins.

The collective result is a negative feedback loop:

1. Companies shrink teams → margins improve
2. Displaced workers reduce consumption → demand falls
3. Revenue comes under pressure → more cuts → more AI investment
4. The cycle repeats

Citrini calls it the intelligence-displacement spiral. The most disturbing part is that every step is individually correct. Nobody makes a mistake. The system makes the mistake.

The numbers are specific: the top 10% of earners drive more than 50% of consumer spending. A reduction in white-collar employment does not merely reduce headcount; it hollows out the demand base. A 2% decline in white-collar employment becomes a 3%–4% decline in discretionary spending, with several months of savings buffers hiding the damage until it is already deep.

Again: these are assumptions inside the scenario, not observed statistics and not this essay’s prediction. But the structural logic behind them — the fallacy of composition, where something good for every part can be bad for the whole — is real economics, not science fiction.

## What About the Individual?

Return from companies and macroeconomics to the individual. If the leverage gap is real, where is the path?

## If the Leverage Gap Is Real, What Path Remains for Junior Workers?

The path is not closed. It is narrower, and it points in a different direction.

A company that used to hire 100 junior employees may now hire 40. The threshold has not risen in domain expertise — you cannot expect someone entering the field to already possess that. It has risen in the ability to collaborate with AI rather than work through AI.

The difference matters. Working through AI means treating it as sophisticated autocomplete — paste in the question, copy out the answer, move on. Collaborating with AI means understanding what it does well, what it does badly, and how to verify the difference.

A 2023 field experiment found that consultants using AI on a task outside its capability frontier were more likely to produce incorrect answers than those without AI, illustrating the cost of failing to question plausible output. In 2026, when AI is stronger and its output more convincing, the trap is only deeper. If the trend continues, the junior workers most likely to be hired may not be those best at generating answers with AI, but those who develop calibrated trust earlier: knowing when to rely on AI and when to question it.

How do you build that ability without experience? At a smaller scale, the development of this pipeline looked like this:

1. **Use AI as an exploration tool, not a substitute for understanding.** When AI produces an answer, ask it to explain. Try to break it. Build a mental model of why it works, not merely that it works.
2. **The things that build judgment are often not tutorial projects.** They are real things that expose edge cases, failure modes, and actual constraints. The pipeline’s lessons about PDF handling and browser cascades surfaced only under scale and pressure.
3. **Instead of trusting benchmarks, run the smallest possible test on your own problem.** Try 100 cases and count the errors. That builds calibration faster than any marketing material.
4. **In an environment with stronger AI, writing boundaries, stopping conditions, budgets, and exceptions clearly often matters more than “knowing how to prompt.”** Compare a junior employee asking “write me a crawler” with one asking “crawl ESG pages under these stopping conditions, retry budgets, and `robots.txt` compliance rules, and flag anything that does not match these patterns.” The distance between them is the distance between a demo and a system. `CLAUDE.md` is not magic. It is accumulated engineering judgment written down.

Competition has moved earlier. A computer-science degree followed by learning on the job is no longer enough by itself. That is not despair. It is different. Junior employees who arrive having built real things, measured AI failure modes on their own projects, and developed an instinct to question plausible output may have more advantage than they expect — because the ability to direct AI is more valuable than acting as AI’s extension.

And this advice is not only for junior employees. Self-directed learning is the most underestimated variable in the leverage gap. AI has dramatically reduced the cost of experimentation across the spectrum. As described earlier, an engineer can use an afternoon to work through an ESG framework; an investment manager can use AI to translate domain intuition into code constraints. The point is not that AI makes learning automatic. It shifts the barrier from “can you access knowledge?” toward “do you have the curiosity and drive to acquire and calibrate it?” In more and more fields that AI can help people explore, access to knowledge is becoming cheaper. The scarcer resource is the willingness to seek it out and calibrate it.

The pipeline is living evidence of the spectrum model. It could not have been built by a pure software engineer — without knowing which ESG disclosures mattered, the system would have collected the wrong documents. It could not have been built by a pure domain expert — without browser cascades and retry budgets, the work would have remained manual copy and paste. It exists because one person used AI as a bridge and occupied both ends of the spectrum at once.

In an environment where AI amplifies cross-domain ability, the risk of taking a one-sided position — “I do not need to understand the business” or “I do not need to understand the technology” — is rising. AI replaces neither end. It gives growing advantage to people who can cross between them and leaves people who remain on only one side increasingly fragile inside many organizations.

The career ladder has not disappeared. But its first rung is higher, the ladder is shorter because AI compresses the middle, and it no longer climbs in a straight line through one discipline. It bends between disciplines. Put the organizational changes, role compression, and cross-disciplinary leverage together, and the path from “can write code” to “can architect a system that solves a domain problem” is becoming increasingly important and increasingly well rewarded.

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
10. Reuters. [“Jack Dorsey’s Block to Cut Nearly Half Its Workforce in AI Overhaul.”](https://www.investing.com/news/economy-news/jack-dorseys-block-to-cut-over-4000-jobs-as-ai-use-expands-shares-surge-4529839) 2026.
11. Dell’Acqua, F. et al. [“Navigating the Jagged Technological Frontier.”](https://www.hbs.edu/faculty/Pages/item.aspx?num=64700) 2023.
