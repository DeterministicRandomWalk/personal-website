---
title: 'Part 7: Context Accumulation — What Agents Do Not Naturally Possess'
description: 'Code is only sediment. What is scarce is the context compressed from failure, comparison, and sustained contact with a problem.'
pubDate: '2026-06-19T12:00:00Z'
heroImage: '../../assets/series-07-context-accumulation.jpg'
lang: 'en'
---

> Series: “We built a pipeline with tens of thousands of lines of code. Why could agents not do it?”

[Previous: Part 6 — The Leverage Gap.](/blog/leverage-gap-en/)

[阅读中文版。](/blog/context-accumulation-zh/)

## Quick Takeaways

- The requirement was one sentence. The code grew to tens of thousands of lines. Only those who crossed the distance between them know what was in it.
- Code is sediment, not the scene where events happened. Behind it are countless rounds of “where did it break this time?”
- Tools can transmit the lessons of other people’s failures, but they cannot take the first fall for you.
- Choosing the difficult path means having no beautiful progress bar in review meetings while also doubting yourself.
- AI is raising the threshold. The question is not “should we use AI?” It is “what can grow only through being present?”

The previous essay, Part 6 — The Leverage Gap, asked who gains more leverage from AI and how the career ladder is being reordered. The natural next question is: where does that leverage come from? One answer is context accumulation — something an agent does not naturally possess. This essay describes what that process actually looked like, including the detours, pressure, and doubt.

## A One-Sentence Requirement and a Real Timeline

By the fourth month, versions of the same scene kept recurring. New MCP demos, new features from open-source data-collection frameworks, and agent systems claiming to orchestrate tasks automatically kept appearing in different discussions. The atmosphere was always excited. He could not find the words to respond. He had already spent four months immersed in the problem. He had tried search-engine APIs, studied the open-source data-collection framework, and evaluated external data options. None was sufficient. But he could not explain why in three minutes. It was even harder to speak because his own direction had not yet been validated. On what basis could he challenge other people’s enthusiasm? At that point, none of the approaches — including his — had produced anything substantial. Saying “I am afraid this will not work” under those conditions sounded less like solving the problem and more like standing in the way.

What he really felt in that moment was: am I the fool walking down a path nobody else believes in?

The original requirement was only one sentence: “Collect ESG information from company websites.”

Sentences like that always look clean. You read one and think: how hard can it be? Write a crawler, add a regular-expression filter, done. The first version really did work that way, and AI genuinely helped with it. What happened next was messier than anyone expected.

## Three Detours

### First: A Search-Engine API

At the beginning, the first approach discussed internally was a search-engine API. The logic was intuitive: define a query — for example, “2025 large technology company ESG report filetype:pdf” — and call the API. Simple, explainable, easy for everyone to understand. A few weeks later, the problems emerged. The search engine returned frighteningly few results, and it would quietly attribute one company’s report to another. A user reported the issue. The entire approach had to be reconsidered.

In retrospect, that failure was valuable. What if the search-engine API had worked? That would have been good, of course, but it would also have meant that this stage offered no additional value. The ranking algorithm was not ours. We did not know how it worked and could not control it. When a third-party solution works, it is a commodity, and effort should go elsewhere. Where third-party solutions fail is where context accumulation begins.

### Second: An Open-Source Data-Collection Framework

Around the same time, an open-source data-collection framework that was attracting a great deal of attention came into view. It did look good. It was pleasant to use and solved many execution-layer problems. But it soon became clear that it solved the “body” problem, not the “brain” problem. It could crawl, but it did not know what to crawl. The self-hosted open-source version was also too rudimentary — they really wanted users to buy the SaaS service — and websites rendered with JavaScript often failed. Time spent studying its internal mechanisms eventually made clear why it could not solve the core problem. On top of that, deploying its Docker environment internally consumed a great deal of time in communication. The SaaS service was tried as well. In essence, the problem was being outsourced: use its search endpoint like a search-engine API, accept a black box, and hope it worked. If it did not, at least we had tried; it was no longer our fault.

### Third: External Data Suppliers

External data options were also brought to the table repeatedly. The hope and the pattern were always similar: presentation materials emphasized how complete and convenient the data was, and the proposition was easy to become excited about. But if external data was good enough, the path he was pursuing had no reason to exist. The question had to be evaluated seriously. There was a subtle pressure here. Promoting a new solution is more visible than deeply validating data quality. The person who performs that validation and concludes “not good enough” can easily appear to be standing in the way. He doubted his own path too, but repeated evaluation pointed to the same answer: external data was excellent, provided that you accepted its incompleteness. Saying that aloud always felt like pouring cold water on enthusiasm.

