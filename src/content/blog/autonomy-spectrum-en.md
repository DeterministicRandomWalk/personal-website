---
title: 'Part 8B: The Autonomy Spectrum — The Real Question Is Not “Whether,” but “Which Layer”'
description: '“Full autonomy” is not a design answer. The real question is which layer can be delegated, which block can be delegated, to what degree, and who catches the failure.'
pubDate: '2026-06-21T12:00:00Z'
heroImage: '../../assets/series-08b-autonomy-spectrum.jpg'
lang: 'en'
---

> Series: “We built a pipeline with tens of thousands of lines of code. Why could agents not do it?”

[Previous: Part 8A — The Delegation Problem.](/blog/delegation-problem-en/)

[阅读中文版。](/blog/autonomy-spectrum-zh/)

“Full autonomy” is not a design answer. It is closer to an overpackaged slogan. The real question has never been whether autonomy should exist, but which layer can be delegated, which block can be delegated, to what degree, and who catches the failure.

Previous essay: Part 8A — The Delegation Problem: Why Agents Cannot Simply Start. Ambiguous goals drift silently. Tools have ceilings, and the model cannot see them. Both happen before code.

Terms like “fully automated,” “fully autonomous,” and “end-to-end autonomy” are attractive not only because marketing likes them, but also because they can genuinely hold for some bounded, repeatable, stable tasks. The problem is that local validity is easily described as global validity. These terms also satisfy a deep human desire: compress away complexity.

Better still, compress away premises, exceptions, responsibility, and feedback loops. Better if the tangled mess of the real world can finally be closed with one sentence: “let the agent do it.”

The problem is that much complexity does not disappear just because you replace it with a bigger word. Usually it is transferred, hidden, or settled later. Today you call it “full autonomy” in a slide deck; tomorrow it reappears as budget loss, distorted inputs, boundary drift, and unclear responsibility.

LLMs have indeed given us an unprecedented way to compress complexity. Things that once required explicit rules, glue code, manual switching, and local judgment can now often be pushed into a natural-language interface. That is a very real advance.

But “can compress a lot of complexity” does not mean “complexity has been eliminated,” and still less does it mean “we have reached the final state of autonomy.” LLMs are powerful, but they are more like a force that pushes systems much farther forward, not a declaration that the road has ended.

Part 8A drew one line: you cannot delegate an entire problem that is still forming.

The emphasis is not “cannot delegate.” It is “entire.”

“Autonomy” is a useful word. So useful that tool calling, process execution, local adaptation, and strategic judgment can all be stuffed into it; and so coarse that layers, premises, responsibility, and failure modes can all be blurred together by one phrase: “let the agent do it.”

So Part 8A answered why you cannot hand over the whole thing. This essay answers: if you cannot hand over the whole thing, how should you hand it over?

What it tries to add is not merely the true but still too-coarse sentence “autonomy is a spectrum.”

It tries to add a more important judgment: the expansion of autonomy never advances as a whole. It always advances unevenly by layer, by block, and by maturity.

Where should autonomy be placed so that it does not cross the boundary?

## The Mistake Is Not Autonomy, but Treating Autonomy as a Switch

In public discussion, autonomy is often described as a binary switch:

- either “fully autonomous agents” will soon take over whole workflows;
- or “humans must always remain in the loop and never let go.”

Each of these claims captures a piece of reality. The problem is that they compress something that should be judged by layer, block, and maturity into a yes/no question.

Real systems do not grow that way. Browser automation can be given a lot of freedom; budget ceilings cannot. Local code implementation can be highly delegated; problem definition cannot. Known disturbances can be partially handed over; success criteria cannot be left for the model to decide.

Autonomy is not a switch. It is a spectrum.

But merely saying “spectrum” is still too coarse. Within the same layer, different task blocks vary enormously in how delegable they are. What needs to be added is how this spectrum unfolds internally by layer, block, and maturity.

