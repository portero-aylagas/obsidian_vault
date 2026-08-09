---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# RAG Testing Strategy Audit

## Prompt

```text
Audit the testing strategy for Retrieval-Augmented Generation in this project.

Separate retrieval quality from generation quality.

Check ingestion:
- Document loading
- Cleaning
- Chunking
- Metadata
- Embeddings
- Index updates
- Duplicate handling
- Missing documents
- Permission metadata where applicable

Check retrieval:
- Whether relevant chunks are returned
- Recall
- Precision/relevance
- Ranking quality
- Metadata filtering
- Empty retrieval behavior
- Ambiguous queries
- Query rewriting
- Stale or conflicting documents

Check generation:
- Whether answers are grounded in retrieved context
- Whether unsupported claims are introduced
- Whether citations/source references are correct
- Whether the model handles insufficient evidence correctly
- Whether conflicting sources are handled explicitly
- Whether retrieved context is actually used

Return:
1. Current RAG architecture
2. Ingestion test gaps
3. Retrieval test gaps
4. Generation evaluation gaps
5. Recommended retrieval metrics
6. Recommended generation metrics
7. Example evaluation dataset structure
8. Highest-risk failure modes
9. Minimal next improvements

Rules:
- Do not edit files yet.
- Do not evaluate RAG only by looking at the final answer.
- Separate retrieval failures from generation failures.
- Prefer deterministic retrieval metrics where possible.
```

## Related notes

- [[Prompt Library]]
- [[01_Architectures/RAG Systems]]
