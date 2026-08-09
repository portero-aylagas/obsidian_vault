---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI CI-CD Testing Audit

## Prompt

```text
Review how AI-related tests should fit into CI/CD for this project.

Classify tests into:
- Fast deterministic unit tests
- Tool/component tests
- Mocked AI orchestration tests
- Real-provider integration tests
- Small evaluation suite
- Full evaluation suite
- Security tests
- Production monitoring

Check:
- What should run on every commit
- What should run on pull requests
- What should run before releases
- What should run nightly or periodically
- Which tests require API credentials
- Which tests are expensive
- Which evaluations are nondeterministic
- Which failures should block deployment
- Whether flaky AI evaluations could create unreliable CI

Return:
1. Recommended CI test layers
2. Tests per commit
3. Tests per pull request
4. Pre-release evaluations
5. Scheduled evaluations
6. Blocking criteria
7. Non-blocking quality signals
8. Cost-control recommendations
9. Minimal implementation order

Rules:
- Do not edit CI files yet.
- Keep normal unit tests fast and deterministic.
- Do not run the full AI evaluation suite on every small code change unless justified.
```

## Related notes

- [[Prompt Library]]
- [[04_Operations/Production Readiness]]