This is where public narratives most often go wrong: they describe what is really a layered expansion problem as a whole-replacement problem.

If an analogy is needed, it is more like a flight system than the light switch at your front door. You can turn on autopilot at cruising altitude, give altitude holding to the system, and let rules handle alerts — but you cannot casually hand over “where are we actually flying, should we turn back now, and who makes the call when something goes wrong.” Advertising driver assistance as “you can sleep in the back seat now” is usually not an engineering conclusion. It is a marketing slide.

## Autonomy Is Not One Thing — There Are at Least Four Layers

Break “autonomy” apart, and there are at least four layers:

1. Tool-level autonomy — helping you click buttons
2. Workflow-level autonomy — helping you run processes
3. Operational autonomy — adjusting when things change
4. Strategic autonomy — deciding what the problem is for you

All of them look like “AI doing things by itself,” but their risk profiles are completely different. That is why questions like “can coding be handed to AI?” are almost meaningless. Within the same coding work, some task blocks are at the first layer, while others have already reached the fourth.

The real judgment should not be about occupations. It should be: which layer does this specific task block belong to, how mature are the tools and processes it depends on, and is it executing a problem that has already formed or quietly rewriting the problem itself?

These four layers are not a leaderboard. Lower layers can be very powerful, while higher layers still cannot be handed over wholesale. What matters is never “which layer is more advanced,” but what prerequisites support delegation at that layer.

### Layer 1: Tool-Level Autonomy

This is the most mature layer today, and also the easiest to overestimate.

The model calls tools: search, browsers, the file system, code execution, APIs. Claude Code, various MCPs, browser agents, and local executors all essentially belong here. You ask it to read files, open a terminal, run scripts, or click web pages, and it truly saves a large amount of action.

But the “autonomy” at this layer is shallow. The model is using capability, not defining the problem. It is completing actions for you inside established boundaries, not deciding how those boundaries should be drawn.

Even this layer is far from “as long as there are tools, it works.”

#### Inside Tool-Level Autonomy, There Are at Least Three Very Different Cases

**1) The tool itself is mature enough, as long as the task boundary is clear**

If your goal is only:

- look at today’s headlines on a few mainstream media homepages;
- open a small number of pages;
- make a short summary;

then browser tools, search tools, and script-execution tools are often enough. These tasks share several features:

- the scope is small;
- result quality is easy to check;
- failure cost is low;
- the task boundary is relatively clear.

In that situation, handing actions to an agent is not a big problem. It is more like a reasonably reliable assistant helping you flip through a few fixed materials. You know what it looked at; omissions are easy to fill; mistakes are easy to find.

**2) The tool exists, but the object it hands you is already distorted**

These are the two key examples from Part 8A: PDF parsers and search engines.

The issue is not that tools do not exist. The issue is that they change the object itself:

- PDF parsers compress visual documents into flat text, so layout, hierarchy, and order may be lost;
- search engines do not hand you all existing content; they hand you only the part that surfaces.

This means you think you delegated an action — “help me read this PDF,” “help me search for relevant pages” — but what you actually trusted by default was that the input layer had not been contaminated.

That default is often wrong.

“There is a tool” does not mean “the conditions for delegation exist.” The tool may already have quietly rewritten the problem somewhere you cannot see. You think you delegated an action, but in reality you trusted an input pipeline you never verified.

**3) Whether the tool is good enough depends on the task objective**

This is especially obvious in your system.

“A browser tool exists” does not mean “the browser tool is enough.” “A search API is callable” does not mean “search has replaced visiting the website itself.”

If you only want an agent to visit a few fixed websites and read the news, that may indeed be just a few clicks. But if you want to systematically crawl thousands of company websites, cross subdomains, handle redirects, process PDFs, respect robots rules, control budgets, and guarantee completeness, it is no longer the same problem.

So what tool-level autonomy should really examine is not:

whether a tool exists.

