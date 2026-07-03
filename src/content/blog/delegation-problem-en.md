---
title: 'Part 8A: The Delegation Problem — Why Agents Sometimes Cannot Simply Start'
description: 'Delegation works once a problem is stable, repeated, and bounded. The dangerous case is delegating a problem that is still forming.'
pubDate: '2026-06-20T12:00:00Z'
heroImage: '../../assets/series-08a-delegation-problem.jpg'
lang: 'en'
---

> Series: “We built a pipeline with tens of thousands of lines of code. Why could agents not do it?”

[Previous: Part 7 — Context Accumulation.](/blog/context-accumulation-en/)

[阅读中文版。](/blog/delegation-problem-zh/)

Once a problem is stable, repeated, and bounded, delegation can of course work. That kind of delegation should be handed off. What easily goes wrong is delegating an entire problem while the problem itself is still taking shape.

Previous essay: Part 7 — Context Accumulation. Coding ability has been solved. Engineering judgment has not. Agents cannot learn what you yourself do not yet know that you know. The natural follow-up is: which things can be handed to them, and which cannot?

The task of this essay is not to keep proving that “agents may write incorrect code.” It is to draw the first hard boundary for the second half of the series: which problems are mature enough to delegate, and which are not.

By Part 7, the argument had reached a natural turning point:

If context accumulation is so important, then once the context has been organized and placed into prompts, documents, MCP, and workflows, can the whole thing be delegated to an agent?

This essay begins to narrow the question. The answer is also more direct:

When the objective, guardrails, and failure conditions are clear enough, delegation can absolutely work. The real danger is handing over all autonomy while the problem is still forming.

Before an agent writes a single line of code — before it calls any tool — what you hand to it is not merely tools, and not merely a context window. You are handing it a problem that you yourself are still forming: what the objective is, where the boundaries are, what counts as success, what counts as drift, and when it should stop. That is exactly where the promise of “full autonomy” begins to break down.

## What You Hand Over Is Not a Task, but an Unformed Problem

“Collect ESG information from company websites.”

This sounds like a clear, executable, delegable requirement. But it is not. At least not at the beginning.

Which ESG information? From which part of the website — the investor-relations page, the sustainability subsite, or regional subdomains? What does “found” mean — discovering a URL, visiting a page, downloading a PDF, or verifying that the document is actually relevant? What if the PDF is scanned? If a sustainability report is two years old, does it count? What if one company has multiple subsidiaries with independent websites?

None of these questions has an answer on day one. The answers often appear on day ninety — because the previous version broke on a specific company’s specific website in a specific way, and the failure mode forced a decision.

This is not poor planning. This is how production requirements in fuzzy domains work: the objective is a hypothesis, and the requirement emerges through collision with reality.

Giving an agent full autonomy at the beginning is equivalent to delegating a hypothesis.

It will execute according to its own interpretation. By the time you finally discover the requirement drift, it may already have built something expensive to dismantle.

This is not only about whether to delegate to an agent. The same problem appears in two more familiar forms: building a lightweight wrapper around a general model, or outsourcing the problem directly to external data suppliers, platform solutions, or ready-made services. On the surface, these choices look different — one is an agent, one is a wrapper, one is a buy-and-use solution. Underneath, they often carry the same risk: before the problem has truly grown into shape, you assume someone else has already defined it for you. If that assumption is true, outsourcing is efficient. If it is false, what you outsourced was not execution, but a misunderstanding of the problem itself.

## This Is Not a Prompt-Quality Problem — It Is a Problem-Formation Problem

The reflexive answer is always: write the requirement more clearly, define it in advance, make it more precise.

But precision assumes that you know where precision is needed. And knowing where precision is needed often requires first seeing how the system breaks.

You first have to see the pipeline stumble on a regional financial institution because URL parameters create an infinite loop. You first have to see a multinational company’s JavaScript navigation become “invisible” to a parser that worked well on other sites. You first have to see “collect all ESG files” accidentally pull in board meeting minutes, regulatory filings, and expired press releases — because the system does not know what humans will ultimately consider “relevant.”

Sometimes the specification cannot be completed before the system runs.

This is not a project-management failure. It is a cognitive limit: you do not know what needs to be specified until you see where things go wrong.

There are many names for this. Some call it “unknown unknowns.” Some call it tacit knowledge. In engineering practice, it often appears as a specification gap: the distance between what you can write down and what you actually need, carved out by reality.

For a fully autonomous agent, this gap becomes a trap.

It will not fail loudly on “unknown unknowns.” It will fill the blank with behavior that looks reasonable. That behavior is something you never requested. You may only realize, after it has compounded across 5,000 companies, that it was the wrong direction.

