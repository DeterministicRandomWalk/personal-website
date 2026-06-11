---
title: 'Part 3A: Where LLMs Shine, and the 90% Agents Would Destroy'
description: 'Ambiguous semantic judgment is where LLMs shine; the rest needs precise orchestration.'
pubDate: '2026-06-05T12:00:00Z'
heroImage: '../../assets/series-03a-llm-shines-illustration.jpeg'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[Previous: Part 2.](/blog/seven-layers-en/)  
[阅读中文版。](/blog/llm-shines-agents-destroy-zh/)

Ambiguous judgments that rules cannot resolve are where LLMs shine. The other 90% does not need intelligence. It needs precision.

The previous essay described the path from “just throw it at AI” to 7,400 lines of code. After months of iterative failure, a seven-layer classification architecture emerged. Even the “AI part” turned out to be 90% engineering. But that classification system is only the brain of the pipeline. The rest is the body that keeps it running.

We have talked about the brain. Now we need to talk about the body: the places where precision matters far more than intelligence.

In short: whether a URL contains ESG content looks like a yes-or-no question. Across more than 30 countries, multiple languages, and wildly inconsistent website structures, it becomes a semantic judgment full of gray areas. Rules handle most cases, but there are always cases rules cannot cover. The LLM is the final fallback that completes the system.

That is the exciting part.

But the LLM’s role is not limited to link classification. Domain-level decisions also require semantic understanding. The critical distinction is that the pipeline decides when to call the LLM, what context to provide, and what to do with the answer. The remaining 90% is orchestration: adaptive batch collection, two-level browser fallback, preflight sniffing, single-page-app detection, and rate limiting.

These are solved problems expressed as code. If you can write an `if`, do not ask an LLM.

## Rules First, LLM as Fallback

The previous essay covered link classification: deciding whether each URL is ESG content. Across more than 30 countries, multiple languages, and different URL structures, rules can cover part of the problem, and they should be used first. But there are always cases rules cannot handle. The LLM is the fallback.

Rules first. LLM as fallback.

Think of a hospital triage desk. Temperature, blood pressure, symptoms: a nurse with a checklist can handle 90% of triage. But some patients have strange symptoms, conflicting measurements, or cases the checklist does not cover. That is when you ask the senior doctor to take a look.

You do not put the senior doctor at the triage desk to measure everyone’s temperature. That wastes the scarce resource, and the doctor may not even be good at that task.

Why rules first? Because at the beginning, nothing is clear: the requirement is fuzzy, the target is vague, and success has to be discovered through exploration. You try websites one by one, fail repeatedly, and slowly extract patterns from failure. Each rule is a crystallized lesson.

The LLM fills the space rules have not covered: patterns that have not yet been discovered, or patterns too complex to express cleanly as rules.

That is where intelligence belongs.

This logic matches what many frontier automation projects keep rediscovering: even advanced agentic approaches need iteration to refine goals and requirements. They do not skip straight to the final answer. AI is becoming more human-like, but “human-like” also means this: humans need repeated trial and error to figure out what they actually want. LLMs do not bypass that step.

The reverse is also true. Once rules, requirements, and goals have been clarified through iteration and human judgment, the LLM can often handle the task well, because the answer has nearly surfaced. At that point, the behavior can even be packaged into a skill module.

Imagine a circle of knowledge. The center is mature, stable, well-known territory. The edge is uncertain, underexplored territory. The closer you are to the center, the more standardized the solution becomes. Build a webpage, create a CRUD app: these tasks are almost assembly-line work, with countless examples available. AI can reproduce them easily.

Move outward, and fewer people have walked the path. The solution becomes less certain: basic research, frontier product exploration, obscure failure modes only a handful of people have seen. LLMs can help, but replacing the human in one shot is hard.

ESG collection is not rocket science, but it sits toward the outer side of that spectrum. It is not that nobody has done it. It is that each company’s website structure is a new patch of unknown territory. This is not a binary question of can or cannot. It is a spectrum of determinacy. Mature knowledge is easier to automate; frontier exploration still depends on humans.

