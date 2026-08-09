---
tags: [ai-integration, architecture, pipeline]
type: architecture
complexity: intermediate
---

# Multi-Call Pipeline

## Purpose

Use several model calls in a fixed, code-controlled sequence.

```text
Input
→ LLM A
→ deterministic transformation
→ LLM B
→ validation
→ final result
```

## Key characteristic

The sequence is predetermined. The model does not choose the next stage.

## Testing scopes

1. Test each call independently.
2. Test every interface between calls.
3. Test the complete pipeline.

## Intermediate artifacts

Treat each intermediate result as a contract:

- explicit schema;
- documented meaning;
- validation rules;
- provenance;
- suitability for the next stage.

## Main failure modes

- Error propagation
- Accumulated hallucinations
- Loss of context
- Misinterpreted intermediate output
- Increased latency and cost
- Partial completion
- Retry duplication

## Design practices

- Prefer structured intermediate outputs.
- Validate before forwarding.
- Preserve source references.
- Retry only the failed stage when safe.
- Record per-stage latency and token use.

## Related notes

- [[Single LLM Call]]
- [[Branching AI Workflow]]
- [[Tracing and Observability]]

## Related audit prompts

- [[06_Prompts/Multi-Call Pipeline Testing Audit|Multi-Call Pipeline Testing Audit]]
