---
tags: [ai-security, testing]
type: practice
---

# Security Testing

## Threat categories

### Prompt injection

Untrusted input attempts to override application instructions.

### Tool-output injection

External content contains instructions intended to manipulate the model.

### Argument injection

Model-generated arguments contain malicious or unauthorized values.

### Secret leakage

Secrets appear in prompts, traces, logs, errors, or final output.

### Excessive agency

The model can perform high-impact actions without sufficient controls.

### Resource exhaustion

The system loops, repeatedly calls tools, or consumes excessive tokens and cost.

## Required controls

- Validate all tool arguments.
- Authorize actions in ordinary code.
- Separate data from trusted instructions.
- Require approval for high-risk actions.
- Apply time, token, tool-call, and cost limits.
- Redact sensitive logs.
- Test tenant and user isolation.

## Security principle

> [!warning]
> The model is not a trusted execution environment and is not an authorization system.

## Related notes

- [[Tool-Using Deterministic Workflow]]
- [[AI Agents]]
- [[Production Readiness]]

## Related audit prompts

- [[06_Prompts/AI Security Testing Audit|AI Security Testing Audit]]
