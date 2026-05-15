# Learning Extraction Prompts

> [!info] Purpose
> Use these prompts to turn a lab into durable Obsidian knowledge.
> These prompts are not for improving code. They are for understanding what the lab taught.

---

## Master Vault Learning Extraction Prompt

```text
Extract durable learning from new Ironhack course material and integrate it into my Obsidian vault.

Sources may include:
- mandatory labs
- extra labs
- team projects
- `ac-bootcamp-public` notebooks or notes
- lesson HTML exports
- source folders with `lab_source`
- supporting files such as READMEs, notebooks, scripts, workflow exports, screenshots, examples, and submitted code

My vault goals:
1. Fast discovery: I want to quickly find topics, techniques, and where I practiced them.
2. Progression: I want to understand how the course evolves across weeks, projects, and engineering maturity.
3. Reuse: I want reverse prompts, patterns, and checklists that help me apply the learning later.

Process:
1. Inspect the source material before writing.
2. Decide the source type: lab, extra lab, project, public notebook, lesson, or supporting reference.
3. Extract concepts, techniques, architecture, reusable patterns, and important tradeoffs.
4. Separate what was provided from what I actually practiced when the source is a lab or project.
5. Ignore low-value details such as UI polish tasks, screenshots as proof, file hygiene instructions, or generic setup unless they teach a reusable concept.
6. Capture extras, bonus challenges, and extension activities only when they introduce real AI/engineering concepts.
7. Map each concept to existing vault categories where possible.
8. Create a new category only when existing categories would hide an important recurring theme.

Current vault categories:
- `Foundations`: Python, data structures, pandas, JSON, pipeline basics
- `ML`: classical ML, neural networks, model evaluation
- `APIs`: OpenAI/API usage, reliability, multi-provider patterns, cost tracking
- `Prompting`: prompt techniques, dynamic prompting, context injection
- `RAG`: chunking, embeddings, retrieval, reranking, grounded answers
- `Speech`: STT, TTS, audio chunking, timestamps, evaluation
- `Frameworks`: LangChain, LangGraph, MCP implementation details
- `Agentic`: agent skills, context engineering, reflection, guardrails, skill routing, agent behavior design
- `n8n`: n8n workflows, nodes, JSON item flow, app automation, scheduling, error workflows
- `Engineering`: code quality, refactoring, tests, validation, modularity, repository hygiene
- `Labs`: practical lab and project notes only
- `Prompt Library`: reusable reverse prompts and audit prompts

Integration rules:
- If the source is a lab, extra lab, or project, create or update a note under `Labs/`.
- If the source is a lesson or conceptual reading, create or update a topic note in the best category, not `Labs/`.
- If the source introduces a reusable review or improvement workflow, update `Prompt Library/`.
- If the source adds a new concept or a new applied context, update `01 Shared Concept Index.md`.
- If the source changes the course evolution, update `03 Weekly Progression Rubric.md`.
- If the source changes navigation or categories, update `00 Course Map.md`.
- If the source is a new lab/project, update `02 Lab Index.md`.
- Do not duplicate concept rows if an existing row already covers the idea well.
- Keep topic notes practical and study-friendly; do not paste huge code blocks.
- Prefer concise examples or pseudocode over long copied code.

For labs/projects, use this structure:

# Lab or Project Name

**Source folder**
- `folder_name`

**Main files**
- `file_1`
- `file_2`

**Lab type**
- guided / provided-code / template-heavy / team project / open-ended
- Main value: ...

## What This Lab Teaches

## Techniques Practiced

## Important Architecture

## Important Code Patterns

## What Was Provided

## What I Practiced

## Links to Topic Notes

## What To Reuse Later

## Improvement Ideas

## Key Takeaway

For lessons/conceptual sources, use a topic-note structure:

# Topic Name

**Source**
- `source_path_or_reference`

**Related labs**
- `lab_or_folder_name`

## Main Techniques

## Core Idea

## Important Patterns

## How This Connects To The Course

## Practical Heuristics

## Links To Related Notes

## Key Idea

Output:
1. List the files you inspected.
2. State the source type and where it belongs in the vault.
3. State the concepts worth extracting and the concepts intentionally ignored.
4. Propose the vault edits.
5. If asked to apply changes, edit the vault and then verify wikilinks.
```

