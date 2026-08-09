---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# LangGraph Testing Audit

## Prompt

```text
Audit testing for LangGraph workflows or agents.

Check:
- State schema
- Nodes
- Edges
- Conditional edges
- Entry points
- Termination conditions
- Checkpointing/persistence
- Interrupts
- Resume behavior
- Human approval steps
- Error paths

For each node:
- Determine whether it contains deterministic code, an LLM call, retrieval, or tool execution
- Determine whether it can be tested independently

For the graph:
- Check important execution paths
- Check state transitions
- Check branch routing
- Check loops
- Check maximum-step behavior
- Check interruption and resume behavior
- Check repeated execution/idempotency
- Check state corruption or missing keys

Return:
1. Graph structure
2. State model
3. Node-level tests
4. Edge/routing tests
5. Path-level tests
6. Persistence/resume tests
7. Loop and termination risks
8. Minimal recommended graph test suite

Rules:
- Do not edit files yet.
- Test nodes independently before testing full graph execution.
- Do not rely only on end-to-end graph tests.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/Graph-Based Workflows]]
- [[02_Frameworks/LangGraph]]
