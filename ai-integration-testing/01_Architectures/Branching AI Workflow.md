---
tags: [ai-integration, workflow, routing]
type: architecture
complexity: intermediate
---

# Branching AI Workflow

## Purpose

Route an input through one of several predetermined paths.

```text
Input → router
         ├─ path A
         ├─ path B
         └─ fallback
```

Routing may be controlled by rules, a classifier, or a structured LLM response.

## What to test

- Every branch
- Positive and negative routing cases
- Boundary and ambiguous cases
- Fallback path
- Invalid route output
- Branch convergence
- State consistency

## Metrics

- Routing accuracy
- False-positive route rate
- False-negative route rate
- Fallback frequency
- Per-route latency and quality

## Main failure modes

- Wrong branch
- Missing fallback
- Unreachable branch
- Conflicting route criteria
- Model invents an unsupported route
- Retry loops

## Related notes

- [[Multi-Call Pipeline]]
- [[Graph-Based Workflows]]
- [[LangGraph]]

## Related audit prompts

- [[06_Prompts/Branching Workflow Testing Audit|Branching Workflow Testing Audit]]
