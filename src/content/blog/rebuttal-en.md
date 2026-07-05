---
title: 'Bonus Essay: Rebuttal — We Asked AI to Tear Down the Whole Series'
description: 'Eleven essays, one argument. Now we ask AI to overturn all of it.'
pubDate: '2026-06-25T12:00:00Z'
heroImage: '../../assets/series-bonus-a-rebuttal.jpg'
lang: 'en'
---

> Series: “We built a pipeline with tens of thousands of lines of code. Why could agents not do it?”

[Previous: Part 11 — Evidence.](/blog/evidence-en/)

[阅读中文版。](/blog/rebuttal-zh/)

Eleven essays, one argument. Now we ask AI to overturn all of it.

Previous essay: Part 11 — Evidence. The investment team expected another demo. What they got was a production system. The difference was not the model. It was engineering.

## The Karpathy Test

Andrej Karpathy once described a workflow every writer should be wary of:

You write a blog post. You spend four hours using an LLM to polish the argument again and again. Wow, it feels great, so persuasive!

Then a thought occurs: ask it to argue the opposite. The LLM tears the entire argument apart and convinces you that the opposite is right. Hilarious.

His conclusion was that LLMs are extremely good at arguing almost any direction. They will enthusiastically reinforce whatever position you give them — and if you ask them to reverse direction, they will destroy it with the same enthusiasm. This is actually useful, but only if you actively ask it to argue both sides.

That sounds familiar. Not surprising. It is, in essence, the convergence of human internet language.

We wrote eleven essays arguing that composition — LLM judgment + engineering precision + human expertise — is the right architecture for production-grade AI systems.

But if the argument of this series only holds with the wind at its back, it is not worth believing.

So we thought: let us run a Karpathy test. Feed the whole series to GPT5.5 and Opus4.6:

Argue the opposite. Tear this series down.

Below are the eight strongest counterarguments the models generated over multiple rounds, then repeatedly organized by us, presented as humanly as possible. After each one, we respond honestly.

## Counterargument 1: Your Snapshot Will Go Out of Date

Attack: You are writing in early 2026. The pace of progress in agent frameworks makes any point-in-time evaluation unreliable. OpenAI function calling was crude in 2023, acceptable in 2024, and quite mature by 2025. By the time readers see this series, the claim that “agents cannot handle orchestration” may already have been overturned by facts. You are fighting the last war.

Our response: This is one of the strongest counterarguments, and we take it seriously.

Yes, agents will improve. The question is what type of improvement matters. If models become stronger at semantic judgment — better at classifying links, understanding page content, and evaluating relevance — our architecture benefits directly, because that is exactly the layer where we already use them. The pipeline gets the upgrade for free.

The harder question is whether agents can master the other part: state management across thousands of websites, budget allocation, retry logic, graceful degradation, `robots.txt` compliance, and PDF pipeline management. These are not purely intelligence problems. They are engineering problems. Making the model smarter does not automatically solve them — it only makes the model better at solving the parts someone has clearly defined and verified.

But honestly: we do not know where the boundary will be two years from now. What we know is where the boundary is today, in production, at institutional scale. That is what this series records.

Verdict: Partly valid. The snapshot concern is reasonable. We tried to focus on structural arguments: why control flow needs determinism, why auditability needs traceability, why production systems need responsibility structures. These do not fully depend on a specific model generation. But some concrete comparisons will age. That is the unavoidable cost of writing in a fast-moving field.

We also admit that models will keep pushing the boundary, and many engineering structures that are explicit today may be absorbed by higher-level tools and frameworks tomorrow. But that does not mean the responsibility structure automatically disappears. Boundaries will move; the need for someone to be responsible will not.

## Counterargument 2: Unfair Comparison — A Carefully Polished Pipeline vs. an Out-of-the-Box Agent

Attack: You spent months engineering a pipeline, polishing edge cases, handling failures, and accumulating domain knowledge. Then you compare it with a generic agent given zero iteration time. Of course the pipeline wins. Give an agent the same engineering investment — custom tools, structured prompts, feedback loops, error handling — and the comparison looks completely different.

Our response: This is right, and we should be clearer.

Our comparison was never “our pipeline vs. a carefully engineered agent system.” It was “our pipeline vs. the narrative that agents can replace engineering.”

