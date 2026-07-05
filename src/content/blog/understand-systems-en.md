---
title: 'Bonus Essay: Understand Systems Before Delegating to Systems'
description: 'AI lowers the barrier to learning systems, but it does not remove the need to understand them.'
pubDate: '2026-06-26T12:00:00Z'
heroImage: '../../assets/series-bonus-b-understand-systems.jpg'
lang: 'en'
---

> Series: “We built a pipeline with tens of thousands of lines of code. Why could agents not do it?”

[Previous: Bonus Essay — Rebuttal.](/blog/rebuttal-en/)

[阅读中文版。](/blog/understand-systems-zh/)

## Why “Just Learn to Ask Questions” Is Dangerous

AI lowers the barrier to learning systems, but it does not remove the need to understand systems. Quite the opposite: the more actions can be delegated, the more someone needs to know where things can lose control, where they can silently fail, and where they must be stopped.

This is a bonus essay. Part 6 discussed how AI amplifies the leverage gap, Part 7 discussed why context cannot be easily delegated, Part 8 discussed the delegation problem inside systems, and Part 10 discussed the two rooms inside organizations. This essay brings the problem back to the individual level: being able to hand more actions to AI does not mean you can give up understanding the system.

Let us be clear first: this essay is not trying to persuade people to use AI less. Quite the opposite. It is written for people who want to use AI more seriously.

## Another Sentence That Is Easy to Misread

Earlier in this series, we kept taking apart two extremes: one says “agents will soon take over everything,” and the other says “LLMs are dead and not worth building with seriously.”

But beyond these two extremes, there is another sentence that is just as popular and just as easy to misread:

In the AI era, you no longer need to learn technology.

Just learn to ask questions.

This sounds pleasant because it sits right next to a real change: AI really is lowering the barrier to entering many fields. In the past, you might not even have been able to set up the environment. Today, models can already help you write scaffolding, explain errors, fill in dependencies, and build a minimal working version. Many people who could not even enter the door before can now at least begin.

But lowering the barrier does not cancel understanding.

The real question is not “will AI do things for you,” but:

When more and more actions can be delegated, do you still have the ability to judge when delegation is starting to lose control?

## Why This Narrative Spreads So Easily

It is not surprising that this sentence spreads quickly.

Over the past year, there have been too many stories like this: a celebrity with no technical background builds an app; a founder uses AI to build a beautiful dashboard; a business user creates in a few days a small tool that previously required a developer. Each story, viewed alone, is real, and it does prove something important: AI is lowering many implementation-level barriers.

But when these stories spread, they are often quietly converted into another conclusion:

See, even without understanding technology, you can build complex things.

So from now on, all you need is to know how to ask.

That jump is too fast.

Between “more people can start building things” and “understanding no longer matters,” the most important layer is missing: building it does not mean building it correctly; running does not mean usable; demoing does not mean responsible.

More accurately, what these stories really prove is: AI gives more people the chance to enter systems, not that people no longer need to understand systems.

Lowering the barrier is an opportunity. Canceling understanding is a misreading.

## Rapid Prototyping Is a Strategy, but Not the Answer to Every Problem

Using AI to quickly build a small tool, finding users who are willing to use it or even pay for it — of course that is good. For some people, this is not only a technical choice but a working style: fast trial and error, fast monetization, horizontal expansion, smelling opportunities.

This strategy has its reasonableness. For low-risk, small-scale, easily replaceable products, speed really can matter more than robustness. Not everything needs production-grade engineering at the start.

The “one-person company” narrative is similar. It captures a real change: AI allows one person to complete many actions that previously required a small team. But it often ignores the other side: if this becomes so cheap, it will not be cheap only for you. It will be cheap for everyone.

When everyone can quickly build an app, a dashboard, a chat tool, or a report generator, “being able to build it” is no longer a moat. The real question becomes: why should users use yours? Why are they willing to pay? Why will they keep coming back after the novelty fades?

So lowering construction cost does not cancel competition. Quite the opposite: it pushes competition from “who can build it” toward “who can truly solve the problem, build trust, embed into workflows, and keep creating value.”

The problem is misreading the success of this strategy into a larger conclusion:

Since rapid prototypes can run, sell, and make money, understanding systems, engineering boundaries, and long-term responsibility no longer matter.

That jump is too fast.

