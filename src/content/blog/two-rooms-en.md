---
title: 'Part 10: Two Rooms — Demo Lovers Never Finish, Domain Experts Never Start'
description: 'Demo lovers see capability; domain experts see risk. What is missing is the responsibility structure that connects the two.'
pubDate: '2026-06-23T12:00:00Z'
heroImage: '../../assets/series-10-two-rooms.jpg'
lang: 'en'
---

> Series: “We built a pipeline with tens of thousands of lines of code. Why could agents not do it?”

[Previous: Part 9 — The Other Extreme.](/blog/other-extreme-en/)

[阅读中文版。](/blog/two-rooms-zh/)

Demo lovers see capability; domain experts see risk. What is missing is the responsibility structure that connects the two.

Previous essay: Part 9 — The Other Extreme. “LLM is dead” is as attention-grabbing as “agents will rule the world.” Both are wrong in the same way. The middle position is where production systems live.

Parts 8 and 9 discussed the two extremes in public discourse: “agents can do anything” and “LLM is dead.” Both are simplified amplifications of more careful views.

But extreme narratives do not live only in headlines. They live in meeting rooms — in the people who actually have to decide what to build and what to trust.

This essay is about two groups of people that exist in almost every institution dealing with AI. You have seen them.

## Room 1: Demo Lovers

Demo lovers genuinely like AI. They track every release, try every new framework, and attend all kinds of technical events. In thirty minutes, they can show you something impressive: a chatbot that answers ESG questions, a prototype that classifies links, an agent that can browse websites and download PDFs.

The demo runs. It always runs. And to be fair: demos are not worthless. A demo is not supposed to prove that everything is finished. Its role is to reveal capability first, to let people see for the first time what might be possible.

Three years pass. No production system is truly used by the investment team.

The instinct of demo lovers is to pursue generality. Standard wrappers. Platform solutions. If a framework already exists, why build your own? Do not reinvent the wheel. Connect the interface. Ship the wrapper.

More troublingly, many demo lovers actually know only the API layer. Understanding interfaces is not the same as understanding models; understanding platforms is not the same as seeing boundaries. Being able to connect a vendor platform, call a model successfully, and wrap a product interface around it does not mean knowing where model capabilities differ, where distortion begins, or where failure boundaries lie. So they easily mistake “I can call a model” for “I understand model capability.” People who cannot see these boundaries can easily make demos; they have a much harder time judging whether the demo can become a product.

The problem is that the wrapper has not solved the domain-specific part. It solves the part that was already easy. The truly hard problem — the one the previous nine essays have been describing — sits in the gap between “the demo runs” and “it runs reliably, at scale, and correctly across 5,000 companies.”

The language of demo lovers sounds like efficiency: “ChatGPT can already do this. Why build so much?”

The question from the other side is also real: what is the value of a generic wrapper? If what you built is merely a skin around an LLM — no domain logic, no edge-case handling, no accumulated engineering judgment — then users really are better off using ChatGPT directly. The wrapper adds nothing. It is a demo pretending to be a product.

The value increment comes from the other 90%: the classification layer, budget logic, retry strategies, domain-scope rules, `robots.txt` compliance, PDF scoring, deferred queues — everything that turns “a demo works for one company” into “a production system runs across thousands of companies.”

That is not reinventing the wheel. That is building the road for the wheel.

But without direction from the business-domain side, demo lovers easily stop here too: continuously showing capability, continuously producing “interesting things,” and finally building yet another tool that mostly excites its builders. They do not know where the business is actually stuck, what should be prioritized, or what it means for a tool to be actively and responsibly used inside a real workflow.

But demo lovers do not build roads. They build wheels — one after another, each shinier than the last, but none mounted on a vehicle that can go somewhere. More ironically, they often turn around and mock people building deeply customized AI applications for “reinventing the wheel.” If you stand only at the layer of general models and platform wrappers, a lot of domain engineering really does look like temporary work that will eventually be swallowed by big-company iteration. But once it lands in production, the value often lies not in the general capability itself, but in who can place that capability inside concrete business boundaries, responsibility structures, and reliability requirements.

The failure mode of demo lovers: always almost finished. Never delivered.

## Room 2: Domain Experts

Domain experts understand the business. Deeply. They have spent years or decades doing ESG analysis, portfolio management, investment research. They have seen technology waves come and go. They have been told before that something would change everything.