These were not three independent setbacks. They were three sides of the same fact: execution was never the hard part. Defining the problem was.

## The Difficult Path

By the fourth month, one fact could no longer be avoided: the work had to return to the original idea and start building from the beginning. Put that proposal on the table and most people reasonably asked why, when the existing solutions already seemed good enough. Answering those questions was itself part of context accumulation. It forced a distinction between “commoditized data” and “data embedded with judgment,” a distinction that could not have been articulated four months earlier.

The difficult path was chosen anyway. Without it, the pipeline would remain at the same level as other LLM applications: pleasant to use, but not something a real user would treat as a production tool. (Part 11 — The Evidence — will cover what users later said about this pipeline and other lightweight wrappers.)

The pressure was not only technical. Predictable engineering work is easy to track: ETL pipelines and data-quality checks can be divided into clear milestones. Exploratory work is unpredictable by nature. You do not know which edge case will appear this week, which path is a dead end, or when a breakthrough will arrive. After choosing the difficult path, there was often no beautiful progress bar to show in reviews, while more predictable projects continued delivering visible outputs. This was not the process’s fault. Regular reviews work well in the settings where they belong. But they made “remaining immersed in the problem” harder to understand and harder to see.

The doubt grew too. Every progress review felt like a silent interrogation: what exactly are you doing? Are you sure this is the right path?

## The Fragments Begin to Connect

Then unexpected pieces began to join. During the years spent doing academic research, there had been no shortage of work with data. Crawling, cleaning, and parsing had all been learned along the way because the research required them. The side projects built intermittently over the years — crawlers, parsers, automation — turned out to have been preparation for this moment. Fragmented memories suddenly connected, with the almost audible hum of pieces locking into place. This is another side of context accumulation: it is not always linear. Some context lies dormant for years until you enter a problem that happens to require it. Only then is it activated. But you have to be inside the problem.

It still was not enough. The baseline began to run, and new edge cases arrived one after another. Parts 2 and 3 already described them, so they will not be repeated here. The classification brain was the hardest part. Another dormant piece of context suddenly activated. Before LLMs became popular, he had spent a long time struggling to train a BERT classifier for research and publication. The methodology was entirely different, and today’s LLMs are much stronger than BERT at classification. What remained from that experience was not knowledge of a particular model, but intuition about classification itself: where boundaries become blurry, which features actually matter, and when a classifier will collapse. The two core concepts, “budget” and “priority,” surfaced late one night before sleep after another failure had reached a dead end. The next morning, he could not wait to give the idea to Opus. A few hours later, it delivered the first version of the code. The concept could not have appeared on the first day. It emerged naturally only after failure reached a point of saturation. This is the most characteristic way context accumulation produces something: not by thinking harder, but by remaining in the problem long enough.

One event from this process remains especially vivid. He was not unfamiliar with the domain. But after running a batch of companies, he still deliberately asked someone with deeper experience how they actually found this information. A few working habits and judgment techniques mentioned casually were more useful than anything a prompt could produce. The most valuable context was neither retrieved nor extracted through prompting. It appeared only because someone was genuinely present and asked the right person.

## Looking Back

Looking back, every approach was a reasonable attempt, and every one left something behind. The difference was not who had better judgment. It was who stayed with the problem longer. Someone who used the open-source data-collection framework only at the surface level might not understand why it was insufficient. That is not a question of ability. It is a question of depth of exposure. What happened later is equally revealing. External data options still fell short after deeper evaluation. And when the agent framework moved from demonstration toward real implementation, it encountered infrastructure and governance constraints far more complex than anything visible in the demo.

These outcomes were not coincidences. Behind them is a very common pattern: most people understand most tools only at the level of “I have used it.” In the AI era, the risk of this pattern has grown because AI has made “using something” easier than ever. The easier a path is, the easier it is for AI to standardize. The difficult paths — spending weeks touching the boundaries, understanding internal mechanisms, and accumulating judgment through failure — are precisely where context grows.

The distance between “used it” and “used it for months” is context accumulation.

## Context Is Compressed History

The preceding section described an experience. But what accumulated during that experience was not code. Code was only the final output. What actually grew was a hidden layer of judgment, slowly compressed from repeated failure, comparison, and contact with the problem. That is “context.”

An archaeologist excavates a wall and can see that it is twice as thick as the one beside it. Only the builder knows that a flood came that winter. The wall remains. The memory of the flood disappears, unless someone writes it down. Code is that wall.

