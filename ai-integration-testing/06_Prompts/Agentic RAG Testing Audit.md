---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# Agentic RAG Testing Audit

## Prompt

```text
Audit an agentic RAG system where the model decides whether, when, or how to retrieve information.

Check:
- Whether retrieval is triggered when needed
- Whether retrieval is skipped when unnecessary
- Which retriever or source is selected
- Query generation quality
- Query rewriting
- Number of retrieval attempts
- Retrieved context quality
- Whether retrieved evidence is used correctly
- Whether the agent retrieves repeatedly without improvement
- Whether the final answer contains unsupported claims
- Whether source attribution is correct
- Whether retrieval failure is handled properly
- Whether the same use case could use simpler deterministic RAG

Return:
1. Agentic RAG architecture
2. Retrieval-decision test cases
3. Retrieval-quality metrics
4. Agent trajectory metrics
5. Groundedness metrics
6. Failure cases
7. Loop/repeated retrieval risks
8. Minimal improvements
9. Cases that should use simpler two-step RAG

Rules:
- Do not edit files yet.
- Evaluate retrieval decisions separately from retrieved-content quality.
- Evaluate final generation separately from retrieval.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/Agentic RAG]]