It should ask:

whether this tool, for this task, under this quality requirement and this failure cost, is mature enough.

That is the real question for delegation at the tool layer.

### Layer 2: Workflow-Level Autonomy

One layer above tool-level autonomy is workflow-level autonomy.

Here the model is not merely calling a single tool. It is running multiple steps by itself inside a process that is already mature, repeatable, and bounded:

- collect inputs;
- make intermediate judgments;
- call different tools;
- combine results;
- retry or fall back under predefined error modes.

Much of what is genuinely valuable in so-called “agent workflows” lives here. As long as the process itself has already been thought through by humans, the model can indeed take on more and more execution work.

But there is a premise here that is often underestimated:

the process must first be defined.

Workflow-level autonomy is not “the model invents the process by itself.” It is “humans first grind the process into maturity, and the model executes efficiently inside it.” Processes do not fall from the sky. They grow after someone has paid the cost of failure, clarification, and boundary definition.

Without those premises, an “autonomous workflow” is just a still-growing thing misdescribed as a mature process.

#### This Layer Also Has Different Maturity Levels

**1) Mature processes that have been frozen for a long time**

Some processes have been run many times:

- what inputs look like;
- what outputs look like;
- which exceptions exist;
- how errors fall back.

All of this is already clear.

This kind of process is best suited to workflow-level autonomy. What it needs is not “define the problem,” but “execute efficiently.”

For example:

- filling weekly reports with a fixed template;
- extracting fields from a known schema;
- classifying and routing FAQs with clear boundaries;
- bulk code modifications under known interfaces.

These tasks do not win through improvisational judgment. They rely on stability, speed, and consistency.

**2) Processes whose core is stable but whose edges keep evolving**

This category is more common, and easier to misjudge.

For example, in our pipeline, many main flows have stabilized:

- start from known entry points;
- determine relevance;
- control budget and scope;
- produce logs and traceable results.

But the edges keep changing:

- new website structures;
- new PDF styles;
- new business metrics;
- new definitions of relevance;
- new downstream needs.

This kind of process can be partially delegated, but only if:

you can distinguish the stable core from the still-evolving edge.

If you cannot, “workflow-level autonomy” will misread a system whose core is mostly mature and whose edges are still growing as a system that is already fully stable.

That is exactly the illusion many wrapper-style demos are best at producing.

**3) Processes that look repetitive but are not yet mature**

This is the most dangerous category.

They look very much like processes:

- first A, then B, then C;
- done every week;
- a fixed sequence;
- they can even be demoed.

But the judgments that truly determine success —

- what relevance actually means;
- which exceptions should be absorbed into the system;
- which data-quality problems are worth stopping for;
- which failures are worth fixing and which are not;

are still moving.

If this kind of process is handed to an agent too early, the most likely outcome is not “total collapse,” but:

it appears to run, while silently drifting all the way through.

It does not throw an error. Three months later, you discover that it has been judging with last quarter’s standard, while you yourself have changed that standard twice.

This is also why lightweight wrapper solutions often mislead. They demonstrate a process that has been artificially trimmed clean, not a system that continues growing boundaries in reality. In the demo, everything looks like a pipeline. In production, you discover it is still a construction site.

### Layer 3: Operational Autonomy

The next layer up is operational autonomy.

Here the model does not merely run a fixed process. It can adapt within a known problem space:

- the website structure changes;
- a tool interface changes;
- a class of file format changes;
- one step fails and requires another route;
- the local environment is unstable and another method is needed to continue.

This layer is real, and it is the most promising zone of progress over the next few years.

But it also has boundaries. Complexity rises sharply here, because “change” is not one thing.

#### This Layer Contains at Least Three Kinds of Change

**1) Expected change — you have already prepared a response toolkit**

For example:

- certain kinds of websites often have fixed redirects;
- certain PDFs often have similar problems;
- certain error codes already have fallback strategies;
- certain page-structure changes are already within the range of experience.