What we oppose is absolutely not “agents can do useful things after substantial engineering.” Of course they can. When building this pipeline, we ourselves used AI-assisted coding heavily: drafting implementations, explaining errors, rewriting functions, refactoring local modules, and proposing alternatives. Many ideas landed quickly precisely because models compressed implementation cost.

But compressing implementation cost is not the same as removing engineering responsibility. Key changes still need humans to review, confirm, modify, and integrate them. A fix that looks reasonable must still be placed back into the whole pipeline to check whether it breaks another module, process, or implicit contract.

A carefully engineered agent system — with structured tools, error handling, state management, budget controls, human supervision, traceable output, and feedback loops — looks like what?

It looks very much like a pipeline that uses an LLM at key judgment points. In other words, what we built.

You can even say it the other way around: once you engineer an agent to the point where it can be used in production, it is no longer a “naked agent.” It has become a system constrained by tools, rules, state, logs, budgets, feedback, and human responsibility.

At that point, the difference between “a carefully engineered agent” and “a pipeline that uses an LLM at judgment points” quickly becomes blurry.

So what this counterargument really reminds us is not “the pipeline won unfairly,” but this: if you want agents to work reliably, you eventually have to add back the engineering that was supposedly no longer needed.

We do not oppose agents. We oppose the idea that agents can eliminate the engineering around them.

Verdict: Valid at the framing level, not at the substantive level. We should distinguish more carefully between “agent as an architecture” — possible, sometimes good — and “agent as a replacement for engineering,” which is what we are really arguing against. Criticism accepted.

## Counterargument 3: Your 90/10 Ratio Is Domain-Specific, Not Universal

Attack: Institutional-scale web crawling is an unusually orchestration-heavy domain. Thousands of websites, each with different structure, rate limits, JavaScript rendering, PDF handling — of course deterministic code dominates. But in code generation, creative writing, research synthesis, or customer support, the ratio may be 50/50, or even 10/90 in favor of the model. You are generalizing from one pipeline to the whole AI field.

Our response: This is right, and the series partly admitted it. The 90/10 ratio is specific to our domain. In a customer-service chatbot, the LLM does most of the work and the engineering layer is thinner. In code generation, the model carries a larger share.

Moreover, if we look at the development process itself, we also used Opus heavily for coding assistance. So “90/10” describes the runtime division of responsibility in the production system, not whether the developer used AI while writing code.

Our rebuttal is that even in domains dominated by LLMs, the engineering share is higher than people think.

Cursor is not “Claude with a text box.” Claude Code is not “the model can write code, therefore the product naturally exists.” These products are complex systems: context engineering, file indexing, diff management, multi-model orchestration, tool calling, permission control, user-experience design, testing, and rollback. In other domains, 90% may become 70% or 60% — but it will never be 0%.

And the narrative we oppose says it is approaching 0%.

The deeper point still holds: in any domain that requires reliability, traceability, and large-scale auditability, the engineering share rises. Our domain happens to push these requirements to the limit. But regulated finance, medical technology, and enterprise software have similar needs.

Verdict: Partly valid. We should say more clearly that the precise ratio varies by domain. The principle — engineering does not disappear — is general. The number is not.

## Counterargument 4: Professional Bias — You Built What You Are Good at Building

Attack: You have an engineering background, so naturally you see the problem as an engineering problem. You are good at building pipelines, controlling boundaries, and handling failure modes, so of course you ended up building a heavy engineering pipeline and then saying it is more reliable than an agent. A team better at prompting, agent orchestration, or model productization might have reached a completely different solution. What you saw was not the objective optimum, but your own professional path.

Our response: This stings, because it has truth in it.

Yes, we entered the problem with our own abilities and preferences. We know engineering, data pipelines, error handling, traceability, and production environments, so we see those problems more easily and solve them more naturally in those ways.

That should be admitted.

But this counterargument misses one thing: the constraints were not invented by us. They came from the investment team, the production environment, and institutional requirements.

They needed:

- auditability;
- traceability;
- coverage across thousands of companies;
- predictable cost;
- reproducible output;
- results that could enter a real investment workflow.

These are not engineer preferences. They are conditions the system had to satisfy.

If a team stronger in agent systems built it, the implementation might differ. It might use more tool calls, more complex agent orchestration, and more automated feedback mechanisms. But as long as it has to enter the same investment workflow and bear the same audit and responsibility requirements, it still cannot avoid these structural properties: inputs must be controlled, process must be traceable, outputs must be reviewable, errors must be locatable, and responsibility must be assignable.

