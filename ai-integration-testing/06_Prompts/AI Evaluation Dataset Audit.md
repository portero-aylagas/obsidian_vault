---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Evaluation Dataset Audit

## Prompt

```text
Review the evaluation dataset used for AI features in this project.

Check:
- Number of examples
- Coverage of normal use cases
- Boundary cases
- Ambiguous inputs
- Adversarial inputs
- Tool-specific cases
- Negative cases where tools should not be called
- Historical failures
- Long inputs
- Invalid inputs
- Failure scenarios
- Diversity of wording and user behavior
- Expected outputs or behavioral expectations
- Whether examples are duplicated
- Whether the dataset reflects real application traffic
- Whether dataset versioning is needed

Return:
1. Current dataset structure
2. Coverage gaps
3. Missing high-value categories
4. Examples that should be added
5. Examples that should be removed or merged
6. Suggested dataset organization
7. Recommended initial dataset size
8. How production failures should become regression examples

Rules:
- Do not edit the dataset yet.
- Prefer representative cases over large volumes of synthetic duplicates.
- Include both positive and negative behavior examples.
```

## Related notes

- [[Prompt Library]]
- [[03_Quality/Evaluation Datasets]]
