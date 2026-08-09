---
tags: [ai-integration, architecture]
type: concept
status: active
---

# Architecture Classification

## Primary question

> Who decides what happens next?

| Controller | Architecture |
|---|---|
| Application code | deterministic workflow |
| Model | agent |
| Code and model | hybrid workflow |

## Secondary dimensions

Classify a system by:

1. **Number of model calls** — one, fixed multiple, or dynamic.
2. **Control flow** — linear, branching, cyclic, or model-directed.
3. **External knowledge** — none, fixed context, retrieval, or tools.
4. **State** — stateless, conversational, persistent, or shared.
5. **Side effects** — read-only, write operations, or irreversible actions.
6. **Human control** — none, review, approval, or intervention.

## Complexity ladder

| Level | Pattern | Main new concern |
|---:|---|---|
| 1 | [[Single LLM Call]] | output quality |
| 2 | [[Multi-Call Pipeline]] | error propagation |
| 3 | [[Branching AI Workflow]] | routing |
| 4 | [[Tool-Using Deterministic Workflow]] | external systems |
| 5 | [[RAG Systems]] | retrieval quality |
| 6 | [[Conversation and Memory]] | state correctness |
| 7 | [[Graph-Based Workflows]] | paths and persistence |
| 8 | [[AI Agents]] | dynamic trajectory |
| 9 | [[Agentic RAG]] | retrieval decisions |
| 10 | [[Multi-Agent Systems]] | coordination |
| 11 | [[Human-in-the-Loop Systems]] | approval and recovery |

## Design preference

Use the least autonomous architecture that solves the problem.

```text
Known sequence → deterministic pipeline
Known branches → workflow or graph
Unknown tool choice → agent
High-risk action → human approval
```

## Related notes

- [[AI Integration Foundations]]
- [[LangChain]]
- [[LangGraph]]

## Related audit prompts

- [[06_Prompts/AI Architecture vs Testing Complexity Audit|AI Architecture vs Testing Complexity Audit]]
