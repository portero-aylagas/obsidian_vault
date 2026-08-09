---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Architecture vs Testing Complexity Audit

## Prompt

```text
Review whether the current AI architecture is more complex than the task requires.

Classify the application as one or more of:
- Single LLM call
- Multi-call deterministic pipeline
- Branching workflow
- Tool-using workflow
- RAG
- Stateful conversation
- LangGraph workflow
- Agent
- Agentic RAG
- Multi-agent system

Check:
- Who controls the next execution step: code or model
- Whether dynamic tool selection is actually necessary
- Whether graph orchestration is necessary
- Whether multiple LLM calls provide measurable value
- Whether an agent could be replaced with a deterministic workflow
- Whether multiple agents could be replaced with one agent or workflow
- Whether complexity is increasing testing requirements without meaningful benefit

Return:
1. Current architecture classification
2. Sources of complexity
3. Testing complexity introduced by each source
4. Simplification opportunities
5. Features that genuinely require dynamic AI behavior
6. Minimal architecture that would satisfy current requirements
7. Testing strategy appropriate to that architecture

Rules:
- Do not edit files yet.
- Prefer simpler architectures when they provide equivalent functionality.
- Do not simplify away capabilities the application actually needs.
```

## Related notes

- [[Prompt Library]]
- [[00_Foundations/Architecture Classification]]