Rapid prototypes are good at discovering opportunities; production systems carry sustained responsibility.

Revenue proves that someone needs it. It does not prove it is reliable. Running proves possibility. It does not prove it can be responsibly depended on when nobody is watching.

If a tool is only a low-risk experiment and failure does not matter much, then being faster and rougher can be perfectly acceptable. But once it enters someone else’s workflow, financial judgment, compliance process, investment decision, or client delivery, “I do not care about robustness” is no longer only a product strategy. It is handing risk to the user.

So this is not an argument against rapid prototyping.

Rapid prototyping is a valuable way to discover opportunities. What needs caution is mistaking success at the prototype stage for reliability in a production system.

## Why “Just Learn to Ask Questions” Gets It Exactly Backward

Every failure mode mentioned in this series — fuzzy goals, tool ceilings, silent drift — has one shared premise:

To discover the problem, you must first understand the system.

The people most likely to get into trouble with delegation are not the ones who delegate too much. They are the ones who cannot see how failure happens. If you cannot see it, you do not know when to doubt, when to stop, and when to rewrite.

So the correct conclusion is exactly the opposite of the popular slogan:

Not “you do not need to learn,” but “you should learn more than before, and it is easier than before.”

AI lowers your cost of entering the system, but it does not bear your responsibility for judging the system.

## Why Delegation Raises the Requirement for Understanding

Many people think that the more models can write code, change code, look things up, explain libraries, and fix bugs, the less important understanding the system becomes.

Reality is exactly the opposite. The more the model can complete local actions for you, the more you will hand over to it; and with every extra layer you hand over, the more you need to know:

- how far this layer can be delegated;
- where it will reliably distort;
- when it is helping you compress implementation cost;
- when it has begun to replace the goal without you noticing;
- when it looks like progress but is actually generating a pile of outputs nobody is truly responsible for.

In other words, the stronger the delegation, the more important supervision becomes; the more important supervision becomes, the more important system understanding becomes.

Even if we accept a simpler premise, the conclusion is the same: if humans remain responsible for system outcomes, the key ability is not outsourcing more actions, but understanding the system, correcting it, and pulling it back when it drifts away from the goal.

This is also why a more automated agentic mode is not naturally better. Popular narratives easily equate “fewer clicks, fewer confirmations, less human intervention” with “more advanced.” For some tasks, that is true. But for many new problems, messy problems, and problems whose boundaries have not yet been mapped, it is exactly wrong. These tasks often do not start with a high-resolution enough goal that you can safely hand over in one shot. The goal itself grows slowly through trying, looking, and correcting.

So in many real settings, the stronger approach is not to delegate fully as early as possible, but to think with the agent: you move forward while watching what it misunderstood, what it missed, what it over-optimized, and slowly turn the direction back. This process is not only controlling it; it is also training yourself. Through close supervision, you gradually learn where you can let go, where you must inspect closely, which outputs can be accepted directly, and which signs mean you should immediately stop and recheck. For a clearly defined problem, this may look like “one more layer of human work.” But for a problem whose definition has not yet grown, this is exactly the faster way to approach the real target.

If delegation expands by one foot, supervision and steering ability must expand by ten.

This is not because AI is not smart enough. It is because many decisions require not “generation ability,” but judgment, responsibility, trade-off, and position.

## Concretely, What Breaks When You Do Not Understand?

The previous sections were about principles. The truly dangerous parts often hide in concrete details.

“Understanding systems” is not an abstract slogan. It means you at least need to know where models may fabricate, where code may slow down, where dependencies may break, where networks may reject, where goals may drift, and which choices should never be handed to the model.

Below are nine examples. Readers can read only the titles if they want. Together they illustrate one thing: AI can generate results, but system boundaries do not automatically disappear.

### Example 1: Not Understanding What an LLM Is

If you do not know that current LLMs are fundamentally next-token prediction with probability distributions — not AGI, not universal experts, not black magic that “just works, do not ask why” — you can easily mistake fluency for reliability. Silent drift often begins here: the delegator does not know when to question, so the model fills gaps with plausible content.

Many people also encounter models only at the hosted API layer. Knowing how to call an API and compare subscription plans is not the same as understanding model differences. Only after hitting hard boundaries like VRAM, quantization, throughput, and latency do you understand that 8B, 30B, 70B, and 600B are often not smooth score increments, but changes in task type. Interfaces hide the differences, and this makes it easy to mistake “I can call a model” for “I understand the model.”

