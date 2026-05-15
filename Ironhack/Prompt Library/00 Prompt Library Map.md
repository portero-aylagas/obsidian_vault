# Prompt Library Map

> [!info] Purpose
> This folder stores reusable coding-agent prompts for reviewing projects, improving AI systems, preparing submissions, and extracting learning from labs.

## Prompt Families

- [[Engineering Quality Prompts]]
- [[AI System Quality Prompts]]
- [[Workflow Quality Prompts]]
- [[Submission Review Prompts]]
- [[Learning Extraction Prompts]]

## When To Use Each Family

### Engineering Quality

Use when the goal is:

```text
Make the project cleaner, safer, more maintainable, and more testable.
```

Best for:
- Python projects
- UI apps
- API projects
- code before refactoring
- project quality reviews

### AI System Quality

Use when the goal is:

```text
Check whether the AI-specific design is good.
```

Best for:
- prompt-heavy apps
- RAG projects
- LangChain agents
- agent skills
- speech pipelines
- structured output workflows
- LLM/API integrations

### Submission Review

Use when the goal is:

```text
Check whether the project is ready to submit, demo, or explain.
```

Best for:
- final presentation readiness
- teacher/stakeholder review
- demo risk review

### Workflow Quality

Use when the goal is:

```text
Review orchestrated AI workflows and app automations.
```

Best for:
- LangGraph workflows
- MCP integrations
- n8n automations
- guardrails and human approval
- workflow submission evidence

### Learning Extraction

Use when the goal is:

```text
Turn a lab into Obsidian knowledge.
```

Best for:
- extracting from multiple source types at once
- after completing a lab
- after adding lesson HTML or public notebooks
- weekly review
- building lab notes
- connecting labs to topic notes

## Recommended Workflows

### For a project

```text
Engineering Quality
-> AI System Quality
-> Workflow Quality if the project uses LangGraph, MCP, n8n, or guardrails
-> Submission Review
-> Apply one safe patch
-> Re-audit
```

### For a lab

```text
Learning Extraction
-> AI System Quality if the lab is AI-heavy
-> Update topic/lab notes
```

### For weekly review

```text
Learning Extraction
-> Shared Concept Index
-> Weekly Progression Rubric
```
