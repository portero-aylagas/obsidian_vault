---
tags: [ai-integration, rag, retrieval]
type: architecture
complexity: intermediate
---

# RAG Systems

## Purpose

Retrieve external information and provide it to a model for grounded generation.

```text
Question → retrieval → selected context → LLM → answer with evidence
```

## Two subsystems

### Offline ingestion

```text
Sources → loading → cleaning → chunking → metadata → indexing
```

### Online query flow

```text
Question → query processing → retrieval → filtering/reranking
→ context assembly → generation → citations
```

## Evaluate separately

### Retrieval quality

- Recall of relevant material
- Precision of retrieved material
- Ranking quality
- Metadata and permission filters
- Empty retrieval behavior
- Freshness

### Generation quality

- Faithfulness to retrieved context
- Correct citations
- Handling conflicting evidence
- Appropriate uncertainty
- No unsupported factual claims

### End-to-end quality

- Did the system find the needed evidence?
- Did the model use it correctly?
- Was the final answer useful?

## Main failure modes

- Bad chunking
- Missing or stale documents
- Irrelevant retrieval
- Lost metadata
- Context overload
- Unsupported synthesis
- Citation mismatch

## Related notes

- [[Agentic RAG]]
- [[Evaluation Datasets]]
- [[Tracing and Observability]]

## Related audit prompts

- [[06_Prompts/RAG Testing Strategy Audit|RAG Testing Strategy Audit]]
