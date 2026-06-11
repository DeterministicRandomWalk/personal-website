---
title: 'Part 3B: Where LLMs Shine, and the 90% Agents Would Destroy'
description: 'Six simple-looking problems that burn through budgets in production.'
pubDate: '2026-06-05T18:00:00Z'
heroImage: '../../assets/series-03b-agents-destroy-illustration.jpeg'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[Previous: Part 3A.](/blog/llm-shines-agents-destroy-en/)  
[阅读中文版。](/blog/agents-destroy-orchestration-zh/)

Every problem looks simple until it burns through your production budget.

The previous essay covered where LLMs shine and why the remaining 90% is orchestration. Ambiguous classification is the 10% where LLMs are indispensable. Domain judgment also requires semantic understanding. The rest is orchestration. If you can write an `if`, do not ask an LLM.

But what does that orchestration actually face? Can agents handle it?

Imagine moving into a new apartment. You sign the contract, get the keys, and the big thing is done. Then you discover the shower pipe leaks, the kitchen outlet is unreliable, the closet door does not close, and the neighbor’s Wi-Fi interferes with your speaker. None of these is “hard.” Each one takes half a day. Three weeks later, you realize the move took one day and the “small things” took a month.

A production collection pipeline is like that. The previous essay covered the brain, the classification system. That is signing the contract and getting the keys. This essay covers the month after moving in. Six “small problems,” each one apparently solvable in half a day, each one eventually taking weeks.

In short: six simple-looking problems — link extraction, query parameters, stopping rules, PDF handling, PDF deferral, and `robots.txt` compliance — all break in surprising ways on real websites. Fixes come from company-by-company failures. Once fixed, they are written into code permanently.

Agents hit the same traps every run. A pipeline hits them once, then never repeats them.

## Problem 1: Link Extraction

How hard can it be to find every link on a page?

You go shopping. Products on shelves are easy to see. But some items are in the storage room, some are behind the freezer, and some are printed on a flyer that only makes sense if you ask an employee. Links on webpages are like that. Some are obvious. Some hide in places you would not expect.

An agent can call existing HTML parsing libraries. The question is: which one works directly?

The pipeline started with the simplest approach: find every `<a href>` tag. Done.

Then a company site rendered the navigation entirely with JavaScript. The static parser saw an empty page, like walking into a store and finding empty shelves because all products appear only after scanning a code. So browser rendering was added before HTML parsing.

Then another company hid download links inside `<link>` and `<area>` tags. Those are not normal places to put download links, but reality does not care about convention. Add them.

Then another company used a `<base>` tag, which changes the base address for all relative links on the page, breaking relative URL resolution. Fix it.

Then raw HTML parsing was not enough, so a Markdown conversion route was added because standardized text makes URL extraction easier. But the Markdown route could not handle every edge case, so the more complex raw HTML route had to remain. Merge both result sets and deduplicate.

See the pattern? Every time you think the extractor is complete, the next website disagrees.

Then comes deduplication. `/page`, `/page/`, and `/page/index.html` are the same page. `/reports?lang=en&sort=date` and `/reports?sort=date&lang=en` are also the same. But `/reports?lang=en` and `/reports?lang=fr` may be different pages. Deduplication has to understand which differences matter.

`javascript:` links, `mailto:` links, `tel:` links, and pure anchors are filtered. Cookie consent overlays that hide real navigation are handled. Download links and menu links are tracked separately.

Hundreds of lines of normalization code. Every line traces back to a real website where extraction failed.

The irony is that the most likely way for an agent to do this well is for someone to open-source a field-tested extraction pipeline, wrap it as a callable tool, and let the agent invoke it. Good. But now the agent is calling deterministic code written by engineers. It has become a natural-language shell around the pipeline.

The agent is the interface. Code is the engine.

That is exactly the composition model this series argues for.

No single library gets link extraction right across thousands of corporate websites. The answer is hundreds of fixes, each one earned through a real failure.

## Problem 2: Query Parameters

If link extraction is “finding every door,” query parameters are “discovering that many doors lead to the same room.”

Query parameters are the part after the question mark in a URL, such as `?page=2&lang=en`. Corporate websites use them to generate endless URL variants:

```text
/reports?page=1
/reports?page=2
/reports?lang=en
/reports?lang=fr
/reports?sort=date
/reports?sort=date&page=3&lang=en
```

Every combination is technically a unique URL.