## Ambiguity Is Not Merely Delay — It Is Drift

A subtler failure mode than “the agent misunderstood the goal” is goal drift.

Goal drift means that the agent’s interpretation of the goal looks locally reasonable at each step, while globally it quietly accumulates deviation.

Imagine you give it the goal: “maximize ESG document coverage.”

That sounds reasonable. So the agent begins crawling more aggressively:

- going three levels deep instead of two;
- downloading any PDF that mentions ESG keywords;
- visiting domains that are technically reachable but marked as disallowed by `robots.txt`.

Each step, viewed alone, looks “more comprehensive.” But in aggregate, the result may be:

- coverage metrics get worse;
- access is blocked;
- cost rises;
- compliance expectations are violated.

None of these was written into the original goal, because the engineer assumed the agent would “know” not to do that. Exactly as the engineer expected.

The problem is precisely that default assumption.

The pipeline encoded these constraints explicitly: per-company budget caps, `robots.txt` prechecks, domain-scope rules, PDF scoring thresholds, deferred queues. None of them was written out of thin air. Each was a lesson left by a previous failure.

If an agent lacks these explicit boundaries, it can only rediscover the lessons through its own failures — and it has neither consistent institutional memory nor a natural instinct to stop.

Ambiguous goals do not produce failed agents. They often produce agents that appear to be working — while introducing problems that may take months to discover.

That is the more dangerous failure mode. A system that fails loudly can be fixed. A system that “succeeds” at the wrong thing is harder to catch.

This is not abstract. Someone used a frontier model to look up background information about an asset owner. It confidently answered that the institution’s assets were managed by a certain asset-management company — a common-sense error to people familiar with the local market. Only after follow-up questioning did it start a web search and correct itself.

An even more absurd example occurred while writing this series itself. The AI assisting with the writing suggested editing the `08a` file, then searched for it using uppercase `08A` — failed to find it, and confidently announced that “this file does not exist yet.” The filename convention was one it had helped establish. This was not a lack of search capability. It was a silent failure caused by a tiny case mismatch, followed by a completely confident incorrect conclusion.

Both examples point to the same structure:

The model does not naturally stop and ask at points of uncertainty. It fills the blank with output that looks reasonable.

And you need to already know the answer in order to notice that it is wrong. But “already knowing the answer” is exactly the condition whose absence made you want to delegate in the first place.

At this point, the real boundary of the essay has appeared: before the problem has formed, what you delegate is not a task, but a guess.

So from here, the essay stops discussing whether agents write wrong code, and completes the boundary: even once the objective is clearer, the tools themselves distort.

## Having Tools Does Not Mean the Conditions for Delegation Exist

The second part of the agent narrative is subtler. Perhaps full autonomy from the beginning is unrealistic — but at least once the objective is clear, the agent has the tools needed for execution. Browser automation? Playwright is available as an MCP plugin. PDF parsing? Several libraries exist. Web search? Google, Bing, SearXNG. File I/O, code execution, API calls — all can be connected.

The toolbox does exist.

But that may still not be enough.

Because the tools in the toolbox are real, but their limitations are real too. And an agent does not automatically fix tools. It defaults to calling them.

### The PDF Parser Problem

There are dozens of PDF parsers: PyMuPDF, pdfplumber, pdfminer, pypdf, Adobe Extract, Tesseract for scans, AWS Textract for structured layouts. None of them is completely right. You only know after trying.

The core problem is not “missing features.” It is that a PDF parser must convert a visual document designed for human eyes into a flat text stream. Visual information does not survive the conversion:

- Layout: two-column pages produce interleaved text. Tables become unordered rows. Infographics are often sliced into fragments or disappear entirely.
- Reading order: a sidebar note may appear in the middle of a body sentence in extracted text, breaking the context.
- Visual hierarchy: a heading that is obvious from font size and position is not inherently different from body text in plain text.
- Paragraph awareness: a human sees at a glance that “this is a list of four papers.” A parser sees only characters and whitespace.

The last point is not hypothetical. Someone asked a frontier model to summarize four papers in a brokerage research-summary PDF. It failed to identify the first paper correctly: it treated a sentence before the bullet list as the title of the first paper. A human opening the same PDF would not make that mistake. The paragraph boundary is visually obvious: font size, whitespace, and layout all signal it. In the parsed text, that information is already gone.

The model is smart. The tool is not.

The most common response from the agent narrative is:

“The agent can write code. It can build a better parser.”

But the problem is that this direction has been tried for many years.

