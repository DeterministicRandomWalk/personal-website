---
title: 'Part 2: From “Just Throw It at AI” to 7,400 Lines of Code'
description: 'Why “let AI decide which links are ESG-related” turned into seven layers of engineering.'
pubDate: '2026-06-04T12:00:00Z'
heroImage: '../../assets/series-02-seven-layers-illustration.png'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[Previous: Part 1.](/blog/impossible-task-en/)  
[阅读中文版。](/blog/seven-layers-zh/)

The previous essay described the portfolio manager’s impossible task: a fund needed ESG data for 5,000 companies. A chatbot could not do it because scale, completeness, and auditability all failed. So she brought the problem to the development team.

The developer’s first instinct was straightforward: start from each company’s homepage, extract all links, and decide which ones should be collected. It sounds simple until you actually try to do it.

In short: asking AI to decide which links are ESG-related sounds easy. In practice, it became seven layers of engineering: multi-level keyword scoring, cross-language rules, URL tree analysis, score inheritance, PDF filename scoring, prompts refined through repeated failures, and budget allocation that tightens or loosens automatically.

AI handles only the small final slice of genuinely ambiguous cases. The earlier layers filter everything that can be filtered. Each layer exists because the previous layer failed on a real website.

## Receiving the Task

The portfolio manager brought the requirement over: can we systematically collect all ESG-related pages and files from the official websites of thousands of companies?

The first reaction was direct: visit each company’s homepage, extract every link, and decide which links to collect. After collecting a page, extract links from that page, decide again, collect again, and continue until there are no new links worth exploring.

It does not sound hard. The hard part is “decide.”

“Decide which links to collect” takes three seconds to say and months to build.

## First Try: Keyword Matching

The most obvious idea is to look for keywords in the URL. Keep links containing `sustainability`, `ESG`, or `climate`; discard the rest. A few lines of regular expressions, right?

A few companies later, it already fails.

`/energy/`: is that an energy product page or climate policy? It depends on the company. `/csr/`: on some corporate websites, this is ESG, but an English regex may not recognize it. `/content/dam/doc-847293.pdf`: there is not a single useful keyword in the URL, but it happens to be the company’s annual sustainability report.

Too many keywords create false positives: product pages and news pages flood in. Too few keywords create false negatives: the important disclosure is hidden behind a meaningless path.

Hundreds of lines of regex still do not solve it. This is not a problem rules can solve alone, because the same path means different things across companies, languages, and industries.

Fine. If rules are not enough, let AI decide.

The same word means different things on different company websites. Rules never catch up with reality’s diversity.

## Throw It at a Large Language Model

This feels like the step that should solve it. You have seen the demos: AI reads documents, answers questions, classifies text, and appears close to human-level accuracy. Asking it whether a URL is ESG-related should be easy for a model that can write poetry and solve complex questions, right?

The most obvious first step is to send each URL to the model individually: “Is this ESG-related?” Simple. Accurate. And immediately, absurdly expensive. One company can have more than ten thousand links. Now multiply that by 5,000 companies.

So you batch. Put 50, maybe 100 URLs into one prompt: “Which of these are ESG-related?” Costs drop by orders of magnitude. But how large should a batch be? Too small, and API calls are still too numerous. Too large, and the model starts losing track: classification quality drops, items are missed, output formatting breaks.

The best batch size is not something you can guess. You test 20, 50, 80, 100. You check accuracy, cost, timeout rate, and keep adjusting.

This is the first place where human judgment becomes unavoidable. There is no formula for the optimal batch size. It depends on the model, prompt length, URL complexity, and context density. Machines can execute the batches, but humans decide which trade-off is acceptable.

It works. Sort of.

For a large company with more than 1,000 URLs, this means multiple batches, minutes per batch, and costs that accumulate quickly. Sometimes an API call times out halfway through processing. Sometimes the response format is malformed: the model returns classifications for 47 of 50 URLs, and you do not know which three are missing. Sometimes it simply misclassifies.

`/content/dam/doc-847293.pdf` has no ESG keyword in the URL, so the model skips it.

You just lost the company’s main sustainability report because the path was an auto-generated content-management identifier.

“Let AI decide” is the most natural idea, and the starting point for every layer of complexity that follows.

Each of the seven layers starts the same way: you expect AI, so magical in demos, to solve the problem directly without requiring you to understand the messy details underneath. Then reality tells you, layer by layer: no.

Not because AI is useless. AI is useful, and becoming more useful. But there is a long distance between “impressive in a demo” and “stable across thousands of companies and many languages on real data.” You do not cross that distance with hope. You test, measure, and hit the boundary again and again, even as the boundary keeps moving.

## Layer 1: Context Changes Everything

**Insight: a raw URL does not carry enough information.**

Links do not live alone on a page. They are surrounded by titles, descriptions, and nearby text. A link labeled “Download our 2024 sustainability report” under an “ESG Disclosure” heading is obviously relevant, even if the URL is `/content/dam/doc-847293.pdf`.

