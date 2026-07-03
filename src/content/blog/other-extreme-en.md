---
title: 'Part 9: The Other Extreme — Why “LLM Is Dead” Is Also Wrong'
description: '“LLMs are not the endpoint of AGI” may well be true; it does not imply that LLMs have no value in real systems.'
pubDate: '2026-06-22T12:00:00Z'
heroImage: '../../assets/series-09-other-extreme.jpg'
lang: 'en'
---

> Series: “We built a pipeline with tens of thousands of lines of code. Why could agents not do it?”

[Previous: Part 8B — The Autonomy Spectrum.](/blog/autonomy-spectrum-en/)

[阅读中文版。](/blog/other-extreme-zh/)

“LLMs are not the endpoint of AGI” may well be true; but it cannot directly imply “LLMs have no value in real systems.” The former is a research judgment. The latter is a product judgment. Compressing the two into “LLM is dead” is just another low-resolution narrative.

Previous essay: Part 8 — The Autonomy Spectrum: The Real Question Is Not “Whether,” but “Which Layer” (Part B). The problem with the “full autonomy” narrative is not that none of it is true, but that it miswrites local validity as global validity, and layered expansion as total replacement.

Part 8B discussed one kind of flattening:

compressing a question that should be judged by layer, block, and maturity into the sentence “agents will take over everything.”

This essay discusses the mirror image on the other side: not exaggerating local capability into total replacement, but compressing the limitation of one research route into the invalidity of the whole technology. It is not entirely wrong; it often captures part of a real problem. The real issue is:

it compresses “the limitation of one research route” into “this technology has no value for real systems.”

Structurally, this step is very similar to the role Part 6 played relative to the first five essays.

The first five essays argued all the way through that AI cannot autonomously build systems. The easiest conclusion to draw from that is: “Since it cannot do these things, maybe it is not that useful.” What Part 6 really did was turn that lazy extrapolation around: precisely because judgment is scarce, AI’s leverage becomes enormous.

After Parts 8A and 8B, there is almost the same lazy extrapolation.

Since the “full autonomy” narrative has been dismantled, since the model is not the endpoint, since it has clear ceilings, does that mean this route itself is not worth seriously building on?

Many people compress this step into an even shorter, more conclusion-like sentence: “LLM is dead.”

This essay turns that conclusion over. Its focus is not to re-argue that “AI is useful,” a judgment that has almost become common sense today, but to handle another mistaken inference that becomes easy to slide into after resisting hype.

There is also a background that needs to be made clear. The reason the earlier essays in this series spent so much space pushing back against AI hype was not that we think AI is useless. Quite the opposite: because “AI is powerful,” “AI will reshape work,” and “if you do not use it, you will fall behind” have almost become default assumptions today — the ambient noise of the environment — what most needs to be added are precisely the boundaries, costs, failure modes, and judgment conditions that hype narratives automatically omit.

That is also why the earlier essays may sometimes read as anti-AI. But the real position has always been: the value is enormous; and because the value is enormous, it cannot be understood through low-resolution narratives. This is where the “LLM is dead” narrative is truly wrong. The mistake is not saying that LLMs have limits. The mistake is translating a judgment about ultimate capability directly into a judgment about present engineering value.

## What Is Actually Being Mixed Together Are Three Sentences

In public discussion, three sentences are often mixed together:

1. LLMs have clear limits.
2. LLMs are not the final route to AGI.
3. LLMs have no long-term value for real systems.

The first sentence is probably right. The second may also be completely right. But the third does not automatically follow from the first two.

What is really happening here is not reasoning, but slippage. From “this technology is not everything,” it slips to “this technology is nothing.” From “this route has a ceiling,” it slips to “building systems with it today is a wrong path.” From “it is not the endpoint,” it slips to “it is not worth seriously building infrastructure around.”

That slippage is what this essay is about.

## What LeCun Is Actually Saying, and How People Misread It

