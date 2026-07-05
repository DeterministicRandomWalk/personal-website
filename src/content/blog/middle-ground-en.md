---
title: 'Bonus Essay: Standing in the Middle Ground'
description: 'The thought that woke me up in the middle of the night was not simply fear. More precisely, it was the unease of having been amplified.'
pubDate: '2026-06-27T12:00:00Z'
heroImage: '../../assets/series-bonus-c-middle-ground.jpg'
lang: 'en'
---

> Series: “We built a pipeline with tens of thousands of lines of code. Why could agents not do it?”

[Previous: Bonus Essay — Understand Systems Before Delegating to Systems.](/blog/understand-systems-en/)

[阅读中文版。](/blog/middle-ground-zh/)

The thought that woke me up in the middle of the night was not simply fear. More precisely, it was the unease of having been amplified.

This is the final bonus essay of the whole series.

The main thread has basically reached its end: Part 6 discussed the leverage gap, Part 7 discussed context accumulation, Part 8 discussed delegation and autonomy boundaries, Part 9 pushed back against the other extreme of “LLMs are dead,” Part 10 discussed the two rooms inside organizations, and Part 11 described what happened after we actually built the system.

This essay no longer tries to prove why the system works.

It is about the more complicated feeling left behind after the system does work.

## Three in the Morning

One night at three in the morning, I suddenly woke up with a very clear thought in my head:

If these tools keep getting stronger, what happens next?

This question is not new. People discuss every day whether AI will replace people, whether AI will rewrite career paths, and whether AI will change organizational structures.

But the unease in that moment did not come from abstract discussion.

It came from a more specific fact: we had indeed turned part of the work that previously required a large amount of human time into a system.

It was not a demo. It could run. It could be used. It could be relied on by a team. It turned part of material collection, filtering, judgment, recording, and feedback loops into a repeatable process.

Of course this is a good thing.

But precisely because it is a good thing, the question becomes less easy to answer.

## Two Feelings That Are True at the Same Time

The feeling this brings is not singular.

On one hand, it is exciting. Because you really see that AI is not only for writing paragraphs, summarizing webpages, or generating toy apps. As long as the model is placed in the right position and supported by engineering, data, constraints, and human judgment, it can enter real workflows, expand human leverage, reduce repetitive labor, and make complex processes more controllable.

On the other hand, it is also unsettling. Because the same thing also shows that many links once assumed to require large amounts of human labor, experience, and time are being split apart, compressed, and systematized again.

These two feelings do not contradict each other.

It is both opportunity and pressure.

It both makes you feel “we can finally do what we could not do before,” and makes you realize “part of what used to define capability may be getting eaten by the system.”

This is not simple optimism or pessimism.

More precisely, it is the feeling of standing in the middle ground.

## Why Write This Down

When I started writing this series, I was not trying to write an essay about “what should people do in the age of AI.”

The original question was very concrete: we built a production pipeline with tens of thousands of lines of code. Why could an agent not directly replace it?

That question looked like an engineering question. But as I kept writing, it slowly became a larger question.

Why can strong models not naturally possess system context?

Why does being able to generate code not equal being able to maintain a system responsibly?

Why does being able to complete local actions not equal being able to take over a complete workflow?

Why do demo enthusiasts and domain experts inside organizations keep misunderstanding each other?

Why, after a system truly succeeds, does it make people even more uncomfortable?

That last question is the entry point of this essay.

Because once a system really works, it does not only prove a technical path. It also changes how people understand their own work.

## When “Having Technical Ability” Is No Longer So Easy to Judge

In the past, technical capability in many kinds of work was relatively easy to identify.

Being able to write code, set up frameworks, tune databases, process data, deploy services, write scripts, and automate workflows — these capabilities were concrete and relatively visible.

After AI appeared, these capabilities did not disappear. But their visibility changed.

Someone who cannot handwrite a complete system from zero may still produce a decent-looking tool with AI assistance.

Someone who does not understand the underlying mechanism may still have the model guide them step by step through a workflow.

Someone without long-term engineering experience may still build a polished demo in a short time.

This is not fake.

These changes are real, and they are very important.

But the problem is that outside observers are finding it harder and harder to judge what exactly it means when something has been “built.”

Was it built because the person truly understood the system, or because the model temporarily stitched together a runnable result?

Was the problem solved, or did the demo path simply avoid hitting the boundary?

Is the capability sustainable, or was the context temporarily lucky enough?

The fact that something “can be built” is losing part of its old distinguishing power.

