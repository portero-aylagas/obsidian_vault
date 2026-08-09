---
tags: [debugging, failure-analysis]
type: practice
---

# Failure Analysis

## Root-cause categories

### Tool implementation

The tool returns incorrect data or handles failures poorly.

### Tool description or schema

The model cannot determine when or how to call the tool.

### Prompt or context

Instructions are ambiguous, conflicting, or incomplete.

### Model capability

The selected model cannot reliably perform the required reasoning or schema adherence.

### Orchestration

Messages, state, routing, or tool results are handled incorrectly.

### Retrieval

Required evidence was not found, ranked, filtered, or supplied correctly.

### Evaluator or dataset

The test incorrectly rejects valid behavior or misses important failures.

### Requirement

Stakeholders have not defined what correct behavior means.

## Debugging order

1. Reproduce the case.
2. Inspect the trace.
3. Identify the first incorrect step.
4. Classify the root cause.
5. Fix the responsible component.
6. Add a regression test.
7. Rerun the full relevant dataset.

## Rule

Do not treat prompt changes as the universal fix.

## Related notes

- [[Production Readiness]]
- [[AI System Testing - MOC]]
- [[Tracing and Observability]]

## Related audit prompts

- [[06_Prompts/AI Failure Injection Audit|AI Failure Injection Audit]]