First reaction: remove all query parameters. Clean URLs, no duplicates.

Immediate failure. `?lang=fr` may be the French version of a report that has no English equivalent. `?year=2024` may be the only path to the current disclosure. Remove everything and you lose files.

Second reaction: keep everything. Now 1,000 URLs become 10,000, or explode forever. Every parameter combination is technically “new,” and the collector enters an infinite loop.

The real answer: treat parameter classes differently.

The pipeline maintains a two-layer system. First, a fixed blocklist of useless parameters: ad-tracking parameters, analytics parameters, session IDs, and temporary tokens. Remove them unconditionally.

Then a heuristic classifier groups the remaining parameters: pagination, sorting, display settings, search facets, regional settings, resource IDs. Pagination and sorting are removed because they generate loops. Regional parameters and resource IDs are kept because they point to different content.

This classification was not designed up front. It was forced by a cloud billing alert.

One day an over-budget email arrived: LLM call costs had spiked far beyond expectations. Investigation showed that the collection engine was stuck in a loop on a large enterprise website. Different combinations of query parameters generated thousands of “different” URLs. `?sort=date&page=3` and `?page=3&sort=date` were technically two URLs but pointed to the same page.

The collector did not know. The classifier did not know. Every “new” URL triggered another LLM call, and the job kept running for days. It was like someone walking through a revolving door, convinced that every rotation led to a new place.

The bill kept growing.

The funny part: the bug was found by a billing email, not by the logging system.

An agent can easily see two URLs with different parameter order and treat them as different pages. It follows each variant and burns the token budget on duplicates it cannot recognize. By the time it “realizes” it is looping, if it realizes at all, the budget is gone.

“Which parameters matter?” sounds like a one-sentence question. In practice, it is a classification system accumulated from real failures.

The difference between 1,000 URLs and infinite explosion is one layer of parameter normalization. The difference between doing it right and doing it wrong is weeks of iteration.

## Problem 3: Knowing When to Stop

You are at a buffet. The first dishes are what you came for. Then you see desserts, fruit, drinks. Each item is individually “worth taking,” but if you take everything, the plate becomes a pile and most of it goes to waste.

Agents do not know when to stop.

Every corporate website has hundreds of news articles. Many mention `sustainability` or `climate`, and are technically ESG-related. But once the core reports, policies, and disclosures have been collected, another 500 news articles are just paper on the floor. The plate is already full.

It took weeks to learn this. Early versions of the pipeline behaved like a new intern, putting everything into the bag regardless of value. One large multinational produced thousands of news pages, press releases, and blog posts. The disk filled with noise. Downstream analysis was drowned in low-value content.

So the pipeline learned budgets. News pages have a hard cap of 200, written directly into code. Core ESG content — real reports, policies, and disclosures — is not capped. PDF downloads are deferred until page collection is complete because pages produce new links and PDFs do not. Downloading a 200-page report during collection blocks the link-discovery loop.

Adaptive thresholds tighten when signals are plentiful and loosen when signals are scarce. The logic is simple: when good content is easy to find, be selective; when signals dry up, cast a wider net.

None of this was designed in advance. Each rule came from watching the collector overspend on news archives, stall on huge PDFs, over-explore multinationals, and under-explore small companies.

An agent runs until the budget is gone. No cap, no deferral strategy, no adaptive tightening. People already complain that personal assistant tasks are expensive. Now imagine unconstrained collection across 5,000 corporate websites.

Human analysts know when to stop. The pipeline learned from observing analysts: 200 news articles are enough; get the formal reports first.

The interesting part is that humans need only a few dozen websites to form this intuition. The pipeline writes those human-derived rules into code and copies them across 5,000 companies without loss.

“When is enough?” is an engineering judgment. The pipeline hard-codes it. An agent may not even notice that the question exists.

The first three problems may feel understandable: a lot of details, but the logic is clear.

The next one is different. Even if you understand the logic, that is not enough, because the failure is not in the logic. It is in the messiness of reality.

## Problem 4: PDFs

PDF download sounds simple. Click link. Save file. Four words.

In practice, it is one of the most unpredictable parts of the entire collection system.

Start with filenames. This alone took multiple rounds.

A PDF link like `/content/dam/doc-847293.pdf` tells you almost nothing. It is like receiving a package labeled only with a tracking number. You have to guess what is inside.