## Being Able to Build It No Longer Says Enough

This is also why the series repeatedly emphasizes the difference between a demo and a production system.

A demo can prove possibility. A production system has to carry responsibility.

Before AI, being able to build something already said a lot. Because implementation cost was high enough, being able to build it usually meant you understood a meaningful part of the path.

But after models sharply reduce implementation cost, “being able to build it” is no longer enough.

The real questions become:

- Do you know why the system can run?
- Do you know when it will be wrong?
- Do you know how to investigate when it is wrong?
- Do you know which parts must be reviewed by humans?
- Do you know which outputs can be trusted and which merely look reasonable?
- Do you know how the system should change when requirements change?

These questions may not appear in a demo.

But they will appear in real use.

So technical ability has not become unimportant.

It has simply moved from “can you implement it?” toward “can you understand, constrain, maintain, judge, and take responsibility for it?”

## Fast Wins Attention; Deep Has to Prove Itself

This creates a very real pressure:

Fast people win more attention.

Deep people have to work harder to prove why they matter.

Many products and stories in the AI era naturally lean toward “fast.” Build an app in a few days. Launch a tool in a week. One person completes what used to require a team. These stories spread well because they are clear, direct, and energizing.

The value of “deep” is usually harder to display.

You prevent a silent failure; nobody sees it.

You design the system to be traceable; nobody gets excited.

You do not let the model exceed its authority; nobody takes a screenshot.

You build exception handling, budget control, feedback loops, and audit paths properly, and from the outside it only looks like: it works normally.

That is the awkward part.

The more mature a system is, the more it hides its own complexity.

The more reliable a system is, the easier it is for people to forget that reliability was designed.

This is not a problem unique to AI. All infrastructure has a similar fate. AI merely amplifies it: models make things that “look usable” easier to produce, while making the parts that are “truly reliable” harder for outsiders to see.

## How Complexity Gets Compressed Inside Organizations

Organizations naturally like to compress complexity.

This is not a bad thing. Organizations must compress complexity, otherwise they cannot make decisions. Nobody can re-understand every technical detail, every failure mode, and every contextual history in every discussion.

So organizations compress complex systems into simple labels:

This is an AI project.

This is an automation tool.

This is a data pipeline.

This is a search system.

This is an efficiency improvement.

None of these labels is entirely wrong.

But none of them is enough.

The truly difficult parts are often hidden behind the label: how inputs are defined, how evidence is traced, how boundaries are drawn, how failures are handled, how user feedback enters the next round, and where responsibility stops.

This is also why, the more a system enters a real organization, the more someone is needed in the middle to translate.

Not to translate technology into slogans.

But to translate model capability, engineering constraints, business judgment, and organizational responsibility onto the same plane.

This work is hard to see, but it is extremely important.

## The Middle Ground: Not Just Two Rooms, but Many Rooms

Part 10 wrote about “two rooms”: demo enthusiasts see capability, while domain experts see risk.

But in real organizations, there are often more than two rooms.

There is the platform room, which cares about unified entry points, permissions, governance, and reuse.

There is the engineering room, which cares about maintainability, observability, cost, and failure recovery.

There is the business room, which cares whether the system really solves the problem, whether it saves time, and whether changing the workflow is worth it.

There is the management room, which cares about priority, resources, risk, and narrative.

There is the compliance or control room, which cares about responsibility boundaries, audit paths, and explainability.

Each room sees part of the truth.

Each room is also prone to treating the part it sees as the whole truth.

Standing in the middle ground does not mean standing in a compromise position and distributing blame evenly.

It is more like walking back and forth between different rooms, trying to help them see what the others cannot see.

Tell the demo enthusiasts: the capability is real, but capability is not a system.

Tell the domain experts: the risk is real, but risk is not a reason to refuse to begin.

Tell the platform view: unification is important, but it cannot flatten the complexity of concrete workflows.

Tell the engineering view: reliability is important, but not every new problem can be compressed into old engineering patterns.

Tell the business view: efficiency is important, but you need to know where the efficiency comes from and where the risk has been placed.

That is the work of the middle ground.

It is not always comfortable. Because it is hard to provide simple slogans.

But precisely for that reason, it may be where systems like this can actually land.

## The Discomfort After Evidence

Part 11 discussed evidence.

The investment team thought it was another demo. They got a production system.

That is a happy outcome.

But it also brings another layer of questions.

After a system proves that it works, people naturally begin to ask:

What next?

