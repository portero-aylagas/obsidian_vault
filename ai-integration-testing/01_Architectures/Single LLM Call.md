---
tags: [ai-integration, architecture, llm]
type: architecture
complexity: basic
---

# Single LLM Call

## Purpose

Use one model invocation inside otherwise deterministic software.

```text
Input → prompt/context → LLM → validation → result
```

Typical uses: classification, extraction, rewriting, summarization, tagging, and structured generation.

## Control model

Application code decides:

- when the call occurs;
- what context is supplied;
- what schema is required;
- what happens after the response.

## What to test

### Before the call

- Input validation
- Prompt construction
- Context selection
- Sensitive-data filtering
- Token limits

### Call boundary

- Correct model and parameters
- Timeout and retry behavior
- Authentication and rate limits
- Usage metadata

### After the call

- Non-empty response
- Schema parsing
- Required fields
- Value constraints
- Fallback behavior

### Semantic evaluation

- Accuracy
- Relevance
- Instruction-following
- Groundedness when context is supplied
- Repeatability

## Main failure modes

- Invalid output format
- Hallucinated content
- Prompt ambiguity
- Excessive verbosity
- Latency or rate-limit failure
- Silent model behavior change

## Next step

When one call cannot reliably perform the whole task, move to [[Multi-Call Pipeline]].

## Related notes

- [[AI System Testing - MOC]]
- [[LangChain]]

## Related audit prompts

- [[06_Prompts/Single LLM Call Testing Audit|Single LLM Call Testing Audit]]