Sometimes the server tells you the real name through a `Content-Disposition` header: `attachment; filename="sustainability-report-2024.pdf"`. That is the real filename.

But some file-distribution layers do not send that header. Then you inspect the final URL after redirects, because the redirect chain may land on a more descriptive endpoint. If neither source works, you fall back to the original URL path.

The pipeline tries these sources in priority order because none of them is reliable.

Then there is the download itself. Each failure mode deserves its own bug report:

1. Download dialogs: automated browsers can intercept them, but behavior differs across browser versions and operating systems.
2. New tabs: the browser renders the PDF instead of downloading it. A human sees it. Code does not. Automation waits forever for a file event that never arrives.
3. Redirect chains: three or four hops lead to the actual file. The HTTP client follows the first redirect, loses authentication cookies, and receives `403`. Or the redirect crosses domains and the `Referer` header breaks authentication.
4. Wrong `Content-Type`: the server says “webpage,” but the response is really a PDF. The browser believes the server.
5. PDF gates: enter an email, accept terms, complete a human challenge. The pipeline needs gate detection, pattern matching, fallback strategy, and logs for manual review when it cannot proceed.

Even after a successful download, saving can fail. Security software on a production machine may lock a file halfway through writing. The pipeline uses atomic file saves: write to a temporary file, confirm it is fully written, then rename it to the final filename. If renaming fails, retry up to five times. Without that mechanism, you get half-written corrupted PDFs.

None of this is intelligence. It is engineering ground out of hundreds of edge cases.

An agent that clicks a PDF link and expects the file to land neatly is not collecting. It is wishing.

The most dangerous failure is silent failure: no error, just a missing file. The agent does not notice. It keeps going, believing it collected the report.

The report is still sitting quietly in a browser tab the agent already closed, never downloaded.

“Click link, save file” is the human understanding of PDF collection. The pipeline version is hundreds or thousands of lines of code that block every known failure path.

PDF handling alone can break an agent. And it is only one of dozens of “simple” problems the pipeline has already solved.

## Problem 5: PDF Deferral

Problem 4 is about how to download one PDF. This problem is higher-level: when should you download it, and should you download it now?

Imagine moving to a new city. On day one, you do not immediately buy every piece of furniture. You first walk around, learn where the stores are, then decide where to buy what. Scout first. Move later.

Early versions of the pipeline did not know this. The strategy was: see a PDF, download it. It sounds reasonable. The link is available. Take it now.

After a few iterations, the problem appeared.

Some company websites contain hundreds of PDFs: annual reports, quarterly reports, press releases, investor presentations, policy documents, governance frameworks. The classifier is designed to prefer recall over omission, so many of them pass the ESG filter. Before the first few page-collection rounds even finish, more than 500 PDFs have already been downloaded and the budget is gone.

Worse, PDFs are dead ends.

After collecting a webpage, you can extract dozens of new links and feed them into the next classification round. That is the core engine of discovery. PDFs do not do that. Once a PDF is downloaded, it is done. It does not bring back new URLs.

Stopping midway through collection to download a 200-page report is like stopping halfway through exploring a city to move furniture. You do not yet understand the city layout, and the truck is blocking the road. Page collection, the part that actually discovers new links, waits. One large PDF occupies connection slots and bandwidth while other requests queue.

Would an agent think of this?

Three lessons forced the deferral strategy:

First, PDFs are dead ends, so collect pages first. Pages produce links. Links produce classification rounds. Classification rounds find more content. That loop is the heart of the pipeline. PDFs do not participate in the loop, so they go last.

Second, deferral enables reordering. If you download a PDF the moment you find it, arrival order decides priority. That has nothing to do with relevance. If you first accumulate all PDF links and process them after page collection, you can sort by relevance: PDFs found on ESG hubs first, PDFs found in news lists later. The most relevant PDFs get the budget first.

Third, batch PDF download needs its own strategy. PDF download failure modes are different from page collection failure modes, so mixing them interferes with both. Deferral lets PDFs use specialized concurrency, retry, and timeout settings without disrupting page collection.

Agents do not naturally have a concept of deferral. They see a PDF link and try to download it because the instruction is “collect ESG content,” and this PDF looks like ESG content. They do not know that downloading it now means giving up opportunities to discover more links. They do not know that only 50 out of 500 PDFs may matter. They do not know that saving PDFs until the end enables reordering.

“Collect pages first, then download PDFs.” Six words. Behind them are multiple iterations of pain.

