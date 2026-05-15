# RAG Optimization

**Labs**
- `week-3/rag_pipeline.ipynb`
- `W2D5_rag_with_open_ai`
- `W3D4_relevance_scoring_and_rerankers_for_trustworthy_AI_and_EU_AI_Act.html`

## Main Techniques
- Query rewriting
- Sub-query decomposition
- Parent document retrieval
- Reranking
- LLM relevance scoring
- Combined retrieval scoring
- Metadata filtering

## Examples

### Query rewriting
Useful when the user query is vague.

```python
def rewrite_query(original_query):
    prompt = f"Rewrite this query to be more specific: {original_query}"
```

Example:

```text
Original: "Tell me about policies"
Rewritten: "What are the company's refund and cancellation policies?"
```

### Sub-query decomposition
Useful when one question contains several questions.

```python
def decompose_query(complex_query):
    prompt = f"Break this complex query into 2-3 simpler sub-queries: {complex_query}"
```

Example:

```text
Complex query:
"How does machine learning compare to deep learning, and when should I use each?"

Sub-queries:
1. What is machine learning?
2. What is deep learning?
3. When should each approach be used?
```

### Parent document retrieval
- Retrieve small chunks for better matching
- Return larger parent documents for fuller context

Example pattern:

```text
Small chunk:
"Refunds are available within 30 days."

Parent document:
Full refund policy section with conditions, exclusions, and examples.
```

### Reranking
```python
def rerank_documents(query, documents, top_k=2):
    # score documents and reorder them
    ...
```

LLM-based reranking idea:

```python
prompt = f"""
Rate the relevance of this document to the query from 0 to 1.

Query:
{query}

Document:
{document.page_content}
"""
```

### Relevance scoring
The W3D4 lab uses an LLM to score retrieved chunks from 0 to 5 and explain the score.

```text
query + retrieved chunk
-> relevance score
-> short explanation
-> combined score
```

This makes the ranking easier to justify than raw vector similarity alone.

### Source-aware retrieval
The Trustworthy AI lab compares chunks from two sources:

- PDF chunks for precise definitions
- podcast transcript chunks for secondary explanation

Metadata filtering lets you inspect each source separately.

### Metadata filtering
- Filter by date
- Filter by category
- Filter by source

Example:

```python
filtered_docs = vectorstore.similarity_search(
    query,
    k=3,
    filter={"category": "regulations"}
)
```

## When to Use Each Technique

- Query rewriting: when users ask vague questions
- Sub-query decomposition: when questions contain multiple parts
- Parent document retrieval: when chunks are too small to answer fully
- Reranking: when retrieved results are noisy
- Relevance scoring: when you need an explanation of why a chunk should be trusted
- Metadata filtering: when date, source, or category matters

## Key Idea
- Basic RAG explains retrieval.
- RAG optimization improves retrieval quality.
- Relevance scoring improves retrieval explainability.

## Progression
- Extends [[RAG Basics]]
- Applied in [[../Labs/W3D4 Relevance Scoring and Rerankers Lab]]