### Example 2: Not Understanding Language, Runtime, and Performance Boundaries

AI can easily help you write a script that reads files, processes data, calls an API, and exports results. Locally, on small samples, for one-off tasks, it may be completely fine. But real systems must run repeatedly, process large amounts of data, deploy into different environments, and recover, trace, and maintain themselves when they fail.

At that point, the problem is not only whether the syntax is correct. It is whether memory grows, I/O blocks, dependencies can be deployed, and processing should be batched or streamed. Models usually first give you a “runs” solution. But “runs” is a success at the syntax layer; “usable” is a success at the system layer. Without understanding runtime and performance boundaries, it is easy to mistake a local script for a deliverable system component.

### Example 3: Not Understanding Dependencies and Environments

It is easy to think everything works out of the box until PDF parsing fails, browser driver versions mismatch, or the same dependency behaves differently on another machine. Tool ceilings are real. People who do not understand dependencies and environments cannot even see where the ceiling is. To them, failure looks random. To someone who understands systems, it is a boundary that can be predicted, isolated, and absorbed.

Take PDF parsing. Normal PDFs often work on small samples, but real files may be scans, two-column layouts, tables, mixed with headers and footers, or have text order scrambled. The same code moved to a server may change behavior because of fonts, low-level libraries, browser drivers, or parser versions.

Someone who does not understand environments says:

It worked yesterday. Why is it broken again today?

Someone who understands systems asks:

What kind of PDF is the input? What parser version is this? Did the runtime environment change? Is this a single-file problem or a dependency boundary problem?

Even if AI tells you “use Docker to solve environment problems,” the story may not end. Company networks, image registries, permissions, security policies, internal proxies, and certificates can all make the standard solution impossible to deploy. The model will keep guessing images, ports, dependencies, and commands, while the real problem may sit inside organizational infrastructure.

Parsing is not an abstract action, and deployment is not an abstract action. Both depend on input shape, tool capability, runtime environment, and organizational boundaries.

This is why dependencies and environments are so easily underestimated. They are not trouble outside the project. They are part of the system.

### Example 4: Not Understanding Efficiency and Complexity

Without understanding complexity and data movement cost, you may accept code that is logically correct but unusable once scale increases. The model responds to what you ask, not to what you should have asked but did not. Without complexity awareness, the system breaks in a way that “looks correct but is actually expensive.”

Once, AI wrote a very natural implementation for text-similarity deduplication: every time it selected a new sentence vector, it rebuilt a matrix from all selected vectors and compared the current vector against it. On small samples, the result was correct and the code was clear.

The problem was that every round recopied data that had already been organized. With dozens of vectors, this was almost invisible; with tens of thousands, repeated memory allocation and data movement were enough to drag the system down. A better approach was to preallocate fixed space, write only one new vector each time, and compare only against the used portion.

Mathematically, the two implementations are almost the same. Systemically, they are completely different. The first is like emptying and rearranging the whole bookshelf every time a new book arrives; the second just puts the new book into the next empty slot. The problem is not that “AI cannot write code.” Quite the opposite: it wrote a serious, intuitive, logically correct implementation. The real question is whether the delegator can see the difference between “logically correct” and “system usable.”

So understanding efficiency and complexity is not an old-era programmer obsession. It is a basic ability for judging whether model output can enter production in the AI era.

### Example 5: Not Understanding Non-Determinism

AI services may produce different outputs for the same input because temperature, sampling, context truncation, and tool-call paths can all change. Someone who does not understand systems says “AI broke again.” Someone who understands systems treats it as non-determinism that must be absorbed by engineering.

For example, when asking a model to judge whether a webpage is ESG-related, most results may be stable, but a few boundary pages will wobble. The issue is not that the model sometimes wobbles; it is whether the system has mechanisms to absorb it: Are boundary samples confirmed twice? Are high-risk classifications handled by a stronger model? Does low confidence enter a review queue? Do key documents require multiple signals? Can downstream users trace why this judgment changed?

Without these designs, non-determinism leaks from the model layer all the way into the business layer. What the user sees is not “a boundary sample needs review,” but “the system changed mysteriously again today.”

So understanding non-determinism is not about tolerating errors. It is about knowing which errors must be absorbed by the system instead of thrown directly at users.

