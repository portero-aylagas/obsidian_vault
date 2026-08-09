---
tags: [ai-integration, rag, agents]
type: architecture
complexity: advanced
---

# Agentic RAG

## Purpose

Let a model decide whether, when, and how to retrieve information.

The model may choose:

- whether retrieval is needed;
- which source to search;
- how to formulate the query;
- whether evidence is sufficient;
- whether to retrieve again.

## Evaluation dimensions

### Retrieval

- Correct source
- Useful query
- Relevant results
- Freshness and permissions

### Agent trajectory

- Retrieval used when needed
- Retrieval avoided when unnecessary
- Bounded number of searches
- Correct interpretation of evidence

### Final answer

- Faithful to evidence
- Properly cites or attributes sources
- Expresses uncertainty when evidence is insufficient

## Main failure modes

- No retrieval when required
- Unnecessary retrieval
- Wrong source
- Poor query generation
- Repeated searches
- Ignored evidence
- Unsupported answer

## Related notes

- [[RAG Systems]]
- [[AI Agents]]
- [[Evaluation Datasets]]

## Related audit prompts

- [[06_Prompts/Agentic RAG Testing Audit|Agentic RAG Testing Audit]]
