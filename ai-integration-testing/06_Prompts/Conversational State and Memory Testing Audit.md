---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# Conversational State and Memory Testing Audit

## Prompt

```text
Audit testing for conversation history, state, and memory.

Check:
- What state is stored
- Where it is stored
- How state is updated
- Whether state persists between turns or sessions
- Whether previous user facts can be corrected
- Whether stale information can remain active
- Whether state can leak between users
- Whether conversation summaries preserve important information
- Whether long conversations cause context growth problems
- Whether deleted information is actually removed
- Whether prompt injection can persist through stored memory
- Whether repeated operations can occur after resume/retry
- Whether multi-turn tests exist

Return:
1. Current state and memory model
2. State invariants that should be tested
3. Multi-turn test scenarios
4. Persistence risks
5. Privacy/isolation risks
6. Context growth risks
7. Minimal recommended test suite
8. What would be excessive for the current project

Rules:
- Do not edit files yet.
- Test complete conversations when behavior depends on previous turns.
- Distinguish temporary conversation context from persistent memory.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/Conversation and Memory]]