This kind of change is best suited to operational autonomy.

Because the system has already prepared a toolkit for handling it.

Many places in our pipeline are essentially like this:

- budget caps;
- domain-scope rules;
- robots prechecks;
- deferred queues after failure;
- low-confidence PDF flags.

None of these was “understood by the model on its own.” You first partially structured the problem space, and only then did the operational layer have a chance to be delegated further.

**2) Change that exceeds expectation but remains within a known problem class**

For example:

- a new website structure that has not appeared before;
- a stranger navigation pattern;
- a rarer document form;
- a business field whose expression has changed.

These changes remain inside the same problem class, but old rules no longer handle them simply. This layer can be partially delegated to agents, provided that:

- the activity boundary is clear enough;
- failure can roll back;
- humans can take over quickly;
- outputs have a checking layer.

This is the most realistic landing point for the “stronger agents” many people imagine: not taking over everything directly, but bearing more disturbance inside a task class you already understand.

**3) Change starts changing the problem itself**

This is the most important kind.

The change is no longer merely:

- how the website structure changes;
- where the document location moves;
- how the tool is called;

but starts becoming:

- the definition of relevance changes;
- the success criteria change;
- “find ESG reports” becomes “find evidence aligned with a decarbonization trajectory under a specific industry standard”;
- “collect materials” becomes “judge which materials are worth using as downstream evidence.”

At this point, the change is no longer merely an operational disturbance. It begins touching the problem definition itself.

Once it reaches this point, the operational layer begins to seep into the strategic layer. That is why the third layer is the easiest to misjudge: it looks like “stronger execution,” but some of the changes inside it are no longer execution problems.

### Layer 4: Strategic Autonomy

This is the most controversial layer.

Strategic autonomy means:

- what the objective actually is;
- which trade-off matters more;
- what “good enough” means;
- which errors are worth fixing and which are not;
- when to stop and when to continue;
- when reality gives feedback, whether to change the implementation or the objective itself.

This is no longer “running the process by itself.”

This is steering.

The problem with steering is not whether you can turn the wheel. It is whether you know where the iceberg is.

And what Part 8A really argued is precisely that the problem lies here:

the information required by the strategic layer often does not exist before the system starts.

It comes from failure, feedback, and repeated collision with reality. So this layer cannot be delegated wholesale in advance. Not because the model is not smart enough, but because what is missing here is not “stronger reasoning,” but:

a problem that has not yet been explicitly formed.

#### But Even at This Layer, It Is Not “Hand Everything Over” or “Hand Nothing Over”

This point matters.

If tool-level, workflow-level, and operational autonomy ask “which actions can be handed over,” then strategic autonomy should ask:

which parts can be supported inside a controlled loop, and which cannot be handed over wholesale.

**1) The model can participate in exploration, but cannot decide**

For example:

- let the model propose possible solutions;
- help list trade-offs;
- expose hidden assumptions;
- generate candidate problem definitions;
- compare different frameworks.

These tasks can be given to the model for participation, and are often well suited to it. But its role remains exploratory support, not final decision-maker.

**2) Some work can be partially delegated inside a human-led iteration loop**

For example:

- you give an initial definition;
- the model produces a version;
- you revise it;
- the model revises again;
- you continue correcting.

This is already a form of human-machine strategic collaboration. It is not the model steering autonomously, but it is certainly not “the model is useless.”

The model is like a sparring partner; the human sets direction. The sparring partner can help you hit more balls, but will not decide whether the match should continue.

**3) The parts that truly cannot be handed over wholesale**

The parts that truly cannot be handed over wholesale remain:

- what the problem actually is;
- which dimension matters most;
- what failure means;
- whether to keep investing;
- whether to change the objective rather than the implementation.

These are not things that “will naturally happen if the model gets a bit smarter.” They come from long accumulation, responsibility, organizational context, and external consequences.

