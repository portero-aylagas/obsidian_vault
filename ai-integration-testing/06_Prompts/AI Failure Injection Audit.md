---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Failure Injection Audit

## Prompt

```text
Audit whether the project tests AI and dependency failures intentionally.

Check behavior when:
- The LLM times out
- The provider returns an error
- Rate limits occur
- Credentials are invalid
- The model returns empty content
- Structured output is malformed
- A tool times out
- A tool raises an exception
- A tool returns malformed data
- Retrieval returns nothing
- Retrieval returns contradictory information
- Context limits are exceeded
- A model call succeeds but returns low-quality data
- One stage of a multi-call pipeline fails

Return:
1. Failure scenarios currently handled
2. Missing failure scenarios
3. Expected behavior for each failure
4. Retry recommendations
5. Fallback recommendations
6. Graceful degradation opportunities
7. Logging/observability requirements
8. What failures should fail fast

Rules:
- Do not edit files yet.
- Avoid blanket retries.
- Do not allow the model to invent missing tool or retrieval results.
```

## Related notes

- [[Prompt Library]]
- [[04_Operations/Failure Analysis]]