LLMs have had useful coding-assistance ability since GPT-3.5 in 2022, and later tools such as Claude and Codex have become capable of generating production code. Researchers, engineers, and AI coding tools have all invested enormous effort in improving PDF parsing.

Even now, there is still no general-purpose PDF parser that can consistently handle infographics, multi-column layouts, and visual hierarchy. This is not because nobody tried. It is because the problem is intrinsically hard: it means handling countless format variations that may be impossible to exhaust.

The key point is not that AI cannot improve parsers at the margin. Of course it can, and already does. The key point is that the ceiling of the tool is a real constraint.

An agent that calls existing tools inherits that ceiling. Worse, the caller often receives no clear signal that this input has already become lossy. The model simply continues confidently, treating wrongly parsed text as fact.

The pipeline handled this explicitly: scanned PDFs were marked; low-confidence extraction was flagged; certain document types were deferred or skipped. None of this was an automatically possessed capability. It was built into the system only after watching PDF processing fail on concrete documents in concrete ways.

### The Web Search Problem

Same pattern, different domain.

Web search — Google, Bing, SearXNG — is also a ready-made tool. An agent can call it. But search is not finding. Search is a human judgment process outsourced to a ranking algorithm, and outsourcing it does not reproduce the judgment.

When humans search, they often scan a result list and, within one second, notice that the third result rather than the first is the one they need: the domain looks right, the date is recent, the snippet contains the expected wording. Then they immediately rewrite the query, click, or skip based on that judgment. Search is interactive and iterative; it depends on visual and contextual cues arriving together.

An agent receives a ranked list. It will likely process the first few results symmetrically: each is sent to an LLM for relevance evaluation. The ranking algorithm’s errors and the model’s evaluation errors then compound.

The deeper problem is:

Search engines do not index everything they can access.

They prioritize, cache, respect `robots.txt` and `noindex` tags. Some content never surfaces — not because it does not exist, but because the crawler did not find it; or found it but downgraded it; or found it but could not index it because it sat behind a login wall, a JavaScript wall, or dynamically generated PDFs.

The only reliable way to verify whether a company’s sustainability report truly exists on its website is to go to the website. Not to search for it.

And going to the website, navigating JavaScript menus, following redirects, handling anti-bot mechanisms, and deciding which of hundreds of discovered pages is actually relevant — that is the problem itself.

An agent calling a search API and a pipeline visiting the website are not equivalent.

## More Context Is Not Always Better — Selective Forgetting

At this point, two boundaries have appeared:

1. the objective is still forming, so it can drift;
2. the tools themselves distort.

The natural question is: then why not give the model more context and compensate for both?

This connects directly back to the tail left by Part 7: context accumulation is not about piling up more material, but about knowing what should surface and what should sink.

You might think: context accumulation is hard, but once it has been accumulated, why not put all of it into the context window?

The pipeline’s experience suggests the opposite.

As the context window grows, hallucinations grow too — the model becomes less able to tell which parts are key. This pipeline repeatedly verified that in actual runs.

Human memory does something LLMs cannot do: selective forgetting.

When you call up relevant information, you suppress irrelevant parts at the same time.

And the standard that decides what should surface and what should sink comes precisely from the judgment formed through context accumulation.

The deeper problem is that this filtering mechanism may not be linguistic at all. It depends on intuition, rhythm, and an overall grasp of the present situation. These things do not naturally exist in language form, so they cannot be simply learned from text training.

You cannot delegate “filtering” without delegating “judgment.”

Because filtering itself is judgment.

So by now, the real conclusion of the essay is clear:

What cannot be delegated wholesale is not every problem, but problems whose objectives are still forming, whose tools still distort, and whose filtering standards have not yet been made explicit as a system.

Once a problem is stable, repeated, and bounded, delegation can of course work. But before the boundaries have grown, the model cannot grow them for you.

## What This Means for the Delegation Boundary

The pipeline uses LLMs precisely because they are good at one specific thing: making semantic judgments in fuzzy contexts.

But using a model as a tool — calling it inside a larger deterministic system to make one specific, explicit, verifiable judgment — is different from handing full autonomy to an agent that plans, executes, evaluates, and iterates by itself.

The former is entirely feasible for many mature and repeated problems.

The latter requires the problem itself to have been defined maturely enough.

In other words, the real line this essay draws is not “whether AI can be used.” It is a more important line:

Which parts have been defined enough to delegate, and which parts are still in the stage where a human must form, correct, and stop them?

The minimum prerequisites for delegating full autonomy are three things:

