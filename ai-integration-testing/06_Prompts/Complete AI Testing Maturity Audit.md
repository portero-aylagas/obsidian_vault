---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# Complete AI Testing Maturity Audit

## Prompt

```text
Perform a complete testing maturity review for AI-integrated functionality in this project.

Evaluate the project across these levels:

Level 1: Deterministic software tests
Level 2: Tool and component tests
Level 3: Single-model provider integration tests
Level 4: Structured-output and interface tests
Level 5: Multi-call pipeline tests
Level 6: Workflow/path tests
Level 7: Retrieval/RAG evaluation
Level 8: State and multi-turn tests
Level 9: Agent trajectory evaluation
Level 10: Evaluation datasets and automated evaluators
Level 11: Regression experiments
Level 12: Failure injection and resilience
Level 13: AI security tests
Level 14: CI/CD quality gates
Level 15: Production tracing and online evaluation

For each level determine:
- Whether it applies to this project
- Current maturity
- Missing coverage
- Risk caused by the gap
- Whether it should be implemented now or later

Return:
1. Architecture classification
2. Testing maturity table
3. Critical gaps
4. Recommended next three improvements
5. Medium-term improvements
6. Future/production improvements
7. Areas that do not apply
8. Areas where additional complexity should explicitly be avoided

Rules:
- Do not edit files yet.
- Do not recommend every testing technique just because it exists.
- Base recommendations on the actual architecture and risk.
- Prioritize improvements by value, not sophistication.
```

## Related notes

- [[Prompt Library]]
- [[00_Foundations/AI Integration Foundations]]
- [[03_Quality/AI System Testing - MOC]]