The interesting part is that once a frontier solution is discovered and shared, it quickly becomes standardized knowledge. LLMs can copy it without difficulty. Today’s frontier becomes tomorrow’s training data.

## Where Rules Fail Again

LLMs are useful beyond link classification. The previous essay focused on whether each URL is ESG content, the seven-layer classification system. There is a higher-level problem too: domain-level judgment.

A company’s ESG content may be scattered across multiple subdomains or even entirely different domains. As the collector extracts links, it continuously discovers new domains. Some of them may contain critical ESG reports. Missing one domain can mean losing an entire disclosure.

General-purpose crawlers usually do not think about this. You give them an entry URL, and they crawl under that domain. They do not proactively discover that key information may live on a different domain you did not know about in advance. So every newly discovered domain has to be judged: is it worth collecting?

As with link classification, rules come first. Newly discovered domains pass through a pattern filter. Domains matching the primary domain are allowed. Obviously irrelevant sites are excluded. The ambiguous cases go to the LLM.

But the LLM is not asked, “Does this domain contain ESG content?” It is asked whether the subdomain is part of the company’s main business presence.

`shop.example.com` is an online store. `careers.example.com` is a recruiting site. Those patterns are obvious and rules exclude them directly. But what about `regional.example.com`? Is it a local corporate site or a product catalog? What about `insights.example.com`? Is it marketing content, or a hub that leads to sustainability reports?

When the pattern cannot decide, the LLM can look at a sample page and judge.

These decisions depend on what is actually on the page. The pipeline fetches one sample page, truncates it to under 5,000 words, which is plenty for a domain-level decision, and sends it to the LLM together with the company name.

The instruction is explicit: prefer inclusion over omission. Missing a relevant subdomain can lose disclosure data. Including an irrelevant domain only costs extra collection time.

The difference from an agentic approach is not who calls the LLM. It is who decides what to ask, who to ask, and what to do with the answer. The pipeline discovers domains at fixed process points, prepares the context, calls the LLM, and then follows deterministic branches based on the result. The LLM does not decide on a whim to go exploring subdomains.

The LLM is the expensive consultant. The pipeline is the project manager: it decides when the consultant enters the room, which materials to review, and how to execute after receiving the recommendation. You would not let the consultant decide the meeting time, the attendee list, and the room temperature.

Use intelligence where intelligence is needed. Use control everywhere else.

## To Be Clear

This is not LLM skepticism. The collector’s output feeds a completely separate downstream LLM pipeline: ESG analysis, risk assessment, portfolio screening. The core judgment steps depend on LLMs.

That system is large too, and the conclusion is the same: LLMs are excellent at judgment and poor at process control. Give judgment to the LLM. Give flow control to code. This is true for the collector, and it is true for the downstream pipeline as well.

The details of that system deserve their own series. I mention it here only to be clear: this is not anti-AI. It is the opposite. We rely heavily on AI. We just put it in the right place.

## The 90% AI Does Not Help With

Everything else in the pipeline is orchestration. Orchestration needs precision, not intelligence.

Each company is a different challenge: managed bot challenges, age checks, JavaScript single-page apps, regional subdomains, cookie walls.

For each company, the collector:

1. Sends a preflight `HEAD` request to sniff content type before opening any browser.
2. Detects defensive measures and tests whether a standard headless browser can render the site.
3. Discovers entry points across domains and subdomains.
4. Classifies hundreds to thousands of links.
5. Collects pages with adaptive concurrent batches.
6. Escalates to a full local browser when the standard headless browser is blocked.
7. Defers PDF downloads until page collection is complete.
8. Loops until there are no new links.

That list looks tidy. But the framework was not designed in advance. It was built over nearly a year, one failure at a time. Each item corresponds to a real failure. The order in which they were added is the order in which things broke.

Small companies produce dozens of ESG pages. Large multinationals produce thousands. Multiply that by 5,000 companies, and the scale becomes obvious.