So the boundary drawn in Part 8A still holds here.

## This Framework Applies Beyond ESG Collection

If this applied only to this one pipeline, it would be a project summary rather than a more general delegation framework.

In reality, this layered way of thinking applies to many kinds of knowledge work. The difference is only:

different categories of work contain different proportions of delegable task blocks at different layers.

The table below is not meant as a complete classification. It is meant to show that this layered judgment is not limited to one pipeline, but transferable across contexts. Whether you come from research, engineering, product work, or more operations- and analysis-oriented work, the same questions can help judge which blocks can be handed over and which cannot yet be handed over.

The same category of work can span multiple layers. The real object of judgment is the task block, not the job label.

**Table 1: General Work Categories × Autonomy Layers**

| Work category | Typical task blocks | More suitable delegation layers | Parts that can be delegated earlier | Parts requiring caution | Hardest parts to delegate wholesale |
| :-- | :-- | :-- | :-- | :-- | :-- |
| Information collection | Web crawling, document collection, file archiving | Tool-level / workflow-level / partial operational | Known entry points, fixed formats, stable-structure data collection | Website-structure changes, redirects, dynamic pages, low-quality input handling | Defining “what counts as complete” and “what is worth collecting” |
| Information extraction | Extracting fields, classifying, tagging documents | Tool-level / workflow-level | Clear schemas, known fields, extraction with stable rules | Expression changes, document-type drift, low-quality OCR / PDF | Defining extraction goals and adjusting relevance standards |
| Coding | Writing functions, fixing bugs, changing tests, refactoring, integration | Tool-level / workflow-level / operational | Local implementation, code generation under known interfaces, test fixes | Cross-file modifications, complex bugs, navigation in unfamiliar codebases | Defining system boundaries, architecture trade-offs, technical-debt judgment |
| Research | Literature collection, experiment design, result organization, alternatives | Tool-level / partial workflow-level / partial strategic collaboration | Material organization, comparison tables, initial option enumeration | Evidence-weight evaluation, redirecting after experimental failure | Defining the problem, choosing the research direction, judging what is worth doing |
| Investigation | Cause analysis, anomaly localization, root-cause analysis | Operational / edge of strategic | Known failure-mode checks, log aggregation, candidate-cause lists | Cross-system anomalies, conflicting signals, hidden failures | Defining “what the real problem is” |
| Product / strategy planning | Requirement sorting, roadmaps, priorities, trade-offs | Strategic (partially collaborative) | Candidate solution generation, risk lists, solution comparison | Converging on real constraints, priority adjustment, organizational coordination | Problem definition, value judgment, responsibility |

What this table really tries to show is not “which jobs AI can do,” but:

low-level task blocks and high-level task blocks are mixed inside the same category of work.

Demos often prove only that low-level blocks can be delegated, but are misread as proof that the whole category of work can be delegated.

That is exactly where popular agent narratives most often go wrong.

## Why This Spectrum Is Not Static

Dividing autonomy into layers is not meant to declare that “upper layers are forever impossible.” It is meant to show:

the expansion of autonomy never happens all at once; it happens layer by layer.

Some layers are already becoming very practical. Some layers are still far from mature enough to trust. The gap between them cannot be crossed with one sentence like “the model got stronger.” It requires an entire set of prerequisites.

That is why the same sentence, “agents are getting stronger,” means very different things at different layers:

- at the tool layer, it means tool calls are becoming more stable;
- at the workflow layer, it means the model can run more steps inside mature processes;
- at the operational layer, it means the model can handle more variation inside known problem spaces;
- at the strategic layer, it becomes a completely different question:

can it decide what the problem is for you?

But “which layer can be delegated” is still not enough. Even within the same layer, different task blocks sit at different maturity states.

Some blocks are already stable. Some have a stable core but changing edges. Some look repetitive but are still growing boundaries. Some changes have already begun touching objectives, boundaries, and success criteria.