Yann LeCun is one of the most representative figures in deep learning, and he has long been one of the public voices questioning whether the current LLM route alone can reach higher-level intelligence. Many people’s impression of him does not come from his complete arguments, but more from short social-media clips, truncated retellings, and forceful impressions detached from context: as if even someone like him is already saying that the LLM route is not very interesting anymore and is basically a dead end.

If he is understood only through those short lines, the question is usually already misread from the beginning. If we discuss only the strongest and most serious version of that camp, Yann LeCun is of course worth taking seriously. His strongest point is not “LLMs are useless,” but: if the goal is general intelligence with human-level world understanding, causal reasoning, and planning ability, then autoregressive text prediction alone is not enough. This is a research judgment.

It discusses:

- what kind of architecture is more likely to lead to higher-level intelligence;
- where the capability boundaries of language modeling lie;
- whether world models, multimodal learning, and representation prediction are more important next steps.

This is serious judgment. But it discusses which route leads to which goal. It does not automatically answer a completely different question:

whether LLMs have enormous value in today’s product and engineering reality.

These two questions are not the same question. One asks about research routes. The other asks about engineering leverage. Compressing them into “LLM is dead” is not seeing more deeply; it is welding two judgment systems together by force.

## The Error Happens in the Apparently Natural “Therefore”

“LLMs cannot realize general intelligence.”

Therefore —

“LLMs are not worth investing in.” “LLMs are only transitional technology.” “Things built with LLMs will all have to be torn down sooner or later.” “Building LLM products seriously today means choosing the wrong side.” None of these “therefores” holds automatically.

Because they secretly cross a huge judgment gap:

from research objective to engineering value.

It is like saying:

- spreadsheets cannot automatically run a company;
- databases are not the final form of organizational intelligence;
- search engines do not understand the world;

but nobody would therefore conclude:

so spreadsheets, databases, and search engines are not important in real systems.

A tool does not need to be the endpoint in order to become infrastructure.

## This Is Actually the Same Error as Part 8B

In Part 8B, the problem was compressing:

- some task blocks can be highly autonomous,

into:

- therefore the whole system can be fully autonomous.

In this essay, the problem is compressing:

- one architectural route may be insufficient for AGI,

into:

- therefore it has no long-term value for real systems.

The concrete positions on the two sides are different. But the flattening mechanism is the same:

rewriting a high-resolution judgment as a low-resolution conclusion.

The former writes local validity as global validity. The latter writes insufficiency for a specific goal as general invalidity. This is also why both are so well suited to headlines. Headlines do not like layers. Headlines like positions. Engineering needs exactly the opposite: layers.

## The Question That Matters to Engineering Teams Is Not That Question

If you are actually building systems today, the real questions are usually not:

- whether LLMs are the endpoint of AGI;
- whether Transformers will be replaced;
- whether world models will win within five years.

The questions you should actually ask are:

- what is the most expensive and hardest-to-structure part of this task;
- can LLMs create visible real leverage here today;
- which parts must be backed by deterministic systems;
- which failure modes are already clear enough today to be engineered around;
- can this combination run stably now.

The research community of course needs to ask: what is the next architecture? But product teams first need to ask:

which capability, combined with what system structure, can stably produce value today.

The leverage is real. If you truly know where AI is strong and where it is weak, which parts can be amplified and which parts must be personally guarded, then it is not a dispensable toy. It is a system component that can multiply your effective output.

Conversely, if you both overestimate it and fail to understand it, of course it will look like an unreliable half-finished thing. The question is not “is it miraculous or not,” but whether you can place it in the right position.

Both questions matter, but they are not the same question.

## The Pipeline Shows Exactly Why This Distinction Cannot Be Skipped

If you look only at the goal of “general intelligence,” this pipeline proves no endpoint judgment: it does not prove that LLMs will become world models, does not prove that autoregressive text prediction is enough to support robotic planning, and does not prove that the current architecture is the endpoint of AI.