We also did not decide at the start to build a heavy engineering pipeline. We tried simpler solutions first. The pipeline grew precisely because simpler solutions failed on the dimensions users actually cared about.

So yes, there is professional bias here; but it is not only professional bias.

If a solution exists only because we are good at it, that is bias. If a solution is forced out step by step by real constraints, that is evidence.

Verdict: Valid at the observer-bias level, not at the production-constraint level. We should admit that our engineering background shaped the problem statement and implementation path. But the same production requirements would push different teams toward similar system properties: controlled inputs, traceable process, auditable output, and assignable responsibility.

## Counterargument 5: The Cost Argument Is a Snapshot, Not a Trend

Attack: You say agents are 3–10x more expensive. But model costs keep falling. The cost comparison that makes your pipeline look efficient today may make it look expensive tomorrow, because agent architectures benefit directly from cost declines: more calls become cheaper. Your deterministic code has fixed engineering-maintenance cost. The economic argument may flip within 18 months.

Our response: The cost decline trend is real, and we respect it. But this argument mixes two different kinds of cost.

Interface cost — the price of calling the model per token — is indeed falling. If the only cost of an agent system were model calls, this argument would be decisive.

But at scale, the main cost is not only model-call cost. It is:

- Debugging cost. When the agent quietly makes the wrong decision on website 2,847, how do you find it? How do you trace it? How do you fix it without affecting the previous 2,846 websites?
- Consistency cost. When you rerun the pipeline next month, are the results comparable? Can you explain the difference to a portfolio manager?
- Audit cost. When compliance asks, “Why did the system classify this page as ESG-related?”, can you answer?
- Responsibility cost. When output enters an investment workflow, who can explain, correct, and own the result?

These costs do not automatically fall because model calls become cheaper. They rise with system complexity. And an agent architecture — if unconstrained by engineering — increases system complexity, because every decision point can become a probabilistic branch instead of a deterministic one.

Cheaper models make agents more viable for experimentation. They do not automatically make agents more auditable for production.

Verdict: Partly valid in interface economics, not valid in total cost of ownership. We should separate “cost per model call” from “cost of reliable operation at scale.” The former is falling. The latter has not automatically fallen, and that is where our argument really sits.

## Counterargument 6: You Are Using Today’s System Complexity Against Tomorrow’s Abstraction

Attack: Your entire series assumes system complexity must be explicitly borne by engineering. But if future model capability continues to improve, it may absorb more and more of the structure you currently think must be expressed in code. Tool calling, state tracking, long-horizon tasks, self-correction — if these are gradually internalized by models, then the engineering you describe may be merely a substitute structure for current capability limits. In other words: you are treating “temporarily necessary engineering” as “permanently necessary engineering.”

Our response: This is a very natural and very strong counterargument. But it hides an assumption:

More capability = less system complexity.

Reality is often closer to the opposite. Once capability gets stronger, it is usually not used merely to solve yesterday’s already-well-defined problem. It is immediately used to expand the problem itself.

That is also why even today’s strong models often do not solve a very concrete task correctly in one shot. Ask a model to generate chart code directly from a table, and the first version may read the wrong field, choose the wrong chart type, mishandle dates, groups, or missing values; only after later rounds does it gradually correct itself. The problem is not only that the model is not strong enough. The goal itself often becomes clear slowly through feedback.

Models can compress implementation, but they do not form the goal for you. They can unfold possible paths, but they do not decide which path should finally converge. They do not have their own reason to stop.

So what we are really arguing against was never “future models will be stronger.” Of course they will. What we oppose is translating rising capability directly into “system complexity will automatically disappear.” Often, stronger capability does not make engineering leave the stage. It upgrades the task, lengthens the feedback loop, and increases the weight of the responsibility structure.

Abstraction moves upward. Constraint does not disappear.

Verdict: Valid on the time dimension, not on the structural dimension. Future models will continue to absorb some structures that are explicit today. But as long as goals need to be formed, results need to be accepted, and responsibility needs to be assigned, the system will not automatically leave the stage just because models become stronger.

## Counterargument 7: Goal Formation Is Not the Core Problem

Attack: You increasingly build the argument around “goals form through feedback”: humans judge, humans converge, humans update the goal. But as model capability improves, this itself may be partially internalized. Models can already propose multiple candidate plans, compare outputs, self-critique, self-correct, and even simulate a shift where “maybe the goal is actually something else.” In other words: what you call human responsibility for goal convergence may just be a current model limitation, not a stable structural division.