What else can be automated?

How much more time can be compressed?

How many more workflows can be rewritten?

These are not bad questions. In fact, they are very reasonable. Once a system proves its value, of course an organization will want it to expand.

What truly makes people uncomfortable is this: success itself pushes the boundary to keep moving.

This is the first layer of paradox after a system is completed:

The more you turn a complex thing into a system, the more easily it is seen as “already solved.”

The more you sediment judgment into a process, the more easily judgment itself changes from capability into infrastructure.

And once it becomes infrastructure, it will keep moving toward standardization, process, and even commoditization.

Beyond that, there is a second layer of discomfort, which comes from changes in work boundaries.

A useful system cannot be simply described as “replacing people.” In real workflows, value is not only completing actions; it also includes judgment, review, responsibility, and context. A more accurate description is: it gives part of the repetitive filtering and material organization to the system, so people can leave more time for the places that truly require judgment.

Of course this is a good thing.

But when the system really takes over part of the repetitive work, it also makes originally blurry work boundaries clearer: which things are merely repetitive processing, and which things contain real judgment; which places can be handed to the system, and which places must remain human responsibility.

This is not simple “replacement.”

It is more like the redistribution of work boundaries.

So evidence is not the endpoint.

Evidence only pushes the question from “is this path right?” into a deeper layer:

When this path begins to hold, how will the boundaries between people, systems, organizations, and users change?

At this point, the question is no longer only whether AI will replace people.

It is: when boundaries keep moving, judgment standards keep changing, and workflows themselves begin to be rewritten, where can people still place themselves?

## What Can Be Done: Keep Moving Vertically Deeper

At least for me, the way to relieve this anxiety is not to choose a side, and not to pretend I cannot see it.

The more feasible approach is to keep moving with the technical boundary.

But “keep moving” does not simply mean chasing newer tools or burning more tokens. First, it means that the understanding of “technology” itself has to change too.

In the past, I also found it easy to understand technology as a more professional, more standardized, more engineering-oriented capability: whether the code is good enough, whether tests are complete, whether the framework is mature, whether the structure is elegant, whether the process is standard. These things are certainly important, especially when a system truly needs to run for a long time.

But in real work, it is becoming increasingly obvious that these are not everything, and are not always the hardest part.

The harder part is bringing a not-yet-fully-formed problem into reality: seeing a direction that has not been fully explored, connecting business judgment, data constraints, model capability, engineering implementation, user feedback, and responsibility boundaries, and turning it into a system that can run, can be reviewed, and can be relied on by a real team.

In this sense, continuing to move is not only continuing to learn new tools. It is continuing to walk toward places where the problem has not yet been clearly defined, the path has not yet been fully explored, and the answer cannot be generated in one shot.

This sentence sounds abstract, but in actual work it is often very concrete.

This pipeline grew from a simple crawler into tens of thousands of lines of code, not because someone planned a complete building from the beginning, but because every time we encountered something the model could not do, could not do stably, or could not do responsibly, the system was forced to grow another ring outward.

Browser cascading, PDF scoring, domain-level stopping rules, budget control, exception recovery, evidence traceability, user feedback records — none of these things is suitable for making the first demo look beautiful. But they determine whether a tool can move from “looks useful” to “is truly relied on.” This is also what the autonomy spectrum really points to once it lands in engineering: what can be delegated, what must retain supervision, and what must remain under human control.

To make this “continuing to move” more concrete, I personally now lean more toward betting on the vertical/depth side rather than the platform/horizontal side.

This is not a simple commercial stance, and certainly not a claim about who will win the entire AI era. Platforms are of course important. Unified entry points, permissions, governance, toolchains, and reuse are all real problems. The issue is that the platform narrative sometimes simplifies a harder problem too early: as if, once the model is strong enough, the interface unified enough, and the entry point standardized enough, most of the complexity in real workflows will naturally disappear.

But the real world often does not work that way. Especially in places full of private information, internal rules, budget constraints, non-public assets, proprietary processes, delayed feedback, and responsibility attribution, the model’s “smartness” must be continuously supported by systems, context, and experts.

So if this has to be called a bet, it is not a bet that human experts will never be replaced. At least for me, the place still more worth investing in looks like the places that embed models into concrete workflows, concrete evidence chains, concrete judgment structures, and concrete responsibility boundaries.

It is more likely to be in places that cannot easily be passed over by a single platform narrative: places where data is not public, where rules are not written in documents, where results need long-term validation, where responsibility cannot be easily outsourced, and where systems must converge together with people.

