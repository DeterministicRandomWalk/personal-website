---
title: 'Part 11: Evidence — What Happened After We Actually Built It'
description: 'The investment team expected another demo. What they got was a production system. The difference was not the model. It was engineering.'
pubDate: '2026-06-24T12:00:00Z'
heroImage: '../../assets/series-11-evidence.jpg'
lang: 'en'
---

> Series: “We built a pipeline with tens of thousands of lines of code. Why could agents not do it?”

[Previous: Part 10 — Two Rooms.](/blog/two-rooms-en/)

[阅读中文版。](/blog/evidence-zh/)

The investment team expected another demo. What they got was a production system. The difference was not the model. It was engineering.

Previous essay: Part 10 — Two Rooms. Demo lovers never finish. Domain experts never start. The pipeline delivered because it listened to both sides.

The previous ten essays were arguments. This essay is evidence.

Evidence is not “can the model answer questions in a demo.” Evidence is whether, after the system is built, a real team begins to depend on it.

More specifically:

The evidence for a production system is not that it can be demonstrated, but that it begins to enter the team’s schedule, judgment process, and responsibility structure.

## The Starting Point

The investment team’s expectations were actually very low. Not because they were cynical, but because they had experience. They had seen many AI demos before. They had heard those promises. What did the annual plan say? The same wording every institution uses when writing about AI projects:

Explore AI applications.

The time allocated to it was 5–10%, and the priority was medium-low. The word “explore” says everything. “Explore” means nobody expects it to truly run. The budget is approved for learning, not for production. The team politely attends the demo, nods, and then goes back to doing the work the old way.

That was the starting point.

## What Was Built

Not a chatbot. Not a wrapper around an interface. Not a demo. A tool fully integrated into the daily investment workflow. This series has mainly discussed the first layer of the project: a production-grade ESG data collection engine. What it does is simple:

It systematically collects as complete a set of ESG-related materials as possible from thousands of corporate websites, then passes them to downstream analysis workflows in a traceable and auditable way.

More concretely, it:

- crawls specific ESG-related information across thousands of corporate websites;
- uses LLM-driven semantic judgment to classify links;
- handles JavaScript-heavy websites, tracks redirects, and manages cookies;
- downloads PDFs and scores them for relevance;
- respects `robots.txt`, manages request frequency, and runs within budget;
- produces traceable, auditable output at every step;
- feeds structured data into the team’s downstream analysis pipeline.

This has already been discussed repeatedly in the previous ten essays. There is no need to expand it again.

In one sentence:

The LLM handles the layer that requires language understanding. Deterministic code handles the layer that requires control, precision, and reliability.

That is the architecture the previous ten essays have been describing.

## Why It Worked

The team rarely found problems in the output. Occasionally they did — usually because some issue had not been clarified in advance, or because the pipeline had missed an edge case — and they gave feedback. That feedback was integrated into the next iteration, and the same mistake did not recur. The improvement loop was fast and predictable. The team could see exactly where and why each change happened. But the most important point is this:

It worked not because the AI model was so powerful.

In real systems, model selection does not end with “use the strongest one.” It is not a matter of belief. It is a matter of system design.

For simple classification, format conversion, and local extraction, a smaller model may already be enough. For complex reasoning, long context, and multi-step tasks, weaker models quickly hit a capability wall. So the mature approach is never to blindly chase the strongest model, nor to assume all models are basically the same. It is to know which task block needs how strong a model, where you can downgrade, and where deterministic code and human judgment must provide the backstop.

The strongest model running naked is worse than a strong-enough model placed in the right layer.

This also explains another often misunderstood point: this pipeline was not “made by the model itself.” Even if you gave a very strong model a long time, it would not automatically converge the entire chain — not because it is not strong enough, but because convergence requires feedback, constraints, acceptance criteria, and responsibility structure. Generation is not convergence. Being able to write a piece of something is not the same as forcing an entire system into a deliverable state.

It worked because of:

- Controlled input pipelines. Every piece of data entering the system passes through defined, auditable steps. There is no black box.
- Predictability. The same input produces the same output. When behavior diverges, the system records why.
- Coverage. The engine covers the complete company list the team needs, not a curated subset that makes the demo look good.
- Traceability. Every decision the system makes — which links to follow, which PDFs to download, which pages to classify as relevant — is logged and can be reviewed.
- Auditability. The team can trace any output back to its original source. In a regulated investment environment, this is not a nice-to-have. It is a basic requirement.

None of these things naturally grow out of “model capability.” They come from engineering around the LLM. The model is smart. The pipeline is reliable. What the team actually uses is the combination of the two.

## How They Use It

Before investment meetings, the team wants the model output to be ready. Not because they blindly trust it, but because manually collecting and organizing ESG data used to be one of the most tedious parts of meeting preparation, often taking hours or even days.