So you build link-context extraction. For each URL, capture anchor text, surrounding paragraphs, and parent headings. Send those with the URL to the model.

Classification accuracy jumps from about 70% to about 95%.

The extraction code itself? An AI coding assistant can write it efficiently. It is direct DOM traversal. But the insight that raw URLs are not enough, that surrounding text carries the signal, comes from weeks of watching the classifier fail on real websites.

Agents can write code. They do not automatically know that this code needs to exist.

Put plainly: the street address of a link matters less than the label taped beside it.

The problem is not that AI is not smart enough. It is that nobody showed it the right evidence.

## Layer 2: Token Explosion

Now you are sending paragraph-level context for 1,000 URLs per company.

1,000 URLs × roughly 2,000 tokens each = 2 million tokens. Accurate classification usually cannot rely on the URL alone; it needs the surrounding paragraph-level context. Just for classification. Just for one company. Now multiply by 5,000.

And the key problem remains: results are still not good enough. The model loses track of items in large batches. You need a smarter method.

You solved the accuracy problem and created a cost problem. Engineering tends to work like that.

## Layer 3: The Tree

URLs are not random. They have structure.

`/sustainability/reports/annual-2024` and `/sustainability/policies/climate` share a prefix. What if you organize all URLs into a tree, a domain prefix tree, split by path segments?

Now `/sustainability/` has 40 child nodes and is obviously worth exploring. `/careers/` has 200 child nodes and is obviously not.

A full tree for a large corporate site may have thousands of nodes, more than fits comfortably in context. So you evaluate only the first few levels. If an entire branch is clearly not ESG, such as `/products/`, `/careers/`, or `/e-commerce/`, you skip its children without looking at them individually.

For large websites, this removes 40–60% of URLs before the model sees anything.

But the tree does more than prune. It identifies trajectories: path prefixes such as `/sustainability/reports/` that carry strong ESG signal. Each trajectory gets a confidence score based on keyword hits, depth, and child count. Later stages treat those trajectories as anchors: anything discovered under a high-confidence trajectory inherits that credibility.

It is like sorting mail by postal code before opening any envelope. Much of the sorting is done before detailed inspection begins.

Not every URL needs individual judgment. Structure itself is information.

## Layer 4: Score Inheritance

A sustainability page under `/sustainability/reports/` links to a PDF: `/content/dam/report.pdf`.

The PDF path, `/content/`, looks like a generic content-management folder. Your rules score it as unknown. But the link came from a sustainability page.

So you add parent-child tracking. PDFs discovered on high-scoring pages inherit the page’s score. Now `/content/dam/report.pdf` is correctly classified, not because of its own path, but because of the page that pointed to it.

Without this, you lose files hosted in content-management systems or static file services. There are many of them.

A document placed on the “sustainability” shelf is probably about sustainability, even if its filename is just an identifier.

The value of a file is not only what it is called. It also depends on who recommended it.

## Layer 5: The Keyword Brain

Many model calls are unnecessary. But the solution is not a simple skip list. It is a scoring engine.

Hard skip rules handle the obvious cases: `/careers/`, `/login/`, `/shop/`, `/press-releases/`. Dozens of regular expressions across multiple languages. On most sites, these are not ESG.

Then comes the real workhorse: a multi-level keyword scoring system.

- **Strong disclosure signals**: terms like `sustainability-report`, `climate-action`, and `human-rights-policy`. If they appear in the URL or context, classify as ESG without calling the model.
- **Ambiguous signals**: terms like `report`, `strategy`, `policy`, `governance`, and `privacy`. They may be ESG, or they may be product strategy documents. Context decides.
- **Topic signals**: terms like `renewable`, `solar-farm`, and `circular-economy`. They are useful only outside commercial paths. `renewable` under `/products/` is a product page; under `/sustainability/`, it may be climate action.
- **News and blog penalties**: news items are scored based on whether nearby text contains ESG evidence.

The same keyword, `energy`, receives very different scores under `/sustainability/energy/` and `/products/energy/`. Commercial path penalties automatically reduce the weight of topic keywords under `/services/`, `/products/`, `/business/`, and similar paths.

PDFs get their own filename scoring system, because filenames reveal a lot. A filename containing `sustainability-report` or `esg-report` is accepted directly. Climate disclosure abbreviations or `climate-report` are almost certainly ESG. `annual-report` is likely, but not guaranteed. `newsletter` or `press-release` is low value and pushed down the queue. Pure identifiers like `doc-847293.pdf` are the cases that genuinely need model judgment.

After the earlier layers, there are not many truly ambiguous files left.

E-commerce detection prevents another class of false positives. If an ESG page sidebar happens to contain words like `deals` or `clearance`, that should not make the page skippable. So the system requires multiple commerce signals before filtering. A single word is not enough.