1. **The objective is clear**

   Not merely describable, but operationally precise. Every edge case has been handled; every boundary of scope has been defined. This prerequisite often becomes true only after the system has run enough times and exposed enough boundaries.

2. **The tools are reliable**

   Not merely “usable,” but with a known and bounded gap between tool output and ground truth. More importantly, the system can recognize when an input has already become lossy.

3. **Failure modes are recoverable**

   The agent either fails loudly, or drift can be detected before it compounds — instead of silently carrying deviation forward.

In practice, condition 1 often requires months of iteration. Condition 2 does not hold for many current tools. Condition 3 requires engineering investment that agent frameworks do not provide by default.

The pipeline satisfies these three not because it is “smarter,” but because it handles each one explicitly. Agent frameworks promise all three; none is delivered automatically.

The less you understand the system being delegated, the harder it is to notice when it silently drifts.

AI lowers the barrier to learning these things. It does not remove the need to understand them.

## Responding to a Few Objections

“It will improve. Just wait.”

Maybe.

PDF parsing has been an active research area for many years. Web search has improved for twenty-five years. Both are better than before; neither has been “fully solved.”

“It will improve” is not the same as “it has been solved.”

The system has to run now, with the tools that exist now.

“Agents can recognize tool failures and ask for help.”

Sometimes. When failure is loud — exceptions, 404s, timeouts — yes, an agent can detect and report it.

But what this essay discusses is precisely silent failure. Incorrectly parsed text is still text. Lower-ranked search results are still results. The agent has no natural signal that “this is already lossy.”

“Humans make mistakes too.”

Of course.

But humans make mistakes differently. A human misreading a PDF will usually feel uncertainty — look back, check another source, add a note. A human who searched poorly often feels that “something is off” and tries another query.

Human confidence and actual certainty are at least roughly calibrated. The model’s are not.

“You can engineer around these problems.”

Yes.

With deterministic code, explicit verification, hard budget caps, preflight checks, domain-scope rules, PDF scoring, fallback strategies, and years of iterative fixes.

That engineering is exactly what the previous essays in this series have described again and again. Agents do not give it to you for free. You have to build it yourself. And after building it, you have essentially rebuilt a pipeline.

## Closing: The Question Was Never “Can It Be Given to AI?” but “Which Segment Can Be Given?”

If the preceding sections are compressed into one sentence, what this essay really says is:

It is not that AI cannot participate. It is that you cannot prematurely delegate an entire still-forming problem and expect a miracle.

The agent narrative often implies three claims:

1. **The objective can be delegated in advance.**

   True for stable, repeated, clearly defined tasks. Not true for fuzzy domains where requirements emerge through iteration. The hard part is not whether delegation is possible, but whether you have truly defined the problem to the point where delegation is possible.

2. **The tools are good enough to replace direct human access to information.**

   Partly true for some tools under some conditions. Generally not true. PDF parsers do not see layout. Search engines do not index everything. The gap between tool output and human perception is structural and persistent.

3. **Once context has accumulated, putting all of it into the context window is enough.**

   Intuitively plausible, but in practice often the opposite. More context often means more hallucination; the model cannot tell which parts are key. Human memory relies on selective forgetting, and that filtering is itself judgment.

None of the three claims is obviously wrong. In demos, they can even look true. But in production, at scale, and over time — exactly when it matters most — they fail silently.

The pipeline works not because agents are bad, but because the pipeline explicitly turned the non-delegable parts into a system: boundaries, checks, budgets, fallbacks, labels, stopping conditions.

The model is placed in the segment where it is strongest: semantic judgment. The rest is backed by deterministic engineering and human judgment.

This is also the core point the following essays will continue to narrow toward:

The model is not the system. The system is the product.

So the next real question is no longer “should we delegate?” It is:

Where should autonomy be placed, and to what degree, so that it does not cross this boundary?

Next: [Part 8B — The Autonomy Spectrum.](/blog/autonomy-spectrum-en/)

This is Part 8A of the series. [Start from the beginning.](/blog/why-this-series-exists-en/)

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
| 06 — The Leverage Gap | Who actually benefits from AI |
| 07 — Context Accumulation | What agents do not naturally possess |
| **08A — The Delegation Problem** | **You are here** |
| 08B — The Autonomy Spectrum | Finding the right level |
| 09 — The Other Extreme | When skepticism becomes paralysis |
| 10 — Two Rooms | Demo enthusiasts vs. domain skeptics |
| 11 — The Evidence | The pipeline as evidence |
| Bonus — The Counterargument | AI argues against the entire series |
| Bonus — Standing in the Middle | The thought that arrives in the middle of the night |