### Example 6: Not Understanding Algorithms and Trade-Offs

AI will choose a solution for you because you did not give it enough background to know how to trade off. It usually will not keep asking:

Do you care more about speed or accuracy?

Memory or latency?

Readability or extreme performance?

Many engineering problems have no single correct answer, only choices with costs. If you do not understand the pros and cons of alternative paths, you will mistake the model’s default choice for the “best answer.”

For example, “coverage” versus “cheapness” in web collection. The model may suggest crawling pages broadly, following links, downloading PDFs, and extracting all relevant information. But coverage is not free: the deeper you crawl, the higher the cost; the more links you follow, the more noise you get; the more PDFs you download, the faster the budget is consumed; the more model calls you make, the slower the throughput.

The question is not “should we be comprehensive,” but how to trade off budget, time, accuracy, recall, website pressure, and downstream usability. Otherwise, the model will rewrite what the team really needs — “comprehensive enough, reliable enough, cost-controlled” — into “crawl as much as possible.”

Engineering judgment is often not choosing the strongest solution, but choosing the solution most suitable under the current constraints.

### Example 7: Not Understanding Networks and Infrastructure

Crawling sounds simple, but its difficulty can rise from a script to complex infrastructure. The most typical misconception is “higher concurrency means faster.” AI may suggest visiting more pages, downloading more files, and calling more APIs at the same time, but the real network is not a stable pipe.

Websites rate-limit. Servers reject dense requests. Pages may require cookies, sessions, and redirects. Failures may require waiting, retrying, and backing off. Without understanding these boundaries, you will misread rate limits and network jitter as code problems and ask AI to “fix the bug” again and again, when what really needs to change may be request frequency, timeout, headers, queueing, and failure recovery.

More importantly, some boundaries are not technical boundaries but responsibility boundaries. AI can generate a crawler that runs, but it will not bear the judgment of whether access frequency is appropriate, whether it follows site rules, whether it creates load, or whether it touches compliance risk. When you cross the line, get blocked, or become responsible for the consequence, the AI tool you pay a few dozen dollars a month will not bear it for you.

You think you merely asked AI to write a piece of code. In reality, you may have handed risk to a tool that cannot bear consequences. The model often will not proactively remind you, because the task frame you gave it was “make this thing,” not “bear the consequences this system creates in the outside world.”

### Example 8: Not Understanding That Some Choices Must Be Made by Humans

Many engineering decisions are trade-offs among multiple reasonable options. AI will not truly make these decisions for you. More precisely, if you do not state a position clearly, it will default to one for you. Because many decisions require not intelligence but trade-off, and the trade-off must ultimately be borne by humans.

For example, how to present “missing information” in a report. The model can phrase missing evidence gently, using words like “may,” “appears,” or “not explicitly disclosed” to make the report smoother. But what the investment team really needs may not be smoothness.

Some gaps must be exposed sharply.

Better to fail loudly than drift silently.

If a company has not disclosed a certain category of key emissions data, the model must not make the report feel complete by writing “disclosure is limited but directionally positive.” That sounds balanced, but it may dilute risk. You must decide: should the system make the report read smoothly, or should it expose risk strongly enough? Should it reduce user discomfort, or protect judgment responsibility?

These choices are not model-capability problems. They are position problems.

If humans do not state a position, the model will choose a tone for them.

But it will not bear responsibility for that tone.

### Example 9: Not Understanding the Evidence Layer and Judgment Chain

Another category of problem is closer to the core of real AI systems: where evidence comes from and how judgment forms.

Give a model a company name and a set of search results, and ask it to generate a fluent summary. In a demo, it can easily look useful. But in a real workflow, the problem immediately becomes concrete: Which materials did it read? Did it miss a key report? Are the materials up to date? Which sentence supports the conclusion? If an expert disagrees, was extraction wrong, evidence incomplete, a rule wrong, or the expert framework itself inconsistent?

The real difficulty is not “make AI summarize better,” but first control the evidence layer, then separate the judgment layer. A company may have dozens or even thousands of relevant documents. You cannot let the model summarize only from “what was found,” because the search results may already have missed the most important material. If the input layer is uncontrolled, the later intelligence is uncontrolled.

The judgment framework of domain experts must also be broken into structures that can be checked. Many judgments sound clear in meetings, but once systematized, they reveal overlapping standards, fuzzy thresholds, undefined exceptions, and “common sense” that was never written down. The model does not simply replace experts; it forces implicit judgment to become nodes that can be discussed, reviewed, and corrected.

