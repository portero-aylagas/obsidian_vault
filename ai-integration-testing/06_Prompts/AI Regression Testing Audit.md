---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Regression Testing Audit

## Prompt

```text
Review regression testing for AI-powered features.

Check:
- Whether there is a baseline model/prompt/configuration
- Whether prompt changes are compared against previous versions
- Whether model changes are evaluated on the same dataset
- Whether temperature changes are evaluated
- Whether tool-description changes are evaluated
- Whether retrieval changes are evaluated
- Whether historical failures remain permanent test cases
- Whether important metrics have acceptable regression thresholds
- Whether exact equality is incorrectly expected from probabilistic outputs
- Whether changes modify several major variables at once
- Whether experiments record model, prompt, dataset, and configuration versions

Return:
1. Current regression strategy
2. Missing baseline information
3. Important regression metrics
4. Suggested acceptance thresholds
5. Recommended experiment comparison process
6. Versioning gaps
7. Minimal CI regression gate
8. What should not block deployment

Rules:
- Do not edit files yet.
- Avoid unstable pass/fail thresholds.
- Prefer meaningful quality deltas over tiny score fluctuations.
```

## Related notes

- [[Prompt Library]]
- [[03_Quality/Evaluation Datasets]]
