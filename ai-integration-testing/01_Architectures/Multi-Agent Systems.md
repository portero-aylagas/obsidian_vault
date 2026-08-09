---
tags: [ai-integration, multi-agent]
type: architecture
complexity: advanced
---

# Multi-Agent Systems

## Common patterns

- Supervisor and specialists
- Router and selected agent
- Agent handoffs
- Parallel agents with aggregation
- Review or critique agents

## New testing concerns

- Task decomposition
- Delegation accuracy
- Shared-state consistency
- Duplicate work
- Contradictory outputs
- Communication loss
- Recursive delegation
- Deadlocks
- Cost growth
- Aggregation quality

## Test scopes

1. Each agent independently.
2. Handoff contracts.
3. Shared state.
4. Coordination paths.
5. Final aggregation.
6. Failure containment.

## Design warning

Several steps do not automatically justify several agents. Prefer a deterministic workflow when roles and sequence are known.

## Related notes

- [[AI Agents]]
- [[Graph-Based Workflows]]
- [[Human-in-the-Loop Systems]]

## Related audit prompts

- [[06_Prompts/Multi-Agent System Testing Audit|Multi-Agent System Testing Audit]]
