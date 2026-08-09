---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# Branching Workflow Testing Audit

## Prompt

```text
Review testing for workflows where inputs can follow different execution paths.

Check:
- What branches exist
- What determines routing
- Whether routing is deterministic or LLM-driven
- Whether every important branch has test coverage
- Whether boundary and ambiguous routing cases exist
- Whether invalid routing decisions have a fallback
- Whether all paths terminate correctly
- Whether branches eventually converge correctly
- Whether failures inside one branch affect unrelated paths
- Whether route selection should use structured output
- Whether branch behavior is observable in traces or logs

Return:
1. Workflow map
2. Routing mechanism
3. Branch coverage gaps
4. Boundary cases
5. Failure cases
6. Tests needed per branch
7. Tests needed for routing
8. Minimal recommended test matrix

Rules:
- Do not edit files yet.
- Focus on behavior and execution paths rather than implementation style.
- Do not recommend graph frameworks unless current control flow genuinely needs them.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/Branching AI Workflow]]