A truly useful system must turn “this tool is not useful” into more specific questions: Which material is missing? Which evidence does not support the conclusion? Which judgment node is wrong? Which threshold or exception needs to be changed? A real system cannot be only a beautiful summary interface. It needs controllable material sources, traceable evidence, explicit judgment logic, human review entry points, and a mechanism for accumulating feedback. Otherwise, the better the model speaks, the easier it becomes to package incomplete evidence and unclear judgment into an answer that looks complete.

## These Are Not Hypotheses. They Really Happen.

This is not abstract speculation. Every type of failure has appeared in real systems:

- something looks fine, but the goal has quietly drifted;
- something runs, but too slowly to scale;
- something works on one machine and fails in another environment;
- something is superficially correct, but shatters when it touches an edge case;
- output looks like an answer, but nobody truly knows why it is that way.

So the danger was never “handing things to AI.”

The danger is:

After handing things to AI, nobody can still see when it starts to drift.

## Why “Just Learn to Ask Questions” Is Especially Misleading

The real problem with “just learn to ask questions” is not that it is literally completely wrong, but that it compresses an experience that only holds under high-resolution conditions into a slogan that will be massively misread.

It spreads quickly not only because it sounds like a method. At a deeper level, it gives many people anxious about the AI era a very easy psychological conversion: you do not need to worry about AI rewriting your position; as long as you “learn to ask questions,” you are still the master of AI.

That is seductive. It converts the fear of “will AI replace me?” into the superiority of “I command AI.”

But this conversion is too easy.

You can ask questions. Other people can ask questions too. The real question is: why are your questions better? What gives you the ability to know what to ask, what not to ask, what to follow up on, where to stop, what to accept, and what to reject?

Is it merely because you mastered some prompt technique?

Or because you actually understand the problem itself better?

AI may not automatically replace everyone. But what is more likely is this: people who understand systems, business, and tool boundaries better will use AI to build system-level products and workflows, replacing people who remain at the surface level of asking questions and hoping AI will take over everything.

So “just learn to ask questions” is not too radical. It is too easy. It packages the fact that the AI era requires broader, deeper, more serious learning into a low-cost comfort.

In high-level practice, asking the right question is of course important. But the premise is: you already understand the system, know the boundaries, and can read the output. It is not because you can ask questions that you ask the right ones; it is because you first understand the problem space that you know how to ask.

Here, “system” is not only a software system. It can be an investment process, a research framework, a data production chain, or a judgment mechanism inside an organization. Real problems rarely arrive as neatly prepared questions. More often, there are many materials, unstable sources, inconsistent definitions, judgment standards hidden inside expert experience, and even “what counts as evidence,” “what counts as passing,” and “what must be manually reviewed” may not be clear at the start.

At that point, question-asking ability is not a prompt trick. You first need to know how the problem should be decomposed: where evidence comes from, where the boundaries are, what the judgment logic is, which parts can be handled by the model, which parts must retain human judgment, how errors are discovered, and how feedback returns to the system. Without this understanding, asking questions easily becomes packaging a messy system into a fluent-looking question and expecting the model to return an equally fluent answer.

This is not a choice between technical and non-technical backgrounds. AI really is lowering the entry barriers between many fields, giving more people a chance to step into systems that used to be hard to approach.

The real dividing line is not what you originally studied, but:

- whether you are willing to keep learning;
- whether you have the patience to truly understand something;
- whether you can keep moving from “make it run first” toward “truly understand it.”

Without these, so-called question-asking skill easily degenerates into another kind of surface fluency:

It looks like you can talk about everything a little, but there is no layer you can truly be responsible for.

## Another More Respectable Misreading: Packaging “Not Learning” as “Uniqueness”

Similar to “just learn to ask questions,” there is another popular kind of statement: have critical thinking, break rules, do not be constrained by existing knowledge, create value through uniqueness.

These are not completely wrong.

The real problem is that they are too easy to use as an escape from learning.

Learning is hard. Understanding the history, rules, failure paths, and boundaries of a field takes time. Phrases like “do not be limited by old knowledge” and “preserve uniqueness” conveniently give people a respectable exit: I am not refusing to learn; I am staying open. I am not underprepared; I am breaking rules. I am not failing to understand the system; I am creating a new paradigm.