It proves something more modest, and more important:

in task blocks dense with language, semantically ambiguous, and hard to exhaust with rules, LLMs can already provide very real engineering leverage.

In other words, where AI is heavily used here is not the rule-friendly scraps at the edge, but the layer where traditional deterministic methods begin to fail and where “judgment” is genuinely needed. If this pipeline has a “brain,” that layer is basically where it sits.

What LLMs do in this pipeline is not world modeling, but the semantic judgments hardest to exhaust with rules: link relevance, domain and page semantics, classification in fuzzy context, and other language judgments that humans would struggle to hard-code in advance.

These are precisely the things deterministic systems find hardest to do, while real work contains them everywhere. Of course you can keep trying to approximate them with rules, templates, keyword blacklists and whitelists, and longer and longer exception tables. But after a certain point, you discover that this is no longer a matter of “spending a bit more engineering effort.” The task itself has entered a region that requires semantic judgment, context absorption, and fuzzy-boundary handling.

In that sense, the model is not decorative trim on the edge of the system. It is the cognitive core of some key links. Everything else — budgets, retries, rate limits, logs, domain boundaries, fallbacks, audits — is held up by deterministic engineering.

Without Opus, this project would not have been impossible to build.

But it would probably have been delayed by months; and under organizational friction, requirement pull, and the steady erosion of user patience, the probability that the project would “slowly die” would also have risen. Not because the core idea was invalid, but because the owner would have been dragged into endless pits, with no time to assemble the truly critical structure.

With a sufficiently strong model, the change is not “you no longer need judgment,” but that you no longer need to assemble a whole small team first just to know whether an idea stands. In the earlier exploration stage, this is especially important: one owner plus one week of intense pushing is often enough to try the core path, eliminate wrong directions, and identify the parts truly worth continued investment. Early exploration often needs not a direction flattened prematurely through average consultation, but speed, focus, and a route that can be falsified quickly.

Besides fuzzy semantic judgment, another equally important piece of leverage appears in coding itself — and writing code is probably the first domain where this capability was widely felt in a way that was simultaneously advanced, common, and attractive. The change is not that the model has architectural judgment for you. It is that when direction, boundaries, and acceptance criteria remain in human hands, much of the implementation, refactoring, glue code, and local repair work that once had to be slowly typed by humans can be substantially compressed. Coding reality is therefore gradually moving from “human-led, AI-assisted,” to side-by-side progress, and then, at many implementation layers, increasingly toward “human sets direction and constraints; model handles most expansion and filling in.”

This is why we must both oppose hype and admit the size of the leverage. Not because AI solved the problem for you. Because it dramatically compresses the distance from “there is a direction” to “we know whether this direction is worth continuing.”

This is not “LLMs can do everything.” Nor is it “LLMs cannot do anything.” It is a more boring but truer statement:

LLMs are already very useful in one class of capability, and what turns that usefulness into a product is the system.

So saying they are “dead” is not too sharp. It is judging at the wrong level.

## Next-Generation Routes Are Worth Researching, but They Are Not Today’s Refutation

This is why the sentence “a better next-generation route is coming” does not by itself refute the value of LLMs today.

If we look beyond the current LLM paradigm centered on autoregressive language modeling, of course there are many new directions worth serious work. If they succeed, they may of course surpass today’s LLMs on some genuinely critical abilities.

But the keywords in that sentence are:

if.

And:

future.

The constraint engineering teams face is usually:

today.

The system you deploy today does not automatically lose value because a theoretically superior future architecture might appear. Otherwise no generation of infrastructure would be worth building.

Databases are not the endpoint. Cloud computing is not the endpoint. Search engines are not the endpoint. None of them is “the final answer.” But that has never stopped them from becoming infrastructure for a generation of systems.

