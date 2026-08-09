---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# Single LLM Call Testing Audit

## Prompt

```text
Audit the testing strategy for single-LLM-call features in this project.

Context:
I want to test the simplest AI integration correctly before introducing more complex agent or workflow testing patterns.

Check:
- How input is validated before the LLM call
- How prompts/messages are constructed
- Whether prompt construction can be tested deterministically
- Whether model configuration is testable
- Whether API/provider calls are isolated enough to mock
- Whether structured outputs are validated
- Whether free-text outputs are tested too rigidly
- Whether semantic output quality needs evaluation
- Whether provider errors, timeouts, rate limits, and malformed responses are handled
- Whether token usage or latency should be measured
- Whether model calls are unnecessarily used during ordinary unit tests
- Whether repeated runs are needed to measure output stability

Return:
1. Current single-call architecture
2. What should be unit tested
3. What should be mocked
4. What should use a real model integration test
5. What requires semantic evaluation
6. Important failure cases
7. Minimal example test structure
8. What not to test with exact-string assertions

Rules:
- Do not edit files yet.
- Keep unit tests deterministic.
- Use real model calls only where they provide meaningful coverage.
- Do not introduce agent-testing concepts unless the project actually contains agents.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/Single LLM Call]]
