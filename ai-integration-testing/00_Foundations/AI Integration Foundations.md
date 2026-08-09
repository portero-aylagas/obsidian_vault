---
tags: [ai-integration, foundations]
type: concept
status: active
---

# AI Integration Foundations

## General anatomy

Most AI-enabled applications can be reduced to this structure:

```text
Input
→ deterministic preprocessing
→ context construction
→ model call
→ output parsing
→ deterministic post-processing
→ application result
```

More complex systems repeat, branch, or dynamically control these stages.

## Shared concerns across all architectures

### Model interaction

- Provider and model selection
- Prompt and message construction
- Model parameters
- Context-window limits
- Structured output
- Timeouts and retries
- Token usage and cost

### Software boundaries

- Input validation
- Output validation
- Error handling
- State management
- External dependencies
- Authorization
- Logging and tracing

### Quality

- Functional correctness
- Semantic quality
- Groundedness
- Stability across repeated runs
- Latency and cost
- Security and privacy

## Deterministic and nondeterministic regions

A useful design exercise is to label every component:

| Region | Example | Testing style |
|---|---|---|
| Deterministic | parsing JSON | ordinary unit test |
| Model-dependent | classifying a message | evaluation dataset |
| External | database or API | integration and failure tests |
| Stateful | conversation memory | sequence and state tests |
| Agentic | tool selection | trajectory evaluation |

## Core testing rule

```text
Test deterministic code with deterministic tests.
Evaluate model behavior with representative examples.
Trace complex execution to understand failures.
Monitor production to detect drift and unknown cases.
```

## Related notes

- [[Architecture Classification]]
- [[AI System Testing - MOC]]
- [[Tracing and Observability]]
- [[Production Readiness]]

## Related audit prompts

- [[06_Prompts/AI Testing Strategy Audit|AI Testing Strategy Audit]]
- [[06_Prompts/Complete AI Testing Maturity Audit|Complete AI Testing Maturity Audit]]