Our response: This counterargument is deeper than “agents will become stronger,” because it attacks not today’s implementation but the final structural division itself.

But there is a key distinction: proposing candidate goals is not bearing a goal; simulating goal updates is not deciding where to stop.

Models can of course generate multiple directions, and even criticize their previous output. But what they are doing is still expanding the possibility space, not defining which possibility space must be fixed. Goal formation is crucial not because the human brain is more mysterious than the model, but because the final goal connects to cost, responsibility, trade-off, and stopping condition.

A model can help you see what you failed to specify. It cannot bear the moment of “now we calculate it this way.” Many agents will help you do that, but not necessarily in the way you want.

So we agree: more and more local actions inside goal formation will be absorbed by models. But the final jump of “forming a goal” is not semantic inference. It is the landing point of responsibility. As long as responsibility has not been automated, goal convergence will not be fully automated.

Verdict: Valid at the local-action level, not at the final-convergence level. Models will participate more and more in goal formation. But participating in the process is not the same as owning the final decision.

## Counterargument 8: The Autopilot Boundary Will Keep Expanding

Attack: You distinguish autopilot — formed problems — from copilot — problems still forming — but this boundary is dynamic. As model capabilities improve, more tasks that used to require human collaborative judgment will be rewritten as “formed problems.” Feedback loops are also being automated: models can self-test, cross-test, run tools, backfill errors, and keep correcting. In that view, the copilot space keeps shrinking and the autopilot space keeps expanding. Your framework may merely describe a transition period.

Our response: This is also a strong attack, and we partly accept it.

The boundary of autopilot will of course expand. Many local tasks that still need human supervision today will become stable automation modules a few years from now. Machine-machine feedback will also increase, and systems will get better at turning once-expensive human checks into routine pipeline work.

But that does not mean the copilot space will linearly disappear.

Because whenever autopilot absorbs a batch of already-formed problems, organizations and users usually do not stop where they are and enjoy the ease. They immediately use the capability to push into larger scope, fuzzier goals, longer chains, and heavier responsibility. Then new “still-forming” problems appear.

The boundary will move, but not in only one direction toward “eventually only autopilot remains.” More often, both sides expand at the same time: automation eats old tasks, reality pushes out new problems.

So what is stable is not how much territory autopilot or copilot covers. What is stable is the distinction itself:

Formed problems can be automated more. Still-forming problems can only be collaborated through.

This line will move, but it will not disappear.

Verdict: Valid that the boundary will move, not valid that collaboration will end. Automation will expand; but as long as reality keeps producing problems that are not yet formed, the copilot structure will continue to exist.

## What This Exercise Proved

Eight counterarguments. None of them is boring. At least three made us uncomfortable. And under our guidance, after multiple rounds of polishing and revision, the model generated them quickly.

But the truly important part of this exercise is not whether we blocked them one by one.

The important thing is this: in a short time, an LLM can generate eight structurally complete, individually plausible, and even mutually incompatible counterarguments. It can support multiple contradictory but internally reasonable world models at the same time.

That is not a flaw. It is exactly what makes it useful.

The model expands possibility. The system compresses possibility.

It does not know which counterargument is closer to evidence and which is merely an attack surface; which one touches real constraints and which one only attacks wording; nor will it voluntarily stop at “do not conclude yet” just because a judgment has not formed. It generates. We converge.

This is what Karpathy was warning about. LLMs will argue any direction with full conviction. With the same enthusiasm, they produced the arguments of our series. If we only ask them to reinforce our position — which is what most people do — we will feel like geniuses.

The Karpathy test reveals not only that “LLMs flatter you.” It also reveals a deeper feature of LLMs as tools: to a large extent, they continue along the direction, tone, frame, and implicit goal you give them. Ask it to support a view, and it supports it beautifully. Ask it to rebut the same view, and it rebuts it beautifully.

Different products appear to have different “personalities” often because the system has already injected some default tone, default boundaries, and default preferences for you. You think you merely entered a question, but the question itself, the system prompt, the product style, and default safety policy have already shaped the direction of the answer together.

So LLMs are especially good at one thing:

Making a direction sound complete.

That is useful.

But it is also dangerous.

## Balance Is Not Judgment

One of the most annoying things about many LLM answers is not that they are wrong, but that they are too good at making everything sound reasonable.