Now they do not have to.

The system does it for them — comprehensively, covering all the companies under management, not only the few they have time to research manually. But — and this is the key — the scoring is still theirs. The methodology is still theirs. The investment decision is still theirs.

The system collects, classifies, and organizes. The team verifies, judges, and decides. The mechanical part is automated. The expert part remains in the hands of experts.

This is not replacement. This is what “copilot-style collaboration” really means when it is built correctly.

Many real tasks are also not solved correctly in one shot. Even with a strong model, if you ask it to generate correct chart code directly from a table, the first version often reads the wrong field, chooses the wrong chart type, mishandles dates, groups, or missing values; only after several later rounds does it gradually correct itself.

That it can do the task is progress. That it cannot do it in one shot is the boundary.

The collection pipeline is the same. What makes the result land is not one generation, but iterative convergence with feedback. This is also why a more automated agentic mode is not naturally more advanced.

Formed problems can be automated more. Still-forming problems can only be collaborated through.

When the goal is clear and the constraints are stable, higher automation can of course be easier. But in many real business settings, people do not first fully know what they want and then outsource the task wholesale. The goal itself often grows slowly through feedback.

Full delegation too early is more likely to drift off course.

The better approach is often for people and systems to move while looking, generate while correcting, let the goal gradually become visible during the work, and let people gradually learn where they can let go and where they must personally watch.

## The 7:58 a.m. Request

There is also one small scene that explains the point better than many formal evaluations.

One morning at 7:58 a.m., a colleague came to the developer. She needed the system to generate a report for a candidate company as soon as possible, because that company was going into an investment decision meeting that afternoon.

The timing itself says a lot. The developer technically started work at 9 a.m. and was still eating breakfast, but she could not wait, because her team needed the model output. If the report could be generated in the morning, the team could review it that afternoon and make a decision. If not, it would have to wait until the next month.

This was not a demo scenario.

A demo only needs to prove “can the model answer.” In a real workflow, the question becomes: can the system, within the rhythm of meetings, candidate lists, and actual decision timelines, move a company into a discussable state?

For the team, this difference matters.

In the past, if the materials were not ready, the discussion had to wait. Now the system compresses the preparation time, and the candidate company can enter the discussion that day.

This does not replace investment judgment. Quite the opposite: it allows investment judgment to happen in time. The model is not deciding for you. It lets you have enough time to judge:

A demo proves possibility. A production system changes the schedule.

The evidence for a production system is not that someone says it is good, but that someone begins waiting for its output in real work.

## The Reaction

The investment team was surprised. Not surprised by AI — they had seen AI demos. What surprised them was:

This thing actually works in production.

The data was comprehensive. Some companies had thousands of ESG-related documents over the past few years, as well as PDFs hundreds of pages long.

The output was traceable. The system could explain what a conclusion was based on. It integrated into their workflow without creating disruption.

Their original expectation — another exploration, another demo, another thing that looked good in a demo but did not work in reality — was wrong. And they were happy to admit it.

In one meeting, a portfolio manager described the difference very directly: what separated this system from other tools was not that it “also used an LLM,” but that it could actually filter, collect, and organize complete ESG materials scattered everywhere and appearing in different formats.

They felt empowered by the system. Not threatened. Not replaced. Empowered.

Where is the difference between “empowerment” and “threat”? Entirely in the architecture.

If the system tries to replace your judgment, you feel threatened. If the system does the drudge work for you and lets you focus on judgment, you feel empowered.

The underlying technology may look similar. The relationship between human and system is completely different.

## They Did Not Fail to Understand AI. They Knew What They Wanted.

There is another point that also explains why this project ultimately stayed.

In a long meeting with the team, the author was actually a little worried: would they see this project as just another AI demo? Would they fail to distinguish it from the various ESG AI tools, data providers, and research platforms in the market?

That worry did not come from nowhere.

At the time, there were indeed external ESG AI data companies in contact with the team lead, and AI research/search services like AlphaSense were also on the table. These tools sounded advanced, and all of them could tell a polished AI story.

But the team ultimately, and very clearly, did not take that path.

The reason was not that they were conservative, nor that they did not believe in AI. Quite the opposite: they valued AI’s potential and were happy to see this internal project continue to develop. But they had a basic judgment: the reason the team exists is not that the market lacks data, nor that nobody can generate summaries, but that they have their own fundamental judgment logic.

What they needed was not a black box that reached conclusions for them, nor a general tool that threw materials into a search box and forced analysts to judge everything again themselves. What they really needed was this: the system should handle the scattered, messy, repetitive, time-consuming material collection and initial organization, while preserving their methodology, judgment rights, and final responsibility.

An ordinary demo shows:

The model can also answer questions.

This system showed:

We can find the relevant ESG materials for a complete universe of thousands of companies, organize them in a traceable and auditable way, and let the investment team use them inside its own judgment framework.

Both things look like AI, but to the team they are completely different.

The former may weaken their position as judges. The latter expands their judgment radius.

The team was not persuaded by AI. They were persuaded by a system that matched their investment philosophy.

That is slower than being impressed by a demo.

But it is also more stable.

## Another Contrast

This difference can also be seen in other AI projects inside organizations.

During the same period, there were also some LLM projects more oriented toward general wrappers or lightweight customization. They were not valueless, and they were not lacking effort. On the contrary, many of them were reasonable at the start: first package the capabilities of major providers, solve permissions, data security, access control, and internal usage boundaries; or add a bit of search, summarization, Q&A, and structured output to existing tools, letting users decide how to use them.

These directions all sound right.

But once they really move forward, they easily fall into another dilemma: large amounts of time are consumed by governance, permissions, approvals, data-provider evaluation, integration processes, and internal rule discussions. Meanwhile, what frontline business users receive is too light — neither a complete product nor a directly verifiable workflow.

So users develop a very typical feeling:

Too good to throw away, too bland to really eat.

To say it is useless seems unfair. To say it is useful makes it hard to specify exactly which key problem it solves.

More troublesome still, these tools are often hard to test.

If the system only gives a summary, a search result, or a chat answer, users do not know where to begin verifying. If it is wrong, was the model wrong? Was the input wrong? Was the prompt wrong? Was a permission not enabled? Was the data source incomplete? Or was the business definition unclear in the first place?

Users feel they have nowhere to start. Developers feel users are not cooperating with testing. Both sides feel the other side is not pushing the work forward.

This is not simply an attitude problem. It is a product-structure problem.

If output does not enter the user’s real workflow, the user has a hard time giving high-quality feedback. If feedback cannot be tied specifically to inputs, rules, evidence, metrics, and final judgment, developers also have a hard time pushing the system to the next layer.

So for many lightweight customization projects, the most painful part is not that the first version cannot be built, but that after it is built, it cannot converge.

They are hard to classify directly as failures, but also hard to truly bring into production. They stop in an awkward place: they seem to have some value, but they are hard to become something users rely on every day.

This forms a strong contrast with this pipeline.

This pipeline did not start from “let us first build a general entry point.” It started from a concrete, heavy, repetitive, time-consuming business problem: thousands of companies, scattered disclosures, different formats, relevant ESG materials that must be filtered out, and every step must be traceable, auditable, and reviewable.

It did not first ask:

What can we package the model into?

It first asked:

Where exactly is the investment team stuck?
Which inputs must be controlled?
Which results must be verifiable?
Where must human judgment remain?

That difference determined what happened next.

General wrappers easily fall into governance and interface problems. Lightweight customization easily gets stuck at “somewhat useful but hard to test.” Deep customization is slow, but once input, scope, evidence, judgment, and responsibility structure are connected, users can truly begin to give feedback, and the system can continue converging.

The meaning of the contrast is not who failed to work hard enough. It is what kind of product structure allows feedback to actually happen.

So the difference between a production system and a demo is not only technical depth. It is also whether the system gives users an object they can test, question, modify, and take responsibility for.

## Portability

The team is now actively asking to extend the tool beyond ESG: risk factors, governance indicators, regulatory risk exposure.

The architecture supports this.

The same pattern — LLMs doing semantic classification, deterministic code doing everything else, domain experts defining what “relevant” means in each new dimension — applies directly.

This is not a coincidence.

It is the result of building a composable architecture rather than a one-off architecture. The pipeline does not “know” ESG. What it knows is: collect structured information from unstructured web sources, classify relevance according to criteria defined by domain experts, and produce traceable output.

ESG is one investment instance. There can be other investment and even non-investment instances.

Portability validates the design. It was not overbuilt for a single use case. It was appropriately designed for a class of problems — and the scope of that class is much larger than people imagine.

Interestingly, deep customization that at first looks like “reinventing the wheel” may, in the end, settle into a genuinely reusable framework.

Truly reusable frameworks often do not begin from abstract platforms. They grow out of a specific problem that is deep enough and real enough.

## What This Proves

The whole series has been arguing one thing:

Composition — LLM judgment + engineering precision + human domain expertise — is the right architecture for production-grade AI systems.

This is the evidence.

This pipeline proves several things:

- Demo-lover wrappers will not work. A general ChatGPT interface cannot crawl thousands of websites, handle JavaScript navigation, manage budgets, respect `robots.txt`, score PDFs, and produce auditable output. The 90% matters.
- Domain experts do not need to retreat. The system does not invent investment decisions. It collects data — traceably, auditably, comprehensively. Expert judgment has not been weakened. It has been extended.
- The “agents can do everything” narrative will fail. An autonomous agent given the instruction “collect ESG data from corporate websites” would run into every problem described in Parts 3 through 8: orchestration failure, cost explosion, silent tool errors, goal drift.
- The “LLMs are dead” narrative is irrelevant. The LLM inside the pipeline is working. It classifies links with an accuracy no rule system can match. Whether it is the path to superintelligence does not matter — it is the path to a production-grade ESG data engine used every day by an investment team.

From beginning to end, the point was never “AI does not work,” nor “AI can do everything.” It is one sentence:

Build it right.

Build it right means: models do judgment, code does control, domain experience sets direction. Traceable. Auditable. A tool for experts, not a replacement for experts.

This is what we built:

The team uses it. They trust it. They want more.

That is the evidence.

## There Is a Second Layer

At this point, this series has actually only finished the first layer:

Why “collecting ESG information” already requires a combination of engineering, models, and domain expertise.

But the project does not stop at the first layer.

After the materials are truly collected, there is a second-layer problem: how should the collected ESG documents be read systematically? How does disclosure language become metric judgment? How are model judgments constrained by evidence? How do analysts override, correct, and confirm, instead of being forced to believe a black-box answer? And ultimately, how do these judgments enter a workflow that portfolio managers will actually use?

That is what another series will discuss.

If the theme of this series is:

Why agents could not build this pipeline.

Then the next series will discuss:

Once the pipeline has truly collected the documents, how can LLMs turn them into reviewable, traceable, responsible investment judgments?

The answer is not simply another RAG system.

This set of essays discussed how capability is placed into a system.

The next set of essays will discuss how judgment forms inside a system.

But that is for the next set of essays.

## Closing

The main body of this series ends here. One pipeline. One argument.

AI is good at understanding meaning. Code is good at guaranteeing behavior. Experience decides when to use which. None of the three can be missing.

This is the beginning. And the end.

It does not close with theory, but with a production system used by a real investment team, helping them make better decisions faster, more comprehensively, and at greater scale.

This story is finished.

But not completely finished. There is one more thing: we did the Karpathy test. We fed the whole series to an LLM and asked it to tear down our argument. Multiple rounds of attack and defense, honest responses, and what we learned from the exercise:

Bonus Essay — Rebuttal.

## Series Review

| Part | Title | Core sentence |
| --- | --- | --- |
| 1 | The Impossible Task | A portfolio manager needs ESG data from 5,000 websites. Chatbots and regex both fail. |
| 2 | How 7,400 Lines Happened | Seven classification layers; each layer is a lesson from the previous failure. |
| 3A | The 90% Agents Would Destroy (Part 1) | LLMs are irreplaceable for semantic judgment; the remaining 90% is orchestration. |
| 3B | The 90% Agents Would Destroy (Part 2) | Six simple-looking problems; each one can make an agent fail. |
| 4 | An Honest Comparison | Pipeline vs. agents: 3–10x more expensive, exponential failure rates, 0.6% probability of perfect execution. |
| 5A | What the Research Says: Data | METR’s reliability cliff; Anthropic finds augmentation, not automation. |
| 5B | What the Research Says: Frameworks | Karpathy says composition, not replacement. |
| 6 | The Leverage Gap | Senior + AI = team. The first step of the career ladder has moved upward. |
| 7 | Context Accumulation | Coding ability is solved. Engineering judgment is not. |
| 8A | The Delegation Problem | Fuzzy goals drift silently. Tools have ceilings; models cannot see them. |
| 8B | The Autonomy Spectrum | Even advocates say something more complex than the headline. The future is differentiated autonomy. |
| 9 | The Other Extreme | “LLMs are dead” is as attention-grabbing as “agents will rule the world.” Both are wrong in the same way. |
| 10 | Two Rooms | Demo lovers never finish. Domain experts never start. The pipeline delivered because it listened to both sides. |
| 11 | Evidence (this essay) | The team expected another demo. They got a production system. Success was not in the model, but in engineering. |

## Bonus Essays

| Bonus | Title | Core sentence |
| --- | --- | --- |
| A | Rebuttal | We asked AI to attack its own series. Five rounds of debate, honest responses. |
| B | Understand Systems Before Delegating to Systems | AI lowers the barrier to learning systems, but does not remove the need to understand them. Asking questions is not a substitute for understanding. |
| C | Standing in the Middle Ground | The thought that woke up at midnight. Not fear — something more complicated. |

This is the final main essay in the series. The bonus essays continue: Rebuttal · Understand Systems Before Delegating to Systems · Standing in the Middle Ground. [Start from the beginning.](/blog/why-this-series-exists-en/)