They have also seen demos. And those demos did not become products. A chatbot hallucinated a company’s carbon-emissions data. An “AI-powered” report contained mistakes a junior analyst could spot. An agent downloaded the wrong PDF, and nobody noticed until a client meeting.

And many domain experts were not completely unmoved at first. Quite the opposite: they were often genuinely shaken by the capability. If a system can already answer, summarize, classify, and generate, will the judgment accumulated over many years suddenly become less scarce? That unease is not hard to understand. Precisely because it is real, when a demo fails at a critical point, people instinctively feel relief: at least the world has not been rewritten all at once, and the professional value they know is still there. This is not necessarily malicious. It is more like self-protection after a professional identity has been shocked. The problem is only that if the relief comes too quickly, “this demo does not work” easily becomes “this whole path does not work.”

So domain experts say — reasonably:

“AI hallucinates.”
“It is not reliable enough.”
“I only need the workflow to be smooth.”
“Stop piling tools on me.”

Every sentence is right. Hallucination is real. Reliability concerns are reasonable. Workflow disruption has real cost. Being handed a pile of bad tools is worse than having no tool.

Domain experts are not resisting. They are precisely describing what they need: accuracy, reliability, and respect for existing workflows. If three years of demos have not delivered these things, that is not their problem. It is the demo lovers’ problem.

But the way domain experts respond creates its own problem. Completely withdrawing from AI means returning to subjective judgment that cannot scale — judgment that cannot be tested, cannot be systematically improved, and cannot keep up with the speed at which markets produce information.

Also, without the technical side continuously pushing capability boundaries forward, domain experts often have a hard time knowing what is now possible, which formerly unrealistic workflows are becoming realistic, and what genuinely interesting new methods may emerge from the combination. Demos are often shallow, yes, but they at least point at the space of possibility.

“I read the reports myself and form my own view” — that is a philosophy one can maintain for 50 companies. It is not one for thousands. And when competitors use AI — not the demo version, but the engineered version — to process information faster, more consistently, and at larger scale, the purely subjective approach becomes a competitive disadvantage that compounds over time.

Domain experts are not wrong in their diagnosis. They are wrong in their conclusion. The right response to “AI hallucinates” is not “do not use AI.” It is “build a system in which hallucination is caught, constrained, and corrected.”

That is what the pipeline does. It is also what domain experts have been asking for all along. They simply have not been shown it — because demo lovers keep showing demos, not this.

The failure mode of domain experts: reasonable concerns, wrong conclusion. Never started.

## Collision

These two groups collide. This collision is not rare.

One side says: “Stop reinventing the wheel. There are frameworks. There are platforms. Use the standard solution.”

The other side says — or thinks: “Where is your value increment? If this is just a ChatGPT shell, why would users not use ChatGPT directly?”

Both sides see the other side’s weaknesses very clearly.

That is why it is interesting to look at the reactions of truly senior software engineers or domain practitioners who are respected in their fields.

Some embrace this wave enthusiastically. Others stand very clearly on the other side: emphasizing rigor, engineering responsibility, and “we will never put AI-generated output directly into product.”

These defenses are not stupid. Often they are quite reasonable.

But in many institutions, the argument is not only technical judgment.

It is also mixed with something harder to say: a feeling that professional identity is being squeezed, a sense that “this is no longer the work I knew or loved,” even an unease that a core self-definition is being eroded.

That is why AI debates in many institutions increasingly look less like purely technical debates and more like identity and survival debates. To management, vendors, and demo lovers, AI often first means capability expansion, efficiency improvement, and not falling behind. But to many people who must find a position, hold a position, and prove that they still have unique value in this market, it first sounds like something else: bargaining power is being compressed, entry-level roles are being rewritten, and the skill signals accumulated over years are losing value. The same sentence, “embrace AI,” does not sound like the same sentence in different rooms.

This misalignment sometimes becomes public: the stage talks about capability, leverage, and opportunity, while the audience hears role compression, lower entry-level demand, and uncertainty about their place in the system. Nobody is necessarily “hearing wrong.” The same technical narrative is naturally interpreted differently depending on where a person sits in the system.

On stage, the word is capability. In the audience, what is heard is risk.

That does not automatically make them wrong.

But it reminds us that many disagreements that look like pure technical positions are actually mixed with emotion, identity, defense, and a changing sense of the era.

