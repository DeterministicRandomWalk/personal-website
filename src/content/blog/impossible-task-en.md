---
title: 'Part 1: The Portfolio Manager’s Impossible Task'
description: 'Why “find all ESG disclosure” sounds simple until it becomes an engineering problem.'
pubDate: 'Jun 04 2026'
heroImage: '../../assets/series-01-impossible-task-illustration.png'
lang: 'en'
---

> Series: We built a pipeline with tens of thousands of lines of code. Why agents could not do it.

[Previous: Part 0.](/blog/why-this-series-exists-en/)  
[阅读中文版。](/blog/impossible-task-zh/)

Every quarter, one investment team at an investment institution has to do something that sounds simple: evaluate the ESG performance of the companies in a fund portfolio.

For each company, the portfolio manager has to read disclosure documents and map them against the fund’s internal assessment framework. Does the company report scope 3 emissions? Does it have a board-level sustainability committee? What do its supply-chain labor practices look like?

Find the right document. Read it. Score it. Move to the next company.

It sounds manageable until you see what “the right document” actually means.

## Not Just the Sustainability Report

She needs climate transition plans, climate-related disclosures, biodiversity statements, modern slavery statements, conflict minerals reports, tax transparency policies, water stewardship commitments, responsible AI policies, data privacy impact assessments, community investment reports, political lobbying disclosures, and executive compensation policies linked to ESG targets.

And that is only the generic list. Industry-specific disclosure adds another layer: tailings dam safety for mining companies, fleet emissions targets for logistics companies, animal welfare standards for food producers.

Different reporting frameworks mean companies report different things in different formats. No two companies organize their disclosures in quite the same way.

She is good at this. But the portfolio holds thousands of companies.

For each one, she visits the corporate website, opens dozens of tabs, follows links that look promising, saves PDFs, and still misses pages buried three clicks deep. Some companies put everything in one place. Others scatter disclosures across investor-relations pages, sustainability microsites, regional subdomains, and third-party reporting platforms.

Each company takes hours. And she knows she is still missing information.

## The Consistency Problem

Then the real problem appears: not just scale, but consistency.

Her colleagues evaluate the same company and arrive at different scores. Not because anyone is doing the job badly, but because they find different files on the same website. One person finds a modern slavery statement hidden under “Legal”; another does not. They interpret the same framework standard differently. For every analyst reading the same written guidance, “sufficient disclosure” means something slightly different.

And, honestly, one person is doing the review on a Friday afternoon after a week of back-to-back meetings. Their condition is not ideal.

The assessment reflects not only the company’s ESG performance, but also who did the work, what they happened to find, and what state they were in that day.

Multiply that by 5,000 companies. Inconsistency compounds into noise and erodes the meaning of the entire evaluation. At that scale, thorough and consistent? Impossible.

## Meanwhile, Technology Headlines Tell Another Story

Open any technology headline and you will read that AI agents are about to replace most software engineers. Give a large language model some tools: a browser, a terminal, a code editor. Connect them with protocols and plugins. The agent can handle everything by itself.

Popular open-source agent frameworks and multi-agent systems tend to make the same promise: agents are the new software. So people ask: if large language models can call tools, read documents, and write code on demand, why write code at all?

There are several layers to this narrative. At one end: “An LLM application is just documents fed into an API call. You do not need real engineering.” At the other end: “Browser automation plus tool calling has solved web collection. Agents are the new pipeline.”

It sounds transformative. The demos look good. And this is exactly the sort of claim that changes management decisions.

At that point, it is no longer just a technical debate. It becomes a business question. A manager sees the demo, reads the headlines, and in the same week may receive two kinds of sales calls.

The first comes from data vendors: “We already have all the ESG data: documents, disclosures, reports, all structured and scored. Why build infrastructure? Just buy the data.”

The second comes from analytics platforms: “We provide AI analysis on top of the data. Connect to the platform, get ESG insights, no custom engineering required.”