---

## Lab Learning Summary

```text
Analyze this bootcamp lab and summarize what I should learn from it.

Context:
This may be a guided lab, a provided-code lab, a template-heavy lab, or a team project.
Do not assume I wrote every line of code.

Return:
1. What the lab teaches
2. Whether it is guided/provided/template-heavy/open-ended/team project
3. Main pipeline or workflow
4. Key techniques practiced
5. Important code patterns
6. What was likely provided vs what I practiced
7. Links to related topic notes
8. What to reuse later
9. What is not important to memorize
10. A short key takeaway

Rules:
- Do not improve the code.
- Focus on learning extraction.
- Keep the summary useful for Obsidian.
```

---

## Technique Extraction Prompt

```text
Extract all technical concepts and techniques from this lab.

Group them by category:
- Python/data handling
- Prompting
- API/LLM integration
- Structured output/validation
- Engineering quality
- RAG/retrieval
- LangChain/agents/tools
- Speech/audio
- UI/app workflow
- Testing/evaluation

For each concept, return:
- concept name
- where it appears
- short explanation
- why it matters
- related Obsidian topic note

Rules:
- Do not rewrite code.
- Do not include concepts that are not actually present.
```

---

## Provided Code vs My Learning Prompt

```text
Analyze this lab and separate what was provided from what I should learn.

Return:
1. Code or structure that appears provided/template-heavy
2. Parts where the student likely had to fill in logic
3. Concepts I should understand even if code was provided
4. Concepts I should be able to reproduce myself
5. Concepts I only need to recognize for now
6. How this lab raises my engineering or AI skill level

Rules:
- Be realistic for a bootcamp lab.
- Do not overstate ownership of provided code.
- Focus on learning value.
```

---

## Reusable Patterns Extraction

```text
Review this lab and extract reusable patterns for future projects.

Look for:
- helper functions worth reusing
- project structure patterns
- prompt patterns
- API wrapper patterns
- validation patterns
- error handling patterns
- testing patterns
- UI callback patterns
- RAG/chunking patterns
- LangChain agent/tool patterns

Return:
1. Reusable patterns
2. Example snippet or pseudocode
3. When to reuse each pattern
4. When not to reuse it
5. Related topic note links

Rules:
- Do not edit code.
- Prefer patterns that are simple and practical.
```

---

## Obsidian Lab Note Generator

```text
Create an Obsidian lab note for this lab.

Use this structure:

# Lab Name

**Source folder**
- `folder_name`

**Main files**
- `file_1`
- `file_2`

**Lab type**
- guided / provided-code / template-heavy / team project / open-ended
- Main value: ...

## What This Lab Teaches

## Techniques Practiced

## Important Architecture

## Important Code Patterns

## What Was Provided

## What I Practiced

## Links to Topic Notes

## What To Reuse Later

## Improvement Ideas

## Key Takeaway

Rules:
- Do not mix this with topic notes.
- Keep the note practical and study-friendly.
- Mention when code was mostly provided.
- Include examples, but do not paste huge code blocks.
```

---

## Weekly Progression Extraction

```text
Analyze the labs and notebooks from this week.

Return:
1. What I was expected to know before the week
2. New concepts introduced this week
3. New engineering skills introduced this week
4. What I should be able to build after this week
5. What an engineer's output should look like at this stage
6. How this week raises the bar from the previous week
7. Self-assessment questions
8. Concepts that connect to previous weeks
9. Concepts that are likely to matter in future weeks

Rules:
- Do not include future course content.
- Do not focus on team-project polish.
- Focus on learning progression.
```

---

## Shared Concept Index Update Prompt

```text
Given this new lab note and the existing topic notes, update the shared concept index.

For each concept in the lab, identify:
- concept name
- topic note link
- official notebook/source if known
- lab/project source
- short description of what it covers

Rules:
- Do not duplicate concepts if an existing row already covers them.
- Add new rows only when the concept is genuinely new or appears in a new applied context.
- Keep the index useful for answering: "Where did I learn this?"
```
