---
tags: [ai-testing, evaluation, datasets]
type: practice
---

# Evaluation Datasets

## Purpose

A dataset converts remembered expectations into repeatable test cases.

## Recommended categories

- Happy paths
- Boundary cases
- Ambiguous inputs
- Negative cases
- Tool-specific cases
- Adversarial inputs
- Historical failures
- Long or multi-turn cases

## Example structure

```yaml
input:
  user_message: "Many monsters appeared. Fix it!"
expectations:
  required_behavior:
    - use relevant evidence
    - provide an actionable response
  forbidden_behavior:
    - expose secrets
    - claim unsupported guarantees
  expected_tools:
    - check_hawkins_records
```

## Evaluation dimensions

- Completion
- Correct routing or tool use
- Structured-output validity
- Groundedness
- Relevance
- Completeness
- Safety
- Latency
- Cost

## Dataset growth rule

> [!important]
> Every meaningful failure should become a permanent regression example.

## Versioning

Record:

- dataset version;
- prompt version;
- model version;
- tool version;
- evaluator version.

## Related notes

- [[AI System Testing - MOC]]
- [[LangSmith]]
- [[Evaluation Case Template]]

## Related audit prompts

- [[06_Prompts/AI Evaluation Dataset Audit|AI Evaluation Dataset Audit]]
- [[06_Prompts/AI Evaluator Quality Audit|AI Evaluator Quality Audit]]
- [[06_Prompts/AI Regression Testing Audit|AI Regression Testing Audit]]