So when judging delegation, you need to look not only at layer, but also at maturity.

This is actually the central point of the whole essay: what determines whether something can be delegated is not an abstract “how strong is AI,” but where this task block currently sits and how mature it currently is.

**Table 2: Task-Block Maturity × Delegation Risk**

| Task-block state | Characteristics | Delegability | Typical examples | Main risk |
| :-- | :-- | :-- | :-- | :-- |
| Mature stable block | Inputs, outputs, exceptions, and fallbacks are clear | High | Fixed-template reports, fixed FAQs, code changes under stable interfaces | Risk relatively controllable |
| Stable core + evolving edge | Main flow is stable, but edge conditions keep changing | Medium | Budget crawling, ESG explorer, gradually expanding metric extraction | Easiest to misread as “fully delegable” |
| Pseudo-repetitive block | Looks repetitive, but standards are moving | Low | “Weekly” analysis where relevance and trade-offs keep changing | Easy silent drift |
| Disturbance block inside a known problem class | Change exceeds presets but remains in the same task class | Medium-low | New website structures, new document formats, new error types | Requires rollback and human takeover mechanisms |
| Problem-redefinition block | Change already touches objective, boundary, and success criteria | Very low | From “collect reports” to “judge evidence validity” | Cannot be delegated wholesale |
| Strategic collaboration block | The model can participate but cannot decide | Medium, only inside a human-led loop | Solution comparison, candidate framing, trade-off lists | Easily mistaken for something fully delegable |
| Strategic steering block | Requires external responsibility, long experience, organizational context | Extremely low | Objective definition, priority ranking, stopping conditions, resource-allocation trade-offs | Cannot be handed over wholesale |

This table supplements the same judgment:

real delegation decisions should not be made at the “occupation” level, nor only at the “layer” level.

They must land on this question: how mature is this task block right now?

## Why the “Full Autonomy” Narrative Keeps Winning

If autonomy is actually expanding by layer, by block, and by condition, why does the public narrative keep talking about “full autonomy”?

Because “full autonomy” sells better.

Product launches, roadshows, speeches, interviews, and VC decks all prefer one simple sentence:

give it tools and let it handle things by itself.

That sentence is extremely effective. It satisfies three imaginations at once:

- capability imagination: models are getting stronger;
- product imagination: fewer humans makes it feel like a “real product”;
- capital imagination: no humans = scalability.

It also fits today’s communication environment naturally. Social media rewards phrases that can be said in one sentence and immediately form an impression. “Full autonomy” is short, loud, and sounds like the future has already arrived. “Layered delegation” and “delegation according to maturity”? Those require the reader to pause and think for a few seconds — exactly what recommendation algorithms are least built to reward.

So “full autonomy” is essentially a high-transmission, low-resolution expression. It transmits efficiently; it judges poorly. It is exactly the kind of phrase best suited to a cover title: few words, strong force, feels already real. As for the details — details are usually left to be filled in after something goes wrong.

“Differentiated autonomy,” “layered delegation,” “delegation according to maturity”? Not sexy. They are true, but not stimulating. They do not sound like revolution. They sound like engineering. And reality is exactly like this:

revolutionary capabilities often need unsexy engineering structures before they can become genuinely usable products.

## So the Real Delegation Question Is: Which Layer, Which Block?

Once autonomy is seen as a spectrum, the question is no longer:

- should agents be given more capability;
- should models become more agent-like;
- should we embrace the future.

The real question becomes:

which layer can be delegated, which block can be delegated, to what degree, and who catches the failure.

This is also why the same sentence, “agents are getting stronger,” leads different people to completely different conclusions.

Some people hear:

- then they will soon replace people wholesale.

But the more accurate understanding is:

- low-level autonomy is getting stronger;
- mid-level autonomy is expanding;
- high-level autonomy is still constrained by problem formation, environment quality, evaluation ability, and system guardrails.

