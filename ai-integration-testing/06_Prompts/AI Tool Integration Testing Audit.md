---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Tool Integration Testing Audit

## Prompt

```text
Audit tools/functions exposed to an LLM or agent.

Check:
- Tool names and descriptions
- Tool argument schemas
- Input validation
- Output structure
- Error handling
- Timeouts
- Retries
- External API failures
- Authentication and authorization
- Side effects
- Idempotency where relevant
- Whether tools can be tested independently of the LLM
- Whether dangerous actions require confirmation
- Whether malformed tool results can confuse the model
- Whether tool outputs contain unnecessary sensitive information
- Whether tool descriptions make correct tool selection likely

Return:
1. Tool inventory
2. Tool purpose and risk level
3. Unit tests needed for each tool
4. Integration tests needed
5. Failure scenarios
6. Side-effect and idempotency risks
7. Schema weaknesses
8. Minimal improvements
9. What should remain outside AI evaluation

Rules:
- Do not edit files yet.
- Treat tools as normal software components first.
- Do not use LLM tests to verify behavior that can be tested directly.
- Highlight tools with irreversible or external side effects.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/Tool-Using Deterministic Workflow]]
