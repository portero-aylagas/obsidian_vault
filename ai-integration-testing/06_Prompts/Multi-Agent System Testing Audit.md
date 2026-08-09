---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# Multi-Agent System Testing Audit

## Prompt

```text
Audit testing for a multi-agent architecture.

Check:
- Agent responsibilities
- Supervisor/router behavior
- Delegation rules
- Handoffs
- Shared state
- Agent-to-agent messages
- Parallel execution
- Aggregation
- Conflict resolution
- Recursive delegation
- Duplicate work
- Deadlocks
- Cost amplification
- Termination
- Whether multiple agents are actually necessary

Return:
1. Agent inventory and responsibilities
2. Coordination architecture
3. Delegation test cases
4. Handoff test cases
5. Shared-state risks
6. Conflict and aggregation tests
7. Loop/deadlock risks
8. Cost and latency risks
9. Simplification opportunities
10. Minimal recommended test suite

Rules:
- Do not edit files yet.
- Challenge unnecessary multi-agent complexity.
- Prefer deterministic orchestration when specialization does not require autonomy.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/Multi-Agent Systems]]
