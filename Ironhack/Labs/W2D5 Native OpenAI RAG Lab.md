# W2D5 Native OpenAI RAG Lab

**Source folder**
- `W2D5_rag_with_open_ai`

**Main files**
- `lab_source/Ironhack Student Portal.html`

**Lab type**
- guided implementation lab
- Main value: understand RAG by building the pipeline directly with OpenAI APIs instead of hiding the pieces behind a framework

## What This Lab Teaches

This lab decomposes RAG into explicit steps:

```text
documents
-> chunks
-> embeddings
-> vector search
-> retrieved context
-> generated answer
```

The main learning is control: direct API use makes retrieval, context formatting, and cost/performance choices visible.

## Techniques Practiced

- document loading
- chunking
- embedding generation
- batched embedding requests
- in-memory vector storage
- cosine similarity search
- top-k retrieval
- context formatting
- grounded answer generation
- source tracking and citations

## Important Architecture

```text
Index time:
document chunks -> OpenAI embeddings -> vector store

Query time:
question -> query embedding -> similarity search -> context -> chat completion
```

This separates indexing from answering. That distinction matters in any production RAG design.

## Important Code Patterns

### Batched embedding concept

```python
for batch in batches(texts, size=100):
    embeddings = client.embeddings.create(input=batch, model=model)
```

### Similarity retrieval concept

```python
scores = cosine_similarity(query_embedding, chunk_embeddings)
top_chunks = select_top_k(scores, chunks)
```

## What Was Provided

The lab source provides the full target pipeline and suggested implementation file name, but the workspace currently contains only the HTML source.

## What I Practiced

- understanding RAG without LangChain abstraction
- connecting embeddings to retrieval
- seeing where source citations enter the pipeline
- thinking about top-k and context-window tradeoffs
- recognizing cost and token pressure in RAG

## Links to Topic Notes

- [[../RAG/RAG Basics]]
- [[../RAG/RAG Optimization]]
- [[../APIs/OpenAI API]]

## What To Reuse Later

- Keep chunk metadata next to every embedding.
- Batch embedding calls when indexing many chunks.
- Limit retrieved context intentionally instead of dumping everything into the prompt.
- Debug poor answers by checking retrieval before checking generation.

## Improvement Ideas

- Add reranking after initial vector search.
- Combine keyword and semantic retrieval.
- Cache embeddings and repeated answers.
- Add retrieval and answer-quality evaluation metrics.
- Add conversation memory only after single-turn RAG works.

## Key Takeaway

Native RAG makes the hidden parts visible: embeddings retrieve context, retrieval quality controls answer quality, and context formatting is part of the model interface.
