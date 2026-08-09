---
tags: [observability, tracing, ai-testing]
type: practice
---

# Tracing and Observability

## Purpose

Tracing explains the execution of an individual request.

## Capture

- System and user messages
- Prompt or context version
- Model calls
- Tool calls and arguments
- Tool outputs
- Intermediate state
- Final response
- Tokens and cost
- Latency
- Errors and retries

## For agents

Inspect the complete trajectory:

```text
model decision
→ tool call
→ tool result
→ next model decision
→ final answer
```

## Observability is not evaluation

A complete trace can still represent a bad result. Tracing provides evidence; evaluators decide whether the behavior meets requirements.

## Privacy controls

- Do not log secrets.
- Redact personal or proprietary data where required.
- Control trace retention.
- Restrict access.
- Treat tool outputs as potentially sensitive.

## Related notes

- [[LangSmith]]
- [[AI System Testing - MOC]]
- [[Production Readiness]]

## Related audit prompts

- [[06_Prompts/AI Observability and LangSmith Testing Audit|AI Observability and LangSmith Testing Audit]]