When many people hear “context,” they think of a longer prompt, more complete documentation, or a larger knowledge base. Those things are useful, but they solve the problem of transmitting context, not producing it. Valuable context is compressed history. Why are PDFs processed later? Why does the browser degrade through a cascade? Why are some kinds of links deliberately skipped at first? Behind every rule is a specific failure. Those judgments were later written into code, thresholds, and stopping conditions. Before they were written down, they were only traces left by many rounds of failure. Code is sediment, not the scene where events happened. The system grew, but the half-conscious judgments formed during that growth — “this path does not work,” “I have seen this pattern,” “this is where we should stop” — were not written into any document. They exist only in the person who crossed that ground.

## Tools Are Narrowing the Gap, but They Are Not Magic

The previous section said that these judgments exist only in the people who crossed the ground. The AI ecosystem has no shortage of tools claiming to solve this problem. MCP places capabilities in the model’s hands. RAG lets the model retrieve documents. Long-term memory lets it remember the previous conversation. Harness engineering turns prompts, guardrails, and tool orchestration into reusable workflows. Agent orchestration allows multiple models to collaborate. They are genuinely narrowing the gap, but they are not magic.

They can help, but they cannot finish the job. Tools can reuse context that has already been produced, but they cannot initiate the first round of context production. MCP can connect an existing capability to a model; it cannot invent the capability boundary for you. RAG can retrieve information that has been written down; it cannot tell you which document should have existed but never appeared. Long-term memory can remember the previous conclusion, but someone first has to discover that conclusion. Agent orchestration sounds elegant: a primary agent assigns subtasks, each produces an MCP skill, and the skills combine to complete the objective. But who defines what “complete ESG information” means for a chemical distributor versus an oil giant versus a Japanese electronics group? All these tools assume that the hardest step has already been completed: someone first crossed the terrain for which no map existed.

The coding ability of LLMs is real. This pipeline is being refactored with Claude Opus 4.6, and it is writing production-grade code. But “turning a thought-through solution into code” and “knowing what should be written” are two different things. Code is the translation. Judgment is the original text.

## Push the Logic to Its Extreme

Twitter and WeChat Moments timelines never lack declarations of this kind: agents are disrupting everything, writing code is obsolete, AI will replace every engineer. One recurring claim is that a particular agent framework can improve productivity tenfold. But if you ask what remarkable thing the speaker actually built — a detail they rarely volunteer — it is likely to be another front-end page, another Snake game, another personal notes app, or another calendar tool. The interesting part is that these are precisely the most standardized scenarios. The training data contains countless nearly identical examples, so of course an LLM can perform well. This is not evidence that “agents can build anything.” It is evidence that “LLMs are good at reproducing patterns thoroughly represented in the training data.”

Not long ago, Tencent set up a booth outside one of its offices to help passersby install OpenClaw, and the scene became briefly lively. But the excitement reportedly faded quickly. How long can the novelty of a personal assistant that calls an LLM for every tiny task last? It is a reasonable question.

Fine. Push the claim all the way. If agents can build anything, why not build WeChat? More than a billion users; the market has validated it.

What does building WeChat require? Real-time delivery and guaranteed arrival for messages at billion-user scale; a financial-grade payment and risk-control system; a mini-program runtime that is essentially an application platform nested inside an application; recommendation algorithms and content moderation for Moments; real-time audio and video encoding; cross-platform, multi-device synchronization. Behind every item are years of engineering accumulation and countless lessons learned at real scale.

Or choose something less extreme: build a general search engine. A search engine essentially does what this ESG-collection pipeline does — find relevant content in the disorder of the web. The search engine operates at the scale of the entire web; this ESG pipeline covers only one vertical slice. Even this “small” problem required tens of thousands of lines of code and months of context accumulation.

The WeChat example is deliberately extreme. Nobody truly expects an agent to build WeChat from scratch. But it exposes a discontinuity that is usually ignored. Between “can write code” and “can build a system” lies context accumulation. The more complex the problem, the wider the gap.

But honesty is required here. None of this means that the threat from AI is unreal. Part 6 already argued that the leverage gap is reordering the entire career ladder. AI may be unable to build WeChat from nothing, but it is already compressing a great deal of middle-layer work.

The hype says, “agents replace engineers.” Reality is less simple: AI is raising the threshold. Once that threshold rises, context naturally divides into two categories. One can be deposited into a system and used smoothly by AI. The other cannot; it grows only through staying with a problem for a long time. The first is an engineering task. Do it well, and the boundary of AI capability moves outward. The second is what this essay is really about.

