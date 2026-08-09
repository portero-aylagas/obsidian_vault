---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Testing Strategy Audit

## Prompt

```text
Review the testing strategy for AI-integrated functionality in this project.

Context:
This project contains one or more LLM-powered features. I want a testing strategy that starts with normal deterministic software testing and adds AI-specific evaluation only where necessary.

Check:
- Which parts of the system are deterministic
- Which parts depend on LLM behavior
- Which parts depend on external tools, retrieval, APIs, or state
- Whether deterministic code is covered by normal unit tests
- Whether LLM behavior is incorrectly being tested with exact-string assertions
- Whether model outputs have appropriate semantic evaluations
- Whether intermediate AI steps need testing
- Whether final outputs are evaluated
- Whether failures and edge cases are covered
- Whether the current test suite mixes unit tests, integration tests, and evaluations without distinction
- Whether tests unnecessarily call real LLM APIs
- Whether important AI behavior currently has no regression coverage

Return:
1. Current testing architecture
2. Deterministic components that should use normal tests
3. AI components that need evaluations
4. Missing test layers
5. Highest-risk gaps
6. Minimal recommended testing strategy
7. Suggested order for implementing improvements
8. What would be over-engineering for this project

Rules:
- Do not edit files yet.
- Prefer deterministic tests whenever possible.
- Do not recommend LLM-as-judge when ordinary assertions are sufficient.
- Distinguish software tests from AI evaluations.
- Keep recommendations proportional to the project complexity.
```

## Related notes

- [[Prompt Library]]
- [[00_Foundations/AI Integration Foundations]]
- [[03_Quality/AI System Testing - MOC]]