That is why these discussions are so easily compressed into one sentence: either fully embrace or fully reject; either turning AI-assisted coding into a status contest or saying “the more AI, the more trouble”; either “the future has arrived” or “never in product.”

What really needs to be solved is not posture, but how capability, responsibility, and constraint can be recombined.

There is another more hidden and more interesting variant that often appears inside engineering teams themselves.

Some people are willing to build LLM wrappers for business users, to package AI as applications, assistants, analysis tools, and automation interfaces. But once the topic becomes “should our own coding workflow deeply involve LLMs,” their attitude suddenly becomes much more cautious, sometimes turning directly into rejection.

The same people can naturally say:

Users should use AI to improve efficiency.

But when it is their turn, they say:

Real engineering still has to be written by ourselves.
I do not trust AI-written code.
We are the people who really write code; we cannot rely on this.

There is of course a reasonable side to this. AI-generated code does make mistakes, can produce things that appear to run but are hard to maintain, and cannot replace architectural judgment, boundary judgment, and responsibility. This series has said again and again: treating model output directly as product is dangerous.

But the problem is that this rejection is often not only engineering rigor. It is also mixed with a more hidden identity defense.

Because writing code is not only a delivery method. For many engineers, it is part of identity itself. Who can write complex code, debug low-level problems, and move steadily through places others cannot understand has long represented status, seniority, and professional dignity.

So when LLMs are used to build demos for business users, they are “our product capability.” But when LLMs are brought into one’s own coding, they touch something else:

they are not only helping you work; they are also changing how others recognize whether you are good.

This misalignment sometimes appears in very ordinary ways: people are happy to point others toward model credits, tool access, and new frameworks to try, while also turning AI-assisted coding ability into a new technical status game. On the surface, this still looks like embracing AI. At a deeper level, it shows that old professional signals are being reordered before new ones have stabilized.

This explains a seemingly contradictory phenomenon: some people are willing to sell AI as leverage for others, but unwilling to internalize AI as their own leverage. They are willing to let LLMs help users write summaries, look up information, classify, and generate reports; but when LLMs start helping them write scaffolding, change interfaces, add tests, and refactor glue code, the question is no longer only “is it accurate,” but:

how should I redefine the professional identity I built by slowly typing, slowly tuning, and slowly accumulating?

This cannot be dismissed with one sentence like “embrace the future.” But it also cannot become a reason to reject change.

Because mature engineering judgment is not “I will always write every line of code by hand.” It is knowing:

- which code can be generated by the model;
- which boundaries must be defined by oneself;
- which structures must be personally guarded;
- which outputs must be reviewed;
- where maintainability must not be sacrificed for speed;
- where involving the model can expose design problems faster.

In other words, the mature use of LLM-assisted coding has the same structure as the LLM use in this pipeline:

the model compresses implementation cost; the human judges direction, boundaries, and acceptance criteria.

If you treat the model as a replacement for judgment, it is of course dangerous.
But if you treat it as leverage at the implementation layer, it is not an insult to engineering ability. It is an amplifier of engineering ability.

Truly mature engineering ability is not insisting that every line must be typed by hand. It is knowing which layer can be handed over and which cannot; when the model should accelerate, when it should be restrained, when something should be rewritten, and when it should be thrown away.

This is also what Part 9 was really saying when it argued against “LLM is dead”: just because an LLM cannot become your architect does not mean it has no value. Often, its most valuable role is compressing implementation cost that consumed a lot of time but did not truly embody core judgment.

So this hidden engineer version is also part of the two-rooms problem.

The demo lovers’ mistake is selling AI capability to others while underestimating the complexity of domain systems. The domain experts’ mistake is retreating to unscalable experiential judgment because they do not trust demos. Some engineers’ mistake is being willing to treat AI as product capability while refusing to admit that it should also change their own production method.

The three look different on the surface, but their essence is similar:

they have not placed AI in the right position.

Not letting it take over everything. Not keeping it outside the door. Let it enter the layers that can be amplified, while keeping the layers that require human responsibility firmly in human hands.

Demo lovers are right: if the domain does not need it, building everything from scratch is wasteful. Domain experts are right too: a generic wrapper adds little beyond what is already freely available.

The solution is not compromise. It is composition:

