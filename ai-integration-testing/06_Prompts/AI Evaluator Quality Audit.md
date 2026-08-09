---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Evaluator Quality Audit

## Prompt

```text
Audit the evaluators used to score AI behavior.

Check which requirements are currently evaluated using:
- Normal assertions
- Code-based evaluators
- Exact-match checks
- Schema validation
- LLM-as-judge
- Human review

Determine:
- Which evaluations should be deterministic
- Which genuinely require semantic judgment
- Whether LLM judges have clear rubrics
- Whether different quality dimensions are incorrectly combined into one score
- Whether judge prompts are vague
- Whether judge outputs are structured
- Whether evaluators have been calibrated against human judgments
- Whether pairwise evaluation would be more reliable
- Whether thresholds are meaningful
- Whether evaluator failures can incorrectly block releases

Return:
1. Evaluator inventory
2. Evaluators that should remain deterministic
3. Evaluators that need semantic judgment
4. Weak or ambiguous rubrics
5. Recommended metric separation
6. Calibration strategy
7. Minimal improvements
8. Evaluations that should be removed

Rules:
- Do not edit evaluators yet.
- Do not use an LLM judge for facts that normal code can verify.
- Separate groundedness, relevance, completeness, and instruction-following.
```

## Related notes

- [[Prompt Library]]
- [[03_Quality/Evaluation Datasets]]