This does not provide a sense of safety. But at least it provides a more concrete direction.

This is not a one-time migration. It is a continuous movement. And it will not end, because the boundary will not stop moving. What people in the middle ground feel is not only opportunity or risk, but a continuous responsibility with no endpoint.

Every new model release reminds people again: the question is not whether the boundary will move, but whether, after it moves, you can understand again where you should stand.

## The Larger Question

Beyond all this, there is an even more fundamental question: when the leverage ratio keeps changing — when fewer and fewer people can complete more and more work — what are the consequences at the level of society?

Employment structure, income distribution, the basis of consumption, people’s sense of value: these questions are larger than any technical blog can cover, and more complicated than the technical problem itself.

This series cannot answer these questions.

What it can do is describe what is happening as honestly as possible: without exaggerating, without avoiding, without pretending to have an answer.

If this discomfort had to be compressed into one sentence, it would probably be:

We have not yet figured out what the problem is, but we are already being asked to take responsibility for the answer.

This discomfort is not the result of system failure, and it will not automatically disappear because the system succeeds.

It is more like part of this stage itself.

The boundary is still moving. Perhaps all people can do is keep re-understanding where they stand.

Related main thread: → [Part 6: The Leverage Gap](/blog/leverage-gap-en/) · [Part 7: Context Accumulation](/blog/context-accumulation-en/) · [Part 8A: The Delegation Problem](/blog/delegation-problem-en/) · [Part 8B: The Autonomy Spectrum](/blog/autonomy-spectrum-en/) · [Part 9: The Other Extreme](/blog/other-extreme-en/) · [Part 10: Two Rooms](/blog/two-rooms-en/) · [Part 11: Evidence](/blog/evidence-en/)

Other bonus essays: → [Bonus Essay: Rebuttal — We Asked AI to Dismantle This Entire Series](/blog/rebuttal-en/) · [Bonus Essay: Understand Systems Before Delegating to Systems](/blog/understand-systems-en/)

## Appendix: Series Index

| Part | Core argument |
| --- | --- |
| [00 — Introduction](/blog/why-this-series-exists-en/) | Why this series exists |
| [01 — The Impossible Task](/blog/impossible-task-en/) | The starting point |
| [02 — How 7,400+ Lines of Code Happened](/blog/seven-layers-en/) | How the pipeline snowballed |
| [03A — The 90% Agents Would Destroy, Part 1](/blog/llm-shines-agents-destroy-en/) | LLMs are irreplaceable for semantic judgment; the remaining 90% is orchestration |
| [03B — The 90% Agents Would Destroy, Part 2](/blog/agents-destroy-orchestration-en/) | Six problems that look simple, each enough to break an agent |
| [04 — An Honest Comparison](/blog/honest-comparison-en/) | Pipeline vs. agents, by the numbers |
| [05A — What Research Says: Data](/blog/research-data-en/) | METR’s reliability cliff; Anthropic finds augmentation, not automation |
| [05B — What Research Says: Frameworks](/blog/research-frameworks-en/) | Karpathy says combination, not replacement |
| [06 — The Leverage Gap](/blog/leverage-gap-en/) | Senior + AI = team. The first rung of the career ladder has moved up |
| [07 — Context Accumulation](/blog/context-accumulation-en/) | Coding ability is solved. Engineering judgment is not |
| [08A — The Delegation Problem](/blog/delegation-problem-en/) | Ambiguous goals silently drift. Tools have ceilings; models cannot see them |
| [08B — The Autonomy Spectrum](/blog/autonomy-spectrum-en/) | Even advocates say something more complex than the headline. The future is differentiated autonomy |
| [09 — The Other Extreme](/blog/other-extreme-en/) | “LLMs are dead” and “agents rule the world” are equally catchy. Both are wrong in the same way |
| [10 — Two Rooms](/blog/two-rooms-en/) | Demo enthusiasts never finish. Domain experts never start. The pipeline shipped because it listened to both rooms |
| [11 — Evidence](/blog/evidence-en/) | The team expected another demo. They got a production system. Success was not in the model; it was in the engineering |
| [Bonus — Rebuttal](/blog/rebuttal-en/) | We asked AI to dismantle this series. Eight sharp attacks. Honest responses |
| [Bonus — Understand Systems Before Delegating to Systems](/blog/understand-systems-en/) | Asking questions is not a substitute for understanding |
| Bonus — Standing in the Middle Ground | ← You are here |