These lists are not purely handwritten. The model suggests candidates, but every entry is reviewed by a human. Models make subtle mistakes: treating `energy` as always ESG, or missing regional synonyms and conventions.

Imagine a 500-entry dictionary where every word means something different depending on the company website. That is what this layer maintains.

The same word can mean opposite things in different contexts. AI does not automatically learn that. People learn it by stepping on the trap.

## Layer 6: Prompt Evolution

This is the part nobody expects to take months.

Version 1: classify as ESG or non-ESG.

`/about/governance/` is classified as non-ESG. The model reads `about` as a generic corporate-info prefix. You rewrite: treat governance, ethics, and board oversight as ESG-related.

Now it catches governance, but overfires on `/about/our-leadership/`, which is just executive bios. Version 3 adds negative examples.

A regionally common `csr` path is missed because the English examples do not cover that convention. Version 4.

PDF links are misclassified. Version 5. The model returns “maybe” instead of yes/no. Version 6. Batch prompts behave differently from single-item prompts. Version 7. An industry-specific safety disclosure is skipped. Version 8.

You are past version 10, even though you expected version 2 to be “done.”

Every version fixes a real misclassification on a real website. Prompts are not clever; they are precise. Precision comes from failure.

An agent starts from version 1 every time. The same mistakes. Every run. Unless someone encodes all those improvements into deterministic prompt templates. Which is exactly what you did.

A prompt is not a clever instruction. It is a field checklist forged from hundreds of failures.

You think you are done writing the prompt, and then the next company breaks it.

## Layer 7: Budget and Allocation

Some companies generate thousands of ESG-related URLs. You cannot collect them all. But hard caps are dangerous: if the first 400 items are sustainability-award news articles and the real report appears at item 450, the cap misses the important content.

So you design allocation. News pages get sub-limits. Core ESG content bypasses limits. The system tracks which categories are full. When signals are abundant, thresholds tighten; when signals are scarce, thresholds loosen.

The real accelerator is iterative context reuse. An exploration cache stores path evaluations from each round. On the second pass through the same company website, most model calls are skipped because the system already knows the answer. By the third pass, the cache hit rate is even higher.

What used to cost several dollars per company per iteration now costs a small fraction of that.

When there are many signals, tighten standards. When there are few, loosen them. Just like a human analyst.

Deciding what to collect under resource constraints is itself engineering. It cannot be improvised every time.

## An Honest Answer

A few weeks earlier, an AI-driven ESG data vendor pitched its data product. The pipeline description felt familiar: same problem, same solution shape, same complexity.

So someone asked directly: where does your data come from? How do you ensure you captured everything?

The answer was honest: they had a data-collection engine, and also a dedicated team that manually clicked through content when necessary.

Not agents. Not one clever prompt. A human team as the final completeness backstop. Even a company whose entire business is ESG data could not fully automate the judgment.

If agents could do it, they would not need that backstop.

Even specialized ESG data providers need human fallback. Fully automated judgment is still a fantasy.

## The Result

Out of 1,000 candidate URLs, the model ultimately sees only a few dozen ambiguous groups.

Classification cost: a few cents to a few tenths of a dollar per company.

Seven layers:

1. **Link context extraction**: anchor text, headings, surrounding paragraphs.
2. **Hard skips + multi-level keyword scoring**: skip rules, keyword tiers, commercial path penalties, commerce detection.
3. **Domain prefix tree + trajectory mapping**: tree structure identifies ESG path prefixes and assigns confidence, pruning many URLs.
4. **Score inheritance**: PDFs and child pages inherit credibility from the page that discovered them.
5. **PDF filename scoring**: strong disclosure filenames pass directly; ambiguous files go to the model.
6. **Field-tested prompts**: many versions, each fixing a real misclassification.
7. **Budget allocation + iterative cache**: adaptive thresholds, category limits, and cross-iteration context reuse.

Even the “AI part” of the collector is 90% engineering and 10% intelligence.

This classification system is the brain of the pipeline, but it is only one organ. The rest is pure orchestration: batch size, browser cascades, state tracking, retry logic, PDF processing, cookie handling, and anti-bot detection.

It does not need intelligence. It needs precision.

Every layer in this essay starts the same way: “AI should be able to handle this, right?” Every layer ends the same way: “It can, but only after someone figures out what to feed it, when to trust it, and when not to.”

AI’s potential is real, and it is growing quickly. But potential is not delivery. Delivery comes from engineering. These seven layers do not reject AI. They are the price of making AI work in production, on real data, in settings where mistakes cost real money.

Next: Part 3A — The 90% Agents Would Destroy.

---

Chinese original: [第2篇：从“直接扔给 AI”到 7400 行代码](/blog/seven-layers-zh/).

Originally published externally: [source article](https://mp.weixin.qq.com/s/8V7cOAcCZLgnSkQOb4ZZhQ).