They often begin with “overall, you are right,” then immediately add a “but”; then list three reasons why you are right and three reasons why you should still be careful. This structure looks balanced, and it often is helpful. But if you are looking for judgment, it becomes a soft kind of delay: everything is explained, every angle is cared for, but the real priority is never cut out.

Real judgment is often not about whether something “has reasons.” Almost any important choice has reasons on both sides. Continuing has reasons; stopping has reasons. Moving faster has reasons; moving more steadily has reasons. Automation has reasons; preserving human judgment also has reasons.

The model can write all of these reasons well. It can endlessly generate both sides, endlessly add “on the other hand,” endlessly remind you that “it depends on the specific situation.”

But judgment is not listing both sides completely.

Judgment is: in this concrete reality, which reason is heavier? Which risk are you willing to bear? Which cost must you accept? When should you stop, when should you continue, and when should you choose an imperfect but good-enough plan?

More troublingly, many weights in real judgment do not exist in the form of “listable reasons.”

When people make choices, they usually do not actually list every factor, score each one, sum the result, and mechanically choose the highest score. Many weights come from experience, organizational context, trust relationships, failures seen in the past, risk tolerance, and a kind of intuition that is hard to fully explain.

These things may not exist completely in internet text. They may never have been written down, or may already be distorted by the time they are written down. Even the person making the judgment may not be able to fully explain all the weights.

So the model can list reasons for and against beautifully, and still not know which reason should weigh more in reality.

Some people look extremely cautious: they first discuss advantages, then disadvantages; a few days later they return to the advantages, then a few days later to the disadvantages. Every round makes sense, but no decision is ever made. The problem is not that they failed to see both sides. It is that they did not form a judgment.

LLMs amplify this state.

You think you are becoming more comprehensive, but in fact you are letting the model help you keep circling inside possibility. It makes every direction look reasonable, every choice receive a supplement, every conclusion receive a caveat. In the end, what you get is not judgment, but an increasingly complete and increasingly hard-to-converge map of possibility.

If no person ultimately says:

Under these constraints, we go this way.

Things will not move forward.

Balance is not judgment. Judgment is knowing when to stop balancing.

Listing reasons is not judgment. Weighting reasons, and bearing the consequence of that weighting, is judgment.

The model can help you see more sides.

But it will not bear the consequences of the choice for you.

This also explains why coding agents are among the first to look especially strong.

Software development is not a simple field, but it is relatively suitable for agents: boundaries are clearer, feedback is denser, toolchains are more mature, and errors are easier to expose. Whether code runs, whether tests pass, what the diff changed, whether a version can be rolled back, whether an interface was broken — many checks are relatively explicit. More importantly, software engineering has accumulated decades of practices that can be written down, learned, and turned into tools.

So tools like Claude Code or Codex may look as if they are “making engineering judgments themselves,” but they are not judging in a vacuum. Behind them stands a highly engineered software world: codebases, tests, version control, command lines, error logs, package management, engineering conventions, and the preferences accumulated by many mature developers.

In other words, coding agents are strong not only because the model is strong, but because the model has been placed inside a relatively clear, testable, feedback-rich, rollback-friendly system.

But software development is only one subset of the world.

Once you enter business judgment, investment workflows, organizational collaboration, or domains where user needs have not yet formed, the situation is completely different. There may be no existing test suite, no single correct answer, no clear preference function, and no mature tool environment to tell the model what matters more, what must not cross the boundary, what evidence must be preserved, and what must be handed back to humans.

In these domains, models are still useful. But they will not automatically fill in the missing system layer for you.

If coding agents do part of the orchestration and engineering for developers, that is because software development itself already contains a great deal of orchestration and engineering that can be productized. In investment, compliance, research, governance, and organizational workflows, that systematized work often does not yet exist.

So the problem returns:

Claude Code inside software development means someone else has already done part of the systems engineering for you.

Claude Code inside your domain may require you to first do that systems engineering yourself.

This is why the success of coding agents cannot be directly extrapolated into “all domains will soon be automatically solved by agents.” The further you move into domains with unclear goals, sparse feedback, complex responsibility, and implicit preferences, the more someone first has to build the problem space, evidence structure, feedback loop, and responsibility boundary.

Model capability matters.

But the system layer around the model matters just as much.

This is the delegation problem Part 8A kept returning to. If you delegate argument to a model and only ask it to confirm your view, you are not thinking — you are outsourcing belief to a system with no beliefs.