In the AI era, this narrative gains another layer of packaging.

Some people who sound trend-aware will say: now that AI can write code, do analysis, and generate plans, why spend time grinding through foundations that are hard to learn, slow to learn, and do not pay off immediately? Those still learning fundamentals, understanding systems, and slowly refining judgment seem clumsy. The smarter way, it seems, is to avoid crowded mainstream paths, find a niche ignored by the crowd, and use AI to amplify yourself quickly.

This kind of argument is seductive because it satisfies two desires at once: you do not need to suffer hard learning, and you can believe you have found the smarter route.

But true excess return rarely comes from “avoiding difficulty” itself. It comes from really seeing a problem others did not see, understanding a structure others did not understand, and having the ability to keep advancing in that direction.

If you choose an easier-looking direction merely because technology is hard and engineering is hard, then explain that choice as “differentiation,” it may not be strategy. It may be mistaking avoidance for strategy.

AI will indeed make some previously expensive skills cheaper, and it will create new opportunities in cross-disciplinary fields. But that does not mean foundational training no longer matters. Quite the opposite: when surface abilities become easier for models to fill in, what distinguishes people is often more fundamental: abstraction, system understanding, problem decomposition, long-term learning ability, and the ability to judge boundaries.

But often, the result is not greater uniqueness. It is spinning in place.

One less-discussed point is that many people too easily imagine “senior people are always constrained by old knowledge and therefore kill innovation.” For the very few who truly propose new paradigms, that is not impossible. But for most ordinary people, the bigger risk is not being constrained by old knowledge; it is placing yourself above it before you have actually understood it.

You think you have discovered a new path nobody has walked, but that path may have been seriously tried, tested, and abandoned many years ago. Because you do not know this history, you become unusually excited, spend a lot of time walking into it, and only later discover it was not an ignored treasure but a dead end others had already confirmed.

“Critical thinking” is the same.

If it does not land on concrete objects, constraints, and alternatives, it is not a capability. It is posture. What exactly are you criticizing? What problem did the existing method solve? What was the cost? What will you replace it with? If you cannot answer these questions, “independent thinking” easily degenerates into posture: it looks brave, but in reality it simply did not understand the problem.

The useful order is:

Understand first, then criticize.

Absorb first, then break through.

Know what problem the rules solve before deciding which parts are worth breaking.

Value does not come from saying “I will not be limited by old knowledge.” Value comes from truly understanding the system, understanding the boundaries of old methods, and then making better judgments and trade-offs.

This is especially true in the AI era.

Because models make the cost of “something that looks new” very low. They can quickly generate a new plan, a new framework, a prototype product, or even a complete-looking rebuttal. But if you do not know why the field was originally designed this way, what problems older methods solved, and which paths have already been tried, you can easily mistake “a generated new thing” for a truly new thing.

So real uniqueness is not refusing to learn.

Quite the opposite.

Real uniqueness often comes from understanding existing systems more seriously than others, then walking one step further where they are genuinely insufficient.

## What AI Really Changes Is Not the Need to Learn, but the Entry Point

The change worth celebrating is not “from now on, we do not need to learn.”

It is:

In the past, many people could not even enter the system. Now they finally can.

This matters.

In the past, learning was often difficult not because understanding itself was impossible, but because the entrance was too heavy. For example, if you wanted to learn programming, the first step might get stuck on environment setup, dependency installation, path issues, editor setup, command line, and error messages. Before touching the actual problem, you were already discouraged by peripheral friction.

AI changes this.

It can explain errors, generate a minimal working version, tell you roughly what a piece of code does, and help turn a fuzzy idea into a first prototype. It compresses many thresholds that previously required teachers, colleagues, forums, search, and lots of trial and error into a single conversation.

So AI gives more people their first chance to:

- build a minimal system themselves;
- understand code they could not previously understand;
- trace an error down to its root;
- compare why one solution is more reasonable than another;
- learn by doing instead of being forever blocked outside the door.

This is where its real promise lies: not making understanding unnecessary, but making understanding more accessible.

Someone may ask further: if an ordinary AI subscription can already answer many difficult questions, and even outperform highly trained people on many tasks, what is the meaning of long-term learning?

This question seems sharp, but it understands learning too narrowly.