The encouraging part is that after a long period of tuning, the pipeline can cover almost all ESG information for almost all companies with high confidence. Early in the project, someone with deep technical and investment-domain experience heard the idea of building an in-house collector and asked the obvious question: is this not basically a vertical mini search engine?

The alternative was to buy the data. But after several attempts, external data never reached the required level. That is why the system ultimately had to be built.

Every line in the list above comes from repeated real failures. Here are a few.

## Preflight Sniffing

Preflight sniffing came from repeated failure. A URL looked like a normal webpage: no `.pdf` extension, no obvious marker. The server returned `application/pdf`.

The pipeline opened a full browser tab, waited for rendering, and received binary data. Repeat that across hundreds of URLs, and each company wastes minutes of browser time.

Now a lightweight `HEAD` request identifies the case in milliseconds. If `Content-Type` says PDF, the URL goes straight to the download queue and skips the browser.

## Single-Page Apps and Browser Fallback

Single-page-app detection came from a recurring problem. Some corporate websites render entirely through JavaScript, and a standard headless browser handles them. Others specifically detect automation traces.

So the pipeline runs a test the first time it touches each domain. If the standard headless browser is blocked, a full local browser becomes the default for that domain. The result is recorded: untested, tested and blocked, or tested and usable.

The judgment is made once. Later URLs reuse the conclusion.

The fallback has two levels: the standard headless browser is fast, cheap, and works on most sites; the full local browser is slower and more expensive, but closer to a real user. URLs that still fail in batch processing get one final chance: retry page by page through the full local browser.

Test once, remember the result, reuse it for thousands of URLs. That is orchestration.

## Rate Limiting

Then there is per-domain rate limiting: send requests to the same server only after a small fixed interval. Without rate limiting, the process gets blocked halfway through. With rate limiting, the collector respects each server while still maintaining throughput by running across domains in parallel.

All of this orchestration is solved behavior expressed as code:

```text
Adaptive batches:
PDF success rate >= threshold -> expand 1.3x
Otherwise -> shrink 0.7x

Page success rate >= threshold -> expand 1.5x
Otherwise -> shrink 0.6x

Browser fallback:
Standard headless browser -> full local browser

Browser lifecycle:
Every 20 URLs -> clean up tabs
Health check failure -> restart

Rate limiting:
Fixed interval per domain
Parallelize across domains
```

Could an agent “think about” the batch size? Yes. In an architect-executor setup, an LLM can adjust concurrency based on success rates.

But the question is: why introduce intelligence where precision is available?

Intelligence means uncertainty. Each run may make a different decision, and you cannot perfectly predict where the noise will appear. An `if` statement in code runs one million times and gives the same result one million times. Ask an LLM to make the same judgment 100 times. Can you guarantee 100 identical answers?

It is like a light switch in your house: press it, the light turns on; release it, the light turns off. It works the same way a million times. Now someone says, “We will use AI to control your light. It will consider brightness, mood, and room temperature before deciding whether the light should turn on.” It sounds intelligent, but you just want to use the bathroom.

This is not only about temperature settings and sampling. Your request hits shared infrastructure alongside huge volumes of other requests. Load balancing, compute-node differences, and routing can all affect the returned result.

There is a fashionable dismissal that programming is “just a bunch of `if...else`.” The implication is that this is somehow low-level or unimpressive. But `if...else` is precise, efficient, free, low-latency, and unsurprising. If a problem can be solved with an `if`, then the `if` is the optimal solution.

Replacing an `if` with an LLM is not progress. It replaces a deterministic system with a probabilistic one, then requires more engineering to handle the uncertainty it introduced.

If you can write an `if`, do not ask an LLM.

That is not conservatism. It is engineering common sense.

This is how the pipeline works. Next comes why agents cannot do it: six problems that look simple but break agentic systems in practice.

Next: [Part 3B — Where LLMs Shine, and the 90% Agents Would Destroy](/blog/agents-destroy-orchestration-en/).

---

Chinese original: [第3A篇：LLM 闪耀的地方——以及智能体会毁掉的 90%（上）](/blog/llm-shines-agents-destroy-zh/).
