---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Security Testing Audit

## Prompt

```text
Audit AI-specific security testing in this project.

Check:
- Prompt injection
- Tool-output injection
- Retrieval/document injection
- Secret leakage
- Environment variables
- Sensitive logging
- Sensitive tracing
- Authorization checks
- Tool argument validation
- Cross-user or cross-tenant data leakage
- Unsafe tool side effects
- Excessive agency
- Unbounded tool loops
- Resource exhaustion
- Stored malicious instructions in memory
- External content treated as instructions

Return:
1. AI attack surface
2. Highest-risk components
3. Missing security tests
4. Prompt-injection test cases
5. Tool-security test cases
6. Retrieval-security test cases
7. Secret-handling issues
8. Resource-control recommendations
9. Minimal protections appropriate for this project

Rules:
- Do not edit files yet.
- Treat the model as an untrusted decision-making component.
- Do not rely on prompts as the only authorization mechanism.
- Prefer deterministic authorization and validation outside the model.
```

## Related notes

- [[Prompt Library]]
- [[03_Quality/Security Testing]]