But if you deliberately ask for the strongest rebuttal, sit inside the discomfort, and update where the argument is right, the model becomes genuinely useful.

Not an oracle.

A sparring partner.

More precisely: when the problem has already formed, it can behave more like autopilot; but when the problem itself still needs to be judged, converged, and updated, it can only be copilot. This exercise was fundamentally the latter. The model could unfold every attack path; none could be automatically accepted. All convergence came from human judgment about evidence, structure, and real constraints.

## What We Updated, and What We Did Not

The first five counterarguments mainly attacked the external boundary of the series: time, comparison method, scope of applicability, author bias, and cost trend. The last three went deeper, attacking the structure itself: whether future models will absorb engineering, goal formation, and the boundary of collaboration.

This was not formalism. It really changed how we later organized Parts 8 through 11. We no longer discussed only “why agents cannot do it,” but more clearly separated four things: which problems have already formed, which goals are still forming, which outputs need engineering constraints, and which judgments must be borne by people and organizations.

After this exercise, what did we update?

1. We will say more clearly that the 90/10 ratio is domain-specific. The principle is general. The number is not.
2. We accept the snapshot problem. This series describes 2026. Some details will age, but the structural arguments should live longer.
3. We will explain more clearly what we are actually against. Not agents. Not AI. The specific claim that “agents eliminate the need for engineering.”
4. We emphasize goal formation and responsibility structure more. Because the strongest rebuttal is no longer merely “future models will be stronger,” but “will future models absorb goal formation and the boundary of collaboration?”

Here is what we did not update:

- The core argument. Composition beats solo performance. Engineering does not disappear. LLMs are tools, not replacements.
- The evidence. The investment team’s experience. The pipeline’s production record. The architectural properties that made it usable.
- The conclusion. Build it right. Models do judgment, code does control, experience sets direction.

None of the eight counterarguments truly pierced the evidence itself. They attacked:

- the timeliness of the argument: whether it will age;
- the expression of the argument: whether the comparison is fair;
- the scope of the argument: whether it is domain-specific;
- the bias of the arguer: whether we built what we are good at;
- the cost trend of the argument: whether price changes will reverse it;
- the temporal extrapolation of the argument: whether today’s engineering will be eaten by tomorrow’s abstraction;
- the goal structure of the argument: whether goal formation will be absorbed by models;
- the collaboration boundary of the argument: whether autopilot will keep swallowing copilot.

In other words, the rebuttals mainly hit three layers: time will change, ratios will change, boundaries will change. But they did not pierce the final layer: production responsibility does not automatically disappear because language becomes more fluent.

These are all real challenges. But none of them answered the hardest layer:

Can this system deliver in production right now?

This is not a coincidence. At this level, the LLM itself cannot generate evidence either.

Because evidence is not a language structure. It is an operating result.

It can generate argument.

It cannot generate delivery.

## The Meta-Lesson

The whole exercise is a miniature version of the series’ argument.

We used an LLM to generate counterarguments. It did extremely well — sharp, clearly structured attacks, one version after another, very quickly. Few human devil’s advocates can be this fast and this broad.

But it still needed humans to evaluate. To decide which points held. To update where they made sense. To hold the position where evidence supported it. This exercise was not finished in a few seconds; the model quickly expanded the possibility space, but humans spent many days judging what had truly matured, where we should update, and which conclusions still stood.

The LLM provided possibility space. Humans provided convergence direction. The combination produced something neither could have produced alone.

So what finally stabilizes this series is not whether we can write a prettier argument, but what happened in Part 11: the system entered a real team’s schedule, judgment process, and responsibility structure.

That is why, by the end, this bonus essay is no longer merely “we defended the original conclusion.” It is more like using a rebuttal experiment to prove again the structure the whole series has been arguing for:

Models can expand possibility. Systems compress possibility.

AI is good at understanding meaning. Code is good at guaranteeing behavior. Experience decides when to use which. None of the three can be missing.

The pattern of writing a blog series about building this pipeline is actually the same.

Main-series endpoint: → [Part 11: Evidence](/blog/evidence-en/)

Start from the beginning: → [Part 1: The Impossible Task](/blog/impossible-task-en/)

Other bonus essays: → Bonus Essay: Standing in the Middle Ground · [Bonus Essay: Understand Systems Before Delegating to Systems](/blog/understand-systems-en/)
