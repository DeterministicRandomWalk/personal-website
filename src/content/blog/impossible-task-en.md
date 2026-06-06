---
title: 'Part 1: The Impossible Disclosure Task'
description: 'Why “find all relevant corporate disclosure” sounds simple until it becomes an engineering problem.'
pubDate: 'Jun 04 2026'
heroImage: '../../assets/series-01-impossible-task-illustration.png'
lang: 'en'
---

> Series: What production AI needs beyond an impressive model.

[Previous: Part 0.](/blog/why-this-series-exists-en/)  
[阅读中文版。](/blog/impossible-task-zh/)

Imagine a recurring investment workflow that sounds simple: evaluate a large set of companies using their public sustainability-related disclosures.

For each company, an analyst has to find the relevant documents and map them against an assessment framework. Does the company report indirect emissions? Does it describe board-level oversight? What do its supply-chain labor practices look like?

Find the right document. Read it. Score it. Move to the next company.

It sounds manageable until you see what “the right document” actually means.

## Not Just the Sustainability Report

She needs climate transition plans, climate-related disclosures, biodiversity statements, modern slavery statements, conflict minerals reports, tax transparency policies, water stewardship commitments, responsible AI policies, data privacy impact assessments, community investment reports, political lobbying disclosures, and executive compensation policies linked to ESG targets.

And that is only the generic list. Industry-specific disclosure adds another layer: tailings dam safety for mining companies, fleet emissions targets for logistics companies, animal welfare standards for food producers.

Different reporting frameworks mean companies report different things in different formats. No two companies organize their disclosures in quite the same way.

The method works for one company. The portfolio-scale version contains thousands.

For each one, the analyst visits the corporate website, opens dozens of tabs, follows links that look promising, saves PDFs, and still misses pages buried three clicks deep. Some companies put everything in one place. Others scatter disclosures across investor-relations pages, sustainability microsites, regional subdomains, and third-party reporting platforms.

Each company can take hours, and the analyst still knows information may be missing.

## The Consistency Problem

Then the real problem appears: not just scale, but consistency.

Two analysts can evaluate the same company and arrive at different scores. Not because either is careless, but because they find different files on the same website and interpret the same written guidance slightly differently.

The assessment reflects not only the company’s ESG performance, but also who did the work, what they happened to find, and what state they were in that day.

Multiply that across a large portfolio. Inconsistency compounds into noise and erodes the meaning of the entire evaluation. At that scale, being both thorough and consistent becomes nearly impossible.

## Meanwhile, Technology Headlines Tell Another Story

Open any technology headline and you will read that AI agents are about to replace most software engineers. Give a large language model some tools: a browser, a terminal, a code editor. Connect them with protocols and plugins. The agent can handle everything by itself.

Popular open-source agent frameworks and multi-agent systems tend to make the same promise: agents are the new software. So people ask: if large language models can call tools, read documents, and write code on demand, why write code at all?

There are several layers to this narrative. At one end: “An LLM application is just documents fed into an API call. You do not need real engineering.” At the other end: “Browser automation plus tool calling has solved web collection. Agents are the new pipeline.”

It sounds transformative. The demos look good. And this is exactly the sort of claim that changes management decisions.

At that point, it is no longer just a technical debate. It becomes a business question. A manager sees the demo, reads the headlines, and hears two common proposals.

The first comes from data vendors: “We already have all the ESG data: documents, disclosures, reports, all structured and scored. Why build infrastructure? Just buy the data.”

The second comes from analytics platforms: “We provide AI analysis on top of the data. Connect to the platform, get ESG insights, no custom engineering required.”

Two pitches, two levels of the same question. The first challenges data collection. The second challenges everything built on top of the data.

The answer to both questions hides in the details that demos do not show and vendors do not emphasize. The observations in this series come from building a production pipeline for a large investment workflow. It uses AI where AI is genuinely strong, and deterministic engineering everywhere else.

Not “no AI.” Not “all AI.”

The right tool at each layer, and how we learned which tool belonged where.

## She Tried the Obvious Thing First

The people doing the assessment saw the same wave from their side: automated analysis, polished demonstrations, and assistants that promise to read reports for you.

Complex tool configuration was too much friction. Even if it worked, how would the result be traced?

But a chatbot available in a browser or desktop app could be tested immediately.

An analyst uploaded a sustainability report and asked an AI assistant to evaluate the company against the framework.

It was impressive. The large language model read the document, identified relevant disclosures, mapped them to standards, and produced structured output. For one company and one file, it felt like magic.

The analyst tried web search: “Find the latest climate transition plan for a large energy company.” The chatbot searched, found, and summarized. Impressive.

Then came repeated use.

## Six Problems

### 1. Scale Breaks the Conversation Pattern

Each company needs its own conversation. The assessment framework has dozens of questions. The output becomes long: clarification, follow-up, re-prompting. For one company, this is a productive hour. For hundreds, it becomes a different kind of manual work: managing conversations instead of managing tabs.

### 2. Output Management Becomes Its Own Job

Over time, chatbots get better: models improve, interfaces become easier, file handling expands. But after the model finishes its part, there is still a lot of work: copying results into spreadsheets, reconciling formats, cross-checking across companies.

AI handles reasoning; humans handle administration. The bottleneck moves, but it does not disappear. To be fair, this administrative work is shrinking. It just never seems to vanish completely.

### 3. Model Choice Matters

Different leading models give different assessments for the same document. Not wildly different, but different enough that switching models during a portfolio review introduces a new source of inconsistency, exactly the problem the workflow is trying to remove. Sometimes performance also seems to degrade suddenly, with no obvious explanation.

### 4. Web Search Retrieves Incomplete Data

The chatbot finds the main sustainability report but misses the modern slavery statement, the climate disclosure hidden in investor relations, and biodiversity commitments on a regional subdomain. It retrieves what is easy to find, not what is complete.

The workflow is back where it started: important documents are missing, just behind a prettier interface.

### 5. Hallucinated Content

A company is said to “commit to net zero by 2030,” but the actual target is 2050. A policy that does not exist is cited confidently. Every output needs verification, which means reading the source documents anyway.

For professional assessments that drive investment decisions, “mostly right” is not a standard. This is not a perfect argument, of course. Humans hallucinate too, just in different ways.

### 6. Transparency and Auditability

The decision maker asks: how was this assessment produced?

“I asked a chatbot” is not an adequate answer.

Institutional investment decisions require an audit trail: which documents were reviewed, how each criterion was scored, and what evidence supports each judgment. A conversation in a chatbot does not naturally produce any of that. “AI did magic” is not a compliance answer.

## The Conclusion from Using Chatbots

They are genuinely useful for exploration, quick lookup, and drafting. They are also getting better all the time.

Just not for investment decisions.

As a systematic assessment tool at portfolio scale, the chatbot fails on the dimensions that matter:

- Completeness
- Consistency
- Auditability
- Reliability

The conclusion is that this is not a prompt problem. It is an engineering problem.

The requirement becomes: can a pipeline do this systematically and leave an auditable trail?

Next: [Part 2 — Why One Classifier Became Seven Layers](/blog/seven-layers-en/).

---

Chinese version: [read Part 1 in Chinese](/blog/impossible-task-zh/).
