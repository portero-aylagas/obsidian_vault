---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# Agent Testing Strategy Audit

## Prompt

```text
Audit the testing strategy for LLM agents in this project.

Check:
- Agent system instructions
- Available tools
- Tool descriptions
- Tool argument schemas
- Tool selection
- Tool ordering
- Repeated tool calls
- Missing tool calls
- Intermediate reasoning decisions visible through traces
- Tool results returned to the model
- Final answer synthesis
- Stopping behavior
- Maximum iterations
- Error recovery
- Unsafe or unnecessary actions
- Whether the agent should actually be a deterministic workflow instead

Evaluate separately:
- Initial model decision
- Tool selection
- Tool arguments
- Tool execution
- Intermediate model calls
- Final answer
- Complete trajectory

Return:
1. Agent architecture
2. Expected agent trajectories
3. Tool-selection test cases
4. Tool-argument test cases
5. Trajectory evaluation needs
6. Final-answer evaluation needs
7. Loop/termination risks
8. Failure recovery cases
9. Cases where deterministic orchestration would be preferable
10. Minimal recommended test strategy

Rules:
- Do not edit files yet.
- Do not evaluate only the final answer.
- Distinguish tool correctness from agent tool-selection correctness.
- Prefer deterministic workflows when the execution order is actually fixed.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/AI Agents]]
