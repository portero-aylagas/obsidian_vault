---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Production Readiness Testing Audit

## Prompt

```text
Assess testing readiness before deploying this AI-integrated application.

Check:
- Deterministic unit coverage
- Tool/component coverage
- Provider integration tests
- Evaluation dataset quality
- Regression coverage
- Failure handling
- Retry behavior
- Timeout configuration
- Model/provider fallback behavior
- Security tests
- Prompt injection resistance
- Sensitive-data handling
- Cost limits
- Token limits
- Tool-call limits
- Agent iteration limits
- Latency expectations
- Production tracing
- Online evaluation
- User feedback collection
- Alerting
- Rollback strategy

Return:
1. Production readiness summary
2. Critical blockers
3. Important but non-blocking gaps
4. Required pre-production tests
5. Recommended monitoring
6. Release gates
7. Post-deployment validation plan
8. What can reasonably wait until later

Rules:
- Do not edit files yet.
- Distinguish true deployment blockers from nice-to-have improvements.
- Keep recommendations proportional to application risk.
```

## Related notes

- [[Prompt Library]]
- [[04_Operations/Production Readiness]]