Learning is not only about obtaining answers. Especially before a person has formed judgment ability, learning trains the brain: attention, abstraction, expression, error correction, and the ability not to give up immediately when facing complex problems.

AI can instantly provide answers. It cannot complete this training for you.

So the stronger AI becomes, the less learning can be understood as “answer retrieval.” The value of learning shifts from remembering answers toward forming understanding, judgment, and correction ability.

Past learning often felt like climbing a high wall first. You had to learn many foundations before you could start building something truly your own. Many people were not uninterested; they were discouraged before even climbing the wall.

Now the wall has been lowered.

You can build something first, then ask: why does it run? Why does it fail here? Why is this solution slow? Why does changing a library break it? Why does the model’s answer look right but not work in reality?

This is a better learning opportunity. But it is still learning.

The difference is that the path has changed: from “learn the system first, then start building,” to “let AI bring you into the system first, then fill in understanding through real problems.”

That is why “AI lowers the learning barrier” and “AI cancels the need to learn” are two completely different things.

The former is an opportunity. The latter is a misreading.

The mature use is not letting AI help you bypass understanding, but letting AI help you enter more quickly into understanding processes that used to be hard to reach. It is like temporary scaffolding that lets you reach higher places; but scaffolding is not the building itself. Whether you can stand steadily in the end still depends on whether you actually built the structure.

So what should be encouraged most in the AI era is not “you can build without learning.”

It is:

In the past, many people never had the chance to begin because the door was too high.

Now the door is lower, and those who truly want to learn can learn faster, deeper, and closer to real problems.

That is the most positive change AI brings to learning.

## Not Vibe Coding, but High-Speed Review of System Responsibility

Half a year ago, after Opus 4.5 came out in late November 2025, the author for the first time clearly felt that coding agents were no longer merely tools that could help write a few snippets, but were truly beginning to change the development process.

Usage intensity rose quickly, and the quota began to feel insufficient. The author and another colleague even discussed whether to raise this in a team meeting: if the tool really could significantly improve development efficiency, quota was no longer a personal preference but a productivity resource.

But when we shared how useful the tool was with the team, the reactions were interesting.

A colleague with a more IT-management or platform perspective said that, if it was genuinely useful, their own quota could be reallocated to development use.

Another colleague joked about it as a kind of AI-coding status contest.

These remarks were not malicious. But they accurately exposed a common misunderstanding: if someone has not used agentic coding tools at high intensity, it is easy to understand them as “letting the model write code for you,” or even as a light kind of vibe coding.

The real experience is exactly the opposite.

After using agentic coding tools intensely, the strongest feeling is not “coding became easy.” Quite the opposite: after a few hours, it can be exhausting. Because the model no longer only completes a few lines. It quickly understands, modifies, refactors, fixes, and even actively advances the whole codebase. What the developer really does is no longer writing code line by line, but protecting system boundaries amid high-speed change.

The tiring part is not that the model is not smart enough. It is that it is too smart, too fast, and too plausible. It rapidly reads code, changes functions, refactors structures, and fixes local problems. The developer must keep up with what it is doing, understand its implicit assumptions, and judge whether these changes will break another invisible part of the system.

Once, the author asked an agentic coding tool to fix a problem. It did fix it. But it did not notice that the same function was reused by another pipeline. The change was valid for the current problem, but would very quietly introduce a new problem into another pipeline. In the end, it was not the model that discovered the risk; the developer stopped it by intuition.

This is the real boundary of agentic coding tools.

They can fix bugs. But they do not necessarily know what contract the buggy function carries inside the whole system.

So if you merely let the model generate freely and accept freely, then yes, it may be vibe coding.

But high-intensity use of agentic coding tools is more like high-speed review of system responsibility.

The model fixes bugs. The human protects the system.

What the model compresses is implementation cost, not responsibility cost.

This experience also explains why the sentence “agents will do all the work, so fundamentals no longer matter” is dangerous. Agents will do more and more execution-layer work, and may do it faster and more plausibly than humans. Precisely because of this, humans need even more to know what it changed, who it affects, whether it broke an implicit contract, and when it must be stopped.

Execution can be delegated. Responsibility cannot be outsourced.

## So What Is the Mature Attitude?

The mature attitude is not:

- I write everything myself;
- I hand everything to the model;
- I misread “knowing how to ask” as not needing to understand;
- AI will keep getting stronger anyway, so understanding systems is no longer necessary.

