---
tags: [langsmith, observability, evaluation]
type: framework
status: active
---

# LangSmith

## Role

LangSmith supports tracing, experiment comparison, evaluation datasets, feedback, and production monitoring for LLM applications.

## Use it for

- Inspecting model and tool calls
- Understanding complete trajectories
- Recording latency, tokens, and errors
- Running repeatable evaluations
- Comparing prompt, model, or tool versions
- Turning failures into regression cases

## Trace versus evaluation

```text
Trace → explains what happened in one run.
Evaluation → measures whether behavior is acceptable across examples.
Monitoring → detects production changes over time.
```

## Recommended workflow

1. Enable tracing.
2. Inspect representative runs.
3. Build a dataset from important cases.
4. Add deterministic evaluators.
5. Add semantic evaluators where necessary.
6. establish a baseline.
7. Compare changes.
8. monitor production failures.

## Related notes

- [[Tracing and Observability]]
- [[Evaluation Datasets]]
- [[AI System Testing - MOC]]

## Related audit prompts

- [[06_Prompts/AI Observability and LangSmith Testing Audit|AI Observability and LangSmith Testing Audit]]