- Let LLMs do what they are truly good at: semantic judgment in fuzzy contexts. That is the 10% where LLMs are better suited than handwritten rules. Do not reinvent the wheel there.
- Build domain-specific engineering around them: the 90% that encodes business logic, edge cases, reliability guarantees, and accumulated experience. Do not skip this — all the value is here.
- Treat domain experts’ requirements as design input: when they say “it must be reliable,” that is a system requirement, not resistance. When they say “AI hallucinates,” that is a constraint to engineer around, not an objection to refute.

Demo lovers bring capability boundaries and an intuition for what might be possible. Domain experts bring business context, priorities, acceptance criteria, and judgment about what it means for a tool to be positively used. Neither side can produce something useful alone.

## The Lesson from the Investment Industry Itself

The tension between the two rooms is not new. The investment industry has lived through the same version for decades.

For many years, the narrative was that everything would move toward quantification. Factor investing. Statistical models. Systematic strategies. Human judgment was a liability — emotional, biased, inconsistent. Let the data decide.

Then reality intervened. Factor-investing teams at large institutions are being dismantled. Statistical methods have not consistently outperformed markets. Performance fluctuates year by year, and after enough cycles, larger investors no longer believe pure quant is the answer.

But the other side of the story is equally sobering. Pure conviction-based fundamental managers — some of whom were on magazine covers five years ago — now live under media criticism. High-conviction bets that looked like genius in a bull market later looked like arrogance.

My master’s thesis more than ten years ago analyzed roughly 300,000 analyst and investor recommendations and asked a simple question: do recommendations have value? The answer was: it depends. On the analyst. On the context. On the time horizon. Not a strong endorsement of pure conviction. Not a death sentence either. The result was almost boring.

The pattern is exactly the same as the one this series has been describing:

- Pure quant — the demo lover of investing — has tools but lacks judgment. It processes everything while deeply understanding nothing in particular.
- Pure conviction — the domain expert of investing — has judgment but cannot scale. It understands deeply but covers too little.
- Composition — systematic tools guided by domain expertise, and domain expertise extended by systematic tools — is what actually works.

Sound familiar?

| Approach | Character | Result |
| :-- | :-- | :-- |
| Pure quant | All data, no judgment | Unstable returns |
| Pure conviction | All judgment, no scale | Cannot cover the investment universe |
| Composition | Judgment × scale | An advantage that can compound |

This is the same structure as the pipeline. LLMs without domain engineering — capability without judgment — produce demos. Domain expertise without AI produces depth that cannot scale. Together, they produce something neither side can reach alone.

A fundamental manager feeding private frameworks into an AI-enhanced system is not abandoning conviction. They are scaling conviction. A quant team absorbing domain-expert input is not abandoning rigor. It is grounding rigor.

The managers that thrive over the next decade will not be the ones who chose one side. They will be the ones who combined both.

## What Domain Experts Need to Hear

This section is written specifically for investment managers, ESG analysts, portfolio strategists — domain experts who have repeatedly been told that AI will replace them and have therefore reasonably become cautious.

Your expertise is worth more now, not less.

Here is why: AI is very good at processing language at scale. It can read thousands of pages, classify, and extract patterns.
But it cannot do what you do: apply judgment formed from years of understanding markets, companies, and regulatory environments, and those thousand subtle signals that distinguish genuine disclosure from carefully packaged emptiness.

That judgment is your competitive advantage. In an AI-enabled world, that advantage does not shrink — it is amplified.

Think about it: if every fund manager can use the same LLM, the same chatbot, the same generic AI tools, what creates separation? Not AI. AI is the same for everyone. The difference comes from what is fed into AI: private frameworks, distinctive evaluation standards, domain-specific knowledge that public models do not have.

If you believe you have a proprietary recipe that makes your investment judgment better than others’ — and you do, otherwise you would not be in this position — then AI is the mechanism that lets you apply that recipe at scale.

Without AI: you apply your judgment deeply to 50 companies. With AI — the engineered kind, not the demo kind — you apply your judgment to 5,000 companies, because the system encodes your standards and the LLM helps classify at the scale your standards require.

This is not replacement. This is leverage. Your secret recipe operating at a scale you could never reach alone.

But this works only if you participate. Feed your framework into the system. Make explicit what “good” means so engineering can encode it. Treat AI as a tool that extends your reach, not as a threat that weakens your role.

Domain experts who participate will become the most valuable people in the room — because they have what demo lovers and AI do not: the domain knowledge that decides whether the system is solving the right problem.

