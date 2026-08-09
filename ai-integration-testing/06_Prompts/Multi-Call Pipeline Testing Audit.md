---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# Multi-Call Pipeline Testing Audit

## Prompt

```text
Audit LLM pipelines containing multiple sequential model calls.

Check:
- What each LLM call is responsible for
- What data is passed from one stage to the next
- Whether intermediate outputs have explicit schemas
- Whether each stage can be tested independently
- Whether failures in an early stage propagate incorrectly
- Whether downstream stages assume information that earlier stages do not guarantee
- Whether intermediate outputs should be persisted or traced
- Whether one bad model response can corrupt the entire pipeline
- Whether retries happen at the correct stage
- Whether the pipeline unnecessarily repeats context
- Whether latency and token usage accumulate excessively
- Whether the final output can pass while intermediate behavior is incorrect

Return:
1. Pipeline stages
2. Responsibility of each stage
3. Interfaces between stages
4. Tests required for each individual stage
5. Tests required between stages
6. End-to-end tests required
7. Failure propagation risks
8. Minimal improvements to testability
9. What would be unnecessary complexity

Rules:
- Do not edit files yet.
- Treat intermediate boundaries as first-class test targets.
- Do not evaluate only the final answer.
- Prefer structured contracts between stages where downstream code depends on specific data.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/Multi-Call Pipeline]]