Search is actually a very fitting analogy. If we go back twenty years, when web search first entered everyday life, the shock was real. It greatly changed how we obtained information, changed how many industries were organized, and made everyday life far more convenient. But even today, you would not understand search as a product that “100% completes judgment for you.” It does very well, so well that it has become social infrastructure; but what to search for, which result to click, which source to trust, and how to turn information into a decision remain human matters.

LLMs are not magic, not the fulfillment of a dream in one step, and they will not remove judgment from systems completely.

But they may very well push the whole system forward in the same way search did — far enough that people who fail to keep up may eventually discover that they are no longer operating on the same efficiency scale.

They may not be the final cognitive architecture. But they have already changed the engineering economics of many language tasks. That is enough to make them important infrastructure.

This is precisely why phrases like “LLM is dead” spread so well. Like “full autonomy,” they are short, hard, and sound like a verdict. They compress a problem that requires distinctions into a choice of position.

But people who actually build systems sooner or later must return to the questions that headlines deliberately skip: what the input looks like, how failure is exposed, how fallback is designed, which judgments can be delegated, which cannot, which abilities are already valuable today, and which remain research visions. Because these questions do not have one-sentence answers, headlines will always be louder than engineering.

## What Is an LLM, Then?

Once both hype and reverse-dismissal are stripped away, what is the LLM of 2026 more like? It is more like a revolutionary advance in language processing.

That sentence does not sound as grand as “general intelligence,” nor as stimulating as “dead end,” but it is closer to reality. Language is of course not everything; but contracts, reports, code, and a large amount of classification, extraction, summarization, judgment, and explanation work are already highly dependent on language processing.

If a technology creates a real leap along this dimension, it is already important enough. It does not first need to prove that it will become “the final architecture of intelligence” before it deserves to be taken seriously.

## Closing: The Other Extreme Is Wrong Because It Turns a Research Question into a Product Question

If this essay is compressed into one sentence, what it really says is: “LLMs are not the endpoint of AGI” may well be true; but it cannot be directly rewritten as “LLMs have no value for real systems.” The former is a research judgment. The latter is a product judgment. Compressing the two into “LLM is dead” does not raise resolution; it merely flattens another kind of complexity.

So after Part 8B, what needed to be added was not a new slogan, but another equally important distinction:

not being the endpoint does not mean having no value.

As for what AGI ultimately is, how it should be defined, and which route truly leads to it, those are not questions we are most qualified to settle today. Those larger questions can be left to people better positioned and equipped with longer research horizons.

What we can see now is something more modest and more reliable: this is already a very powerful tool, and its power is not an abstract slogan but something felt every day in real systems. The place it is most worth using may not be satisfying some ultimate fantasy. Often its more practical meaning is compressing the mechanical, repetitive, time-consuming parts that still have to be done, allowing the system to move a large step forward, and returning human time to judgment, creation, or simply more interesting things.

This pipeline does not prove that LLMs are everything.

When a capability is already strong enough and placed into the right system structure, it can very well not be the endpoint and already be infrastructure.

What is truly worth protecting is not some pride from a “purely hand-built era,” but the core abilities that remain hardest to replace in the short term: judging boundaries, recognizing distortion, defining problems, deciding when to stop, when to change, and when responsibility can no longer be handed further down.

The people least likely to be replaced in the next round of change are those who can fully use AI’s leverage without outsourcing these abilities.

Next: Part 10 — Two Rooms: Why Demo Lovers Never Finish, and Domain Experts Never Start.

This is Part 9 of the series. [Start from the beginning.](/blog/why-this-series-exists-en/)

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
| 08A — The Delegation Problem | Why you cannot simply throw it over the wall |
| 08B — The Autonomy Spectrum | Finding the right level |
| **09 — The Other Extreme** | **You are here** |
| 10 — Two Rooms | Demo enthusiasts vs. domain skeptics |
| 11 — The Evidence | The pipeline as evidence |
| Bonus — The Counterargument | AI argues against the entire series |
| Bonus — Standing in the Middle | The thought that arrives in the middle of the night |
