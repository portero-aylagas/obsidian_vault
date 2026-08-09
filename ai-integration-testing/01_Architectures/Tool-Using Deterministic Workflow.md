---
tags: [ai-integration, tools, workflow]
type: architecture
complexity: intermediate
---

# Tool-Using Deterministic Workflow

## Purpose

Use external systems while application code decides when and how tools run.

```text
Input
→ LLM extracts parameters
→ code validates parameters
→ code calls tool
→ LLM summarizes result
```

## Tool contract

Every tool should define:

- name;
- purpose;
- input schema;
- validation rules;
- output schema;
- error types;
- side effects;
- authorization requirements.

## What to test

### Tool implementation

- Valid and invalid inputs
- Empty results
- Timeouts
- Authentication failures
- Malformed responses
- Idempotency
- Side effects

### Workflow integration

- Correct arguments reach the tool
- Tool output reaches the next stage
- Failures remain distinguishable from empty results
- Retries do not duplicate actions

## Security rule

The model is not a security boundary. Validate and authorize tool calls in ordinary code.

## Related notes

- [[AI Agents]]
- [[Security Testing]]
- [[Failure Analysis]]

## Related audit prompts

- [[06_Prompts/AI Tool Integration Testing Audit|AI Tool Integration Testing Audit]]