This is not a “middle position.” It is a higher-resolution position.

## How Should You Decide: Hand It Over or Not?

If the preceding judgment is compressed into a more usable framework, the questions you should really ask are these five:

**1. Is this task block itself mature?**

Has it run for a long time with clear boundaries and success criteria? Or does it only look repetitive while actually still evolving?

**2. Are the tools this task block depends on mature?**

Do the tools merely exist, or are they reliable enough? Is the input lossless? Or is the tool itself changing the object, hiding information, and creating silent bias?

**3. Is the change inside this block expected?**

Do you have a prepared response toolkit? Or does every change force you to understand the problem again?

**4. If it is wrong, can you detect and roll back quickly?**

Will it fail loudly? Or will it “look like it is working” while silently drifting for months?

**5. Is this block executing the problem, or changing the problem?**

If it is only executing, it is more likely delegable. If it starts defining objectives, changing relevance definitions, or deciding trade-offs, it is already close to the strategic layer.

## Where the Pipeline Sits on This Spectrum

This pipeline itself is a very concrete case of “differentiated autonomy.”

It does not oppose autonomy. It places autonomy in the right layers.

In this pipeline:

- **The strategic layer** is steered by humans. It decides what the problem is, what counts as relevant, which failures are worth fixing, and where the system should evolve.
- **The judgment layer** is handled by LLMs. They make semantic classifications in fuzzy contexts: whether this URL is ESG-related, whether this subdomain is worth entering, which links in a batch are more likely to be relevant.
- **The control layer** is handled by deterministic code. Budgets, retries, rate limits, delayed PDF handling, `robots.txt`, domain-scope rules, logs, and auditability.

This structure cannot be captured by the vague phrase “human-machine collaboration.” More precisely, it is:

- expert humans: strategic direction, requirement evolution, full evaluation
- LLMs / agents: semantic judgment, operational execution, adaptation inside known classes
- code / systems: precision, cost control, compliance, traceability

Remove any layer and the structure fails:

- remove the expert, and the problem drifts — you run this quarter’s data with last quarter’s objective;
- remove the model, and scale and semantic processing do not rise — many judgments retreat back to manual labor and brittle rules;
- remove the deterministic system, and cost, reliability, and compliance collapse together — you run into the bill from Part 4 again.

This is not compromise. It is a layered autonomy design.

And this is exactly what the “full autonomy” narrative most easily skips: it rewrites a precise three-layer collaboration structure as “the model handles it by itself.”

## The Future That Actually Emerges: Not Full Autonomy, but Differentiated Autonomy

If the preceding argument is compressed into one sentence, what this essay really says is:

The future will certainly not have no autonomy; but it also will not be “one large model takes over everything.” The future is more likely to be differentiated autonomy.

What does that mean?

It means:

- the model’s share at the tool, workflow, and operational layers will continue to expand;
- the human role at the strategic layer will not disappear, but become more concentrated and more critical;
- deterministic systems will not leave the stage, but increasingly look like infrastructure around the model.

Capability is rising. The scope of autonomy is expanding. But not every layer expands together. And not every layer is handed over together.

That is why “full autonomy” is both attractive and dangerous: it turns a layered evolutionary process into a myth of whole replacement.

Reality will not move that way. Real systems always grow in layers. And truly effective autonomy is always placed in layers.

Next: [Part 9 — The Other Extreme.](/blog/other-extreme-en/)

This is Part 8B of the series. [Start from the beginning.](/blog/why-this-series-exists-en/)

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
| **08B — The Autonomy Spectrum** | **You are here** |
| 09 — The Other Extreme | When skepticism becomes paralysis |
| 10 — Two Rooms | Demo enthusiasts vs. domain skeptics |
| 11 — The Evidence | The pipeline as evidence |
| Bonus — The Counterargument | AI argues against the entire series |
| Bonus — Standing in the Middle | The thought that arrives in the middle of the night |