The mature attitude is:

I use AI as much as possible to compress learning and implementation cost, but I do not give up understanding the system itself.

“Understanding the system” here does not mean everyone needs to become a professional software engineer. Not everyone needs to write low-level frameworks, optimize compilers, or maintain distributed systems.

But if you are going to hand more and more work to AI, you at least need to understand: how inputs deform, where tools distort, how outputs are verified, how errors surface, and who defines boundaries. Otherwise, what you learn is not delegation, but handing responsibility to a black box you cannot read.

This is also why many engineers who already use AI heavily to write code have not become more relaxed, but busier than before. The leverage increase often brings not more rest, but more tasks, higher response speed, and larger delivery scope. Organizations do not automatically return the saved time to you because you became faster. More commonly, they immediately consume that capability.

So the question is never only “can AI save you time?” More often, the time AI saves is quickly taken by new expectations. In that environment, what determines whether you have leverage is not whether you can produce a pile of things faster, but whether, under higher speed, larger scope, and stronger delegation, you can still preserve judgment, correction, and control.

The real competition is not between humans and models, but between humans: who learns earlier to borrow leverage, who reorganizes workflows faster, and who can remain responsible at higher speed.

Only people who understand systems can judge:

- when to delegate;
- when to stop;
- when to doubt;
- when to rewrite;
- when to personally define the boundary;
- when responsibility must be pulled back into human hands.

This is the premise for keeping leverage in your own hands in the AI era.

## Closing: Asking Questions Is Not a Substitute for Understanding

If this essay were compressed into one sentence, it would be:

AI lowers the barrier to learning systems; it does not cancel the need to understand systems.

Delegation is not a substitute for understanding. Stronger delegation only makes understanding more important.

To use another metaphor, the stronger AI becomes, the more it resembles a group of increasingly capable sheepdogs. They run fast, react fast, and can run many paths you used to have to walk yourself. In the past, you may have had to herd the sheep step by step. Now the sheepdogs can run ahead by themselves, bring scattered sheep back, and even find faster routes.

But the stronger the sheepdogs become, the less the shepherd can disappear. The real question is never “can the dogs run,” but where the flock should be taken, which road has a cliff beside it, which path looks short but cannot be taken, when to let them continue, and when to whistle them back.

If the shepherd does not understand the terrain and only says “move the sheep faster,” the more capable the sheepdogs are, the more dangerous they become. They will execute an unclear goal faster, and they will drive the flock toward the wrong direction faster.

Delegation is not leaving the pasture. Delegation is moving from personally chasing every sheep to becoming the person who must understand terrain, boundaries, and direction.

If the rebuttal is: “Do you not see that models get stronger every year? In one or two more generations, they will naturally find the key points and make the optimal choices for me,” that is just the mistake discussed in Part 8B in another form: compressing rising capability directly into default deliverable autonomy.

Models will continue to get stronger over the next few years. That is not the problem; it is the premise. Precisely because it is the premise, keeping up with them, understanding them, and controlling them matters more. Otherwise, capability growth will only make loss of control arrive faster.

So the most dangerous thing is not that the sentence is literally completely wrong. The real danger is that it spreads at the lowest resolution as a very easy sentence:

Just learn to ask questions.

The high-resolution version is not that sentence itself. The high-resolution version is: when you already understand the system, know the boundaries, and can read what AI did for you, asking the right question is of course critical.

But once it is read as “therefore I do not need to learn those boring things,” it begins to mislead.

So the question was never “is asking important?” The question is: do you understand enough to ask the right question, read the answer, and take over in time when it begins to drift?

AI will of course become stronger. Precisely because of that, learning will not become unimportant. It will become more like a dividing line.

Many people can ask questions. People who can be responsible for systems are truly scarce.

Main-series endpoint: → [Part 11: Evidence](/blog/evidence-en/)

Related main essays: → [Part 6: The Leverage Gap](/blog/leverage-gap-en/) · [Part 7: Context Accumulation](/blog/context-accumulation-en/) · [Part 8A: The Delegation Problem](/blog/delegation-problem-en/) · [Part 10: Two Rooms](/blog/two-rooms-en/)

Other bonus essays: → Bonus Essay: Standing in the Middle Ground · [Bonus Essay: Rebuttal — We Asked AI to Tear Down the Whole Series](/blog/rebuttal-en/)