## Why LLMs Structurally Cannot Do This

The difficulty of replacing context accumulation is not merely an empirical observation. There is a mechanical reason behind it.

Imagine a radio playing every station at once. What you hear is the average of all voices: sometimes astonishing, but always blurry. That is the state of a large language model running without specific context — the statistical average of the internet.

Put plainly, an LLM is a probability machine. From the 2017 paper *Attention Is All You Need* to today, every step is traceable and reproducible engineering. It is not magic, not consciousness, and not the “human-like emotion” suggested by some headlines. But most people did not first encounter LLMs through papers. They encountered them through headlines about ChatGPT. Computers once seemed miraculous to a previous generation; LLMs seem miraculous to this one. The amazement is reasonable. The technology really is changing how work is done. But it is technology built by humans, not a miracle that descended upon us. Understanding that is necessary to see where its boundaries are — and why context accumulation does not lie within them.

Context engineering — Part 5B showed what it looks like in practice — turns the dial to a specific frequency: the part of the training data most similar to your problem. The more precise the prepared context, the more appropriate the “station” the model invokes. MCP, agent frameworks, and harness engineering are all, in essence, tuning controls. They give accumulated context to the model at the right level of granularity.

But the dial can be turned only if someone first knows which frequency to choose. That frequency is the product of context accumulation.

The value is not in the model’s raw output. It is in the engineering that shapes that output. The model is the engine; engineering is the steering wheel, route map, and guardrail.

## What This Mechanism Looks Like in Practice

The abstraction is finished. What does it look like in actual work?

One way to observe it is to look at the work in front of you. It divides roughly into two piles:

- **One pile can be written as rules, workflows, prompts, and checklists — context that can be given to an LLM.** This context can be deposited into a system. Do that well and AI can use it. The act of structuring it is itself valuable; perhaps nobody on the team has yet realized it can be structured. But there is an unsettling paradox. The preceding essays spent a great deal of time explaining why AI could not build this pipeline. Once the pipeline is clearly defined, structured, and deposited into a system, however, it becomes standardized. Standardized things are commodities, and the fate of a commodity is replacement. To be honest, properly structuring even this first pile will take most teams years. Most institutions have not begun. The window is longer than the panic suggests, but it is not infinite. The irony is that whoever structures their context first is amplified by AI first — while that amplification simultaneously accelerates the dissolution of the existing way of working.
- **The other pile cannot be stated clearly, written into documentation, or even acquired through deliberate “study.”** This refers to domain intuition and technical judgment. Organizational politics and interpersonal management are entirely different dimensions, more complex than the subject here and outside this essay’s scope. This context grows slowly by remaining with the problem, participating in discussions, and noticing what is happening nearby. For example: “where this kind of company usually hides ESG information,” “why a PDF in this format is probably an older report,” or “what a sudden change in this metric usually means.” These are not things someone sits down and decides to learn. They become part of judgment through presence, attention, and participation. These are places AI cannot yet reach — and places worth moving toward deliberately.

The pattern is a cycle: structured context → commodity → the next unstructured problem emerges → structure it → it becomes a commodity again. There is no visible end to the cycle. That sounds heavy, but it is an unavoidable reality, and not a new one. Industrial automation and offshore outsourcing have already turned the same cycle several times. What differs now is the speed, and the fact that it cuts into a layer closer to judgment. What this means in practice — what can be delegated, what cannot, and how to find the boundary — is the subject of the next essays, Parts 8A and 8B.

Next: Part 8A — The Delegation Problem: Why You Cannot Simply Throw It Over the Wall.

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
| **07 — Context Accumulation** | **You are here** |
| 08A — The Delegation Problem | Why you cannot simply throw it over the wall |
| 08B — The Autonomy Spectrum | Finding the right level |
| 09 — The Other Extreme | When skepticism becomes paralysis |
| 10 — Two Rooms | Demo enthusiasts vs. domain skeptics |
| 11 — The Evidence | The pipeline as evidence |
| Bonus — The Counterargument | AI argues against the entire series |
| Bonus — Standing in the Middle | The thought that arrives in the middle of the night |

## References

1. Vaswani, A. et al. [“Attention Is All You Need.”](https://arxiv.org/abs/1706.03762) 2017.
2. Business Insider. [“I Went to an OpenClaw Installation Event at Tencent’s Office.”](https://www.businessinsider.com/openclaw-installation-event-tencent-cloud-singapore-ai-agent-lobster-2026-3) 2026.