Deferral is not laziness. It is doing the right thing in the right order.

## Problem 6: robots.txt

The first five problems are engineering problems. This one is different: it is an organizational constraint. It has nothing to do with code quality or model capability. If legal says no, the answer is no.

At some point, compliance and IT review entered the project. The question was direct: is this legal? Does automated access to corporate websites create legal risk?

In practice, the collector behaves much like a human analyst browsing manually: fixed per-domain rate limits, no faster than ordinary browser clicks in many cases. It does not make violent request bursts, bypass authentication, or impersonate users. The purpose is analysis of public ESG information, not competitive intelligence or data resale. That can be explained.

But IT had one hard requirement: respect `robots.txt`. `robots.txt` is a text file at the root of a website that tells automated programs which paths they may access and which paths they should not. No matter how gentle the collector is, if a site explicitly says “do not go there,” the collector does not go there. This is not a technical preference. It is a compliance floor.

So it became a new engineering problem.

The `robots.txt` specification looks simple, like traffic lights: red means stop, green means go. Parse `User-agent` and `Disallow`. How hard can it be?

Real-world `robots.txt` files are more like an old city’s traffic system. Some intersections have lights, some have handwritten signs, some signs contradict each other, and some are broken. Some use wildcards, some define different rules for different crawlers, and some are malformed.

Every URL has to be checked before the request is made: is this path forbidden by `robots.txt`?

This feature took several iterations to stabilize. The first version handled basic rules and worked until wildcards appeared. The second added wildcard matching and `Crawl-delay`. The third handled priority conflicts between `Allow` and `Disallow`. Each round tested against real `robots.txt` files, found edge cases, then iterated.

Now every URL passes through a `robots.txt` check before entering the collection queue. Forbidden paths are skipped, logged, and never requested. This is a deterministic prefilter. It has nothing to do with classification or content. It is compliance.

An agent will not reliably decide to check `robots.txt` on its own. Even if the prompt says “respect `robots.txt`,” the agent has to fetch it, parse it, match every URL, and repeat the process every run.

More importantly, compliance is not a “try your best” task. It is mandatory. Asking a probabilistic system to handle a zero-tolerance constraint is already the contradiction.

Legal and IT do not care how smart the model is. They care whether you can prove every request was checked against `robots.txt`. The pipeline can. The agent cannot.

Compliance constraints do not need intelligence. They need identical, auditable, zero-omission execution every time.

## Six Problems, One Pattern

Look back at the six problems: link extraction, query parameters, stopping rules, PDF handling, PDF deferral, and `robots.txt` compliance. They all have the same shape:

1. From the outside, they look simple: “How hard can link extraction be?”
2. On real websites, they break in unexpected ways.
3. Fixes come from failure: watch the pipeline fail on a company, then fix the failure.
4. Once fixed, encode it in code forever. It does not need to be smart. It needs not to forget.

Agents re-experience the traps every run. Engineers fix them once, write them into code, and never repeat them.

Remember the apartment metaphor? Signing the contract is the big event, but what makes the apartment livable is fixing every leaking pipe and unreliable outlet. These six problems are the pipes and outlets. Not smart. Not simple. But once fixed, they are fixed.

That is the 90%. It has already been solved, and it does not need to be solved again tomorrow.

It is understandable that people outside the system believe agents can solve everything. But even within development teams, AI strategy often splits into two camps. One camp treats AI as a general substrate: build the infrastructure, wrap everything, and let the general tool handle the rest. The other camp still sees human judgment as central and believes the investment should go into domain experience and frontier knowledge. This is not a disagreement between outsiders and insiders. It is a disagreement between engineering philosophies.

Choosing the agent route implies a belief that general tools can handle everything, effectively betting that general intelligence has already arrived. Choosing the custom pipeline route acknowledges that human experience, frontier knowledge, and forms of information transfer not yet fully captured by language are still irreplaceable today.

That gap will shrink over time. AI is indeed eating the boundary of human knowledge step by step. But “step by step” is not the same as “today.”

After all this, where are the numbers? For the same task, how far apart are the pipeline and agents?

Next: [Part 4 — An Honest Comparison: Pipeline vs. Agents, by the Numbers](/blog/honest-comparison-en/).

---

Chinese original: [第3B篇：LLM 闪耀的地方——以及智能体会毁掉的 90%（下）](/blog/agents-destroy-orchestration-zh/).
