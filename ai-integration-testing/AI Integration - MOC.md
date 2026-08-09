---
tags: [ai-integration, moc]
type: map-of-content
status: active
---

# AI Integration — Map of Content

This wiki organizes AI-enabled software by **who controls execution**, **where nondeterminism enters**, and **which additional failure modes each architecture introduces**.

## Core progression

```text
One LLM call
→ Multiple fixed calls
→ Branching workflows
→ Tools controlled by code
→ Retrieval and RAG
→ Conversation and state
→ Graph workflows
→ Model-controlled tool selection
→ Agents
→ Agentic RAG
→ Multi-agent systems
→ Human-controlled production systems
```

## Start here

1. [[00_Foundations/AI Integration Foundations]]
2. [[00_Foundations/Architecture Classification]]
3. [[03_Quality/AI System Testing - MOC]]
4. [[04_Operations/Production Readiness]]

## Architecture notes

- [[01_Architectures/Single LLM Call]]
- [[01_Architectures/Multi-Call Pipeline]]
- [[01_Architectures/Branching AI Workflow]]
- [[01_Architectures/Tool-Using Deterministic Workflow]]
- [[01_Architectures/RAG Systems]]
- [[01_Architectures/Conversation and Memory]]
- [[01_Architectures/Graph-Based Workflows]]
- [[01_Architectures/AI Agents]]
- [[01_Architectures/Agentic RAG]]
- [[01_Architectures/Multi-Agent Systems]]
- [[01_Architectures/Human-in-the-Loop Systems]]

## Framework notes

- [[02_Frameworks/LangChain]]
- [[02_Frameworks/LangGraph]]
- [[02_Frameworks/LangSmith]]

## Quality and operations

- [[03_Quality/AI System Testing - MOC]]
- [[03_Quality/Evaluation Datasets]]
- [[03_Quality/Tracing and Observability]]
- [[03_Quality/Security Testing]]
- [[04_Operations/Production Readiness]]
- [[04_Operations/Failure Analysis]]

## Prompt library

- [[Prompt Library]]

## Templates

- [[05_Templates/Architecture Note Template]]
- [[05_Templates/Test Plan Template]]
- [[05_Templates/Evaluation Case Template]]

## Central principle

> [!important]
> The library does not determine the architecture. The execution model does.
>
> - **Code controls the next step** → deterministic workflow.
> - **The model controls the next step** → agent.
> - **Control is shared** → hybrid system.
