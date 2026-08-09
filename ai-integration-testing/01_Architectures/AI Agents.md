---
tags: [ai-integration, agents]
type: architecture
complexity: advanced
---

# AI Agents

## Purpose

Allow the model to participate in deciding the execution path.

```text
User input
→ model decides
   ├─ answer
   └─ call tool
       → tool result
       → model decides again
```

## Shared testing base

Agents still require tests for:

- prompts;
- model calls;
- tools;
- schemas;
- external dependencies;
- final output;
- latency, cost, security, and failures.

## Agent-specific testing

Evaluate the full trajectory:

- selected tool;
- tool arguments;
- ordering;
- repeated calls;
- interpretation of tool results;
- stopping behavior;
- final synthesis.

## Main failure modes

- Wrong or unnecessary tool
- Correct tool with wrong arguments
- Missing tool call
- Repeated tool loop
- Ignored tool output
- Fabricated tool result
- Premature termination
- Unsafe side effect
- Excessive cost

## Testing levels

1. Unit-test tools.
2. Test tool-call generation.
3. Test orchestration with controlled responses.
4. Run traced real-model cases.
5. Evaluate trajectories on a dataset.
6. Monitor production behavior.

## Related notes

- [[Tool-Using Deterministic Workflow]]
- [[Agentic RAG]]
- [[AI System Testing - MOC]]
- [[LangSmith]]

## Related audit prompts

- [[06_Prompts/Agent Testing Strategy Audit|Agent Testing Strategy Audit]]