Two pitches, two levels of the same question. The first challenges data collection. The second challenges everything built on top of the data.

The answer to both questions hides in the details that demos do not show and vendors do not emphasize. The observations in this series come from practice: a production pipeline used for institutional investment decisions across thousands of companies. It uses AI where AI is genuinely strong, and deterministic engineering everywhere else.

Not “no AI.” Not “all AI.”

The right tool at each layer, and how we learned which tool belonged where.

## She Tried the Obvious Thing First

The portfolio manager saw the same wave from her side. Vendors pitched AI-powered ESG platforms, automated analysis, and polished slides showing structured output generated from unstructured documents. The headlines reached her inbox too: agents, assistants, AI that reads reports for you.

Complex tool configuration was too much friction. Even if it worked, how would the result be traced?

But a chatbot she could open in a browser or desktop app? She could try that immediately.

She opened an AI assistant, manually uploaded a sustainability report, and asked it to evaluate the company against the framework.

It was impressive. The large language model read the document, identified relevant disclosures, mapped them to standards, and produced structured output. For one company and one file, it felt like magic.

She tried web search: “Find the latest climate transition plan for a large energy company.” The chatbot searched, found, and summarized. Impressive.

Then she tried to actually use it.

## Six Problems, Six Weeks

### 1. Scale Breaks the Conversation Pattern

Each company needs its own conversation. The assessment framework has dozens of questions. The output becomes long: clarification, follow-up, re-prompting. For one company, this is a productive hour. For hundreds, it becomes a different kind of manual work: managing conversations instead of managing tabs.

### 2. Output Management Becomes Its Own Job

Over time, chatbots get better: models improve, interfaces become easier, file handling expands. But after the model finishes its part, there is still a lot of work: copying results into spreadsheets, reconciling formats, cross-checking across companies.

AI handles reasoning; humans handle administration. The bottleneck moves, but it does not disappear. To be fair, this administrative work is shrinking. It just never seems to vanish completely.

### 3. Model Choice Matters

Different leading models give different assessments for the same document. Not wildly different, but different enough that switching models during a portfolio review introduces a new source of inconsistency, exactly the problem she is trying to remove. Sometimes performance also seems to degrade suddenly, with no obvious explanation.

### 4. Web Search Retrieves Incomplete Data

The chatbot finds the main sustainability report but misses the modern slavery statement, the climate disclosure hidden in investor relations, and biodiversity commitments on a regional subdomain. It retrieves what is easy to find, not what is complete.

She is back where she started: important documents are missing, just behind a prettier interface.

### 5. Hallucinated Content

A company is said to “commit to net zero by 2030,” but the actual target is 2050. A policy that does not exist is cited confidently. Every output needs verification, which means reading the source documents anyway.

For professional assessments that drive investment decisions, “mostly right” is not a standard. This is not a perfect argument, of course. Humans hallucinate too, just in different ways.

### 6. Transparency and Auditability

The fund’s investment committee asks: how was this assessment produced?

She cannot answer: “I asked a chatbot.”

Institutional investment decisions require an audit trail: which documents were reviewed, how each criterion was scored, and what evidence supports each judgment. A conversation in a chatbot does not naturally produce any of that. “AI did magic” is not a compliance answer.

## The Conclusion from Using Chatbots

They are genuinely useful for exploration, quick lookup, and drafting. They are also getting better all the time.

Just not for investment decisions.

As a systematic assessment tool at portfolio scale, the chatbot fails on the dimensions that matter:

- Completeness
- Consistency
- Auditability
- Reliability

The portfolio manager realizes this is not a prompt problem. It is an engineering problem.

She brings the requirement to the development team: can we build a pipeline that does this correctly?

Next: Part 2 — From “Just Throw It at AI” to 7,400 Lines of Code.

---

Chinese original: [第1篇：投资组合经理的不可能任务](/blog/impossible-task-zh/).

Originally published externally: [source article](https://mp.weixin.qq.com/s/gXuULJQHxcrBQxLdmCtlbg).