Domain experts who withdraw will become increasingly isolated — not because their insistence on quality is wrong, but because the quality of manual review cannot keep up with markets accelerating every year.

Your caution is input for engineering design, not a character flaw. But caution that does not participate is just abstention.

## What Demo Lovers Need to Hear

This section is for builders, framework enthusiasts, and the “just connect the interface” camp — people who genuinely love what AI can do and want to push it into the market.

Your judgment about capability is right. But capability is not product.

A demo runs because the demo is designed to run. It shows the best case. It runs on filtered inputs. It has not met the edge cases that appear only when running at scale, over time, across thousands of entities.

When domain experts say “not reliable enough,” listen. They are not being conservative. They are giving you the requirement that turns a demo into a product. Reliability is a feature. Accuracy is a feature. “Does not hallucinate a wrong carbon-emissions number in a client report” is a feature.

When they ask “what does this add beyond ChatGPT,” take it seriously. If you cannot say what your system does that ChatGPT cannot — if the answer is only “we wrapped it in a nicer interface” — then you have not built anything yet.

The value increment is in domain logic. In the classification layer. In edge-case handling. In reliability engineering. In the accumulated judgment of people who have spent years in this domain being encoded into deterministic rules around which the LLM can run.

Build that, and you have built something generic tools cannot match. Skip that, and what you built is a demo.

Stop merely showing demos. Start encoding domain knowledge. The product is there.

## The Bridge

The pipeline is proof that both groups can be right — if they stop talking past each other.

Demo lovers are right: Claude’s accuracy in classifying ESG links cannot be matched by any rule system. The capability is real. For a system that needs to process thousands of diverse company websites, using it is not optional.

Domain experts are right: LLMs alone are not reliable enough to go directly into production. They need budget controls, scope rules, validation layers, fallback strategies, deterministic guarantees — the things that ensure output reaches the standard the business requires.

The pipeline uses both. 10% LLM. 90% engineering. 100% grounded in years of accumulated domain expertise.

Demo lovers contributed capability and the detection of new possibility. Domain experts contributed business context and judgment about where to focus power and how to avoid building another self-entertaining tool. Engineering combined them into something usable.

None of the three could build it alone.

## An Honest Observation

At this point, technical readers care about how the system is built. Domain readers care about: is it useful? Is it reliable? Will it disrupt my workflow?

This is not a difference in understanding ability. It is a difference in position. Technical people see structure; domain experts see risk, trust, and workflow.

So if this pipeline is explained to domain experts, the version should be shorter:

It collects ESG information from thousands of company websites.
It uses AI where language understanding is needed.
It uses code where reliability is needed.
It is designed by people who understand the domain.
It works.

What domain experts truly need to help define is not how the orchestration layer is written, but what “usable” means, what “trustworthy” means, and what kind of result deserves to enter the workflow.

That is where the two rooms must connect.

## By Now, the Series’ Position Is Clear

At this point, one argument is clear. It is really addressed to both rooms:

To demo lovers:
Your tools are real. Your technical capability is real. But a demo is not a product. The gap between the two must be filled with domain knowledge you do not have and engineering you have not done. Stop merely showing. It is time to build. And build with domain experts, not for them.

To domain experts:
Your concerns are reasonable. Your expertise has not automatically become invalid because AI exists. Expertise that does not interact with new tools is expertise that cannot scale. AI does not replace your judgment — it extends the reach of your judgment. Feed your framework in. Participate in shaping the system. Your caution makes the product better, but only if you are in the room.

To both sides:
The future is not AI doing everything. Nor is it humans doing everything. It is composition — intelligence, precision, and experience each doing their job, assembled by people who understand all three.

But at this point, all of this can still be treated as a position. So the next essay will no longer discuss structure, judgment, or why these two groups need each other.

The next essay, the final essay in the main series, will discuss only one harder thing: evidence. Not whether this composition sounds right, but whether it actually delivered something usable in reality.

Next: [Part 11 — Evidence.](/blog/evidence-en/) [Start from the beginning.](/blog/why-this-series-exists-en/)

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
| 09 — The Other Extreme | Not being the endpoint does not mean no value |
| **10 — Two Rooms** | **You are here** |
| [11 — Evidence](/blog/evidence-en/) | The pipeline as evidence |
| Bonus — The Counterargument | AI argues against the entire series |
| Bonus — Standing in the Middle | The thought that arrives in the middle of the night |
