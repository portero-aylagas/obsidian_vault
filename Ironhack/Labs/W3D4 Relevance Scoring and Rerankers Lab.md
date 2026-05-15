# W3D4 Relevance Scoring and Rerankers Lab

**Source folder**
- `W3D4_relevance_scoring_and_rerankers_for_trustworthy_AI_and_EU_AI_Act.html`

**Main files**
- `relevance_scoring_rerankers.py`
- `data/`
- `data/processed/`
- `lab_summary.md`
- `.env.example`

**Lab type**
- Applied RAG optimization lab
- Main value: make retrieval quality easier to inspect and justify

## What This Lab Teaches

This lab builds a Trustworthy AI RAG pipeline using two source types:

- the English Trustworthy AI PDF
- a podcast transcript generated from audio

Pipeline:

```text
PDF + podcast audio
-> Markdown + transcript
-> chunks with metadata
-> embeddings
-> Pinecone index
-> baseline retrieval
-> LLM relevance scoring
-> metadata-filtered retrieval
-> grounded answer
```

## Techniques Practiced

- PDF-to-Markdown conversion
- Whisper transcription
- transcript segment storage
- chunking with metadata
- OpenAI embeddings
- Pinecone vector storage
- baseline semantic retrieval
- LLM relevance scoring
- combined ranking
- metadata filtering by source
- grounded answer generation

## Important Architecture

```text
relevance_scoring_rerankers.py
Single readable workflow for source preparation, indexing, retrieval, reranking, and answer generation

data/
Raw PDF and audio source files

data/processed/
Generated Markdown and transcript artifacts
```

## Important Code Patterns

### Baseline retrieval
Start with vector similarity search to get likely relevant chunks.

```text
query
-> query embedding
-> Pinecone similarity search
-> retrieved chunks
```

### Relevance scoring
Use an LLM as a second pass over retrieved chunks.

```text
query + retrieved chunk
-> LLM relevance score
-> explanation
-> reordered or justified results
```

### Metadata filtering
Compare behavior by source.

```text
source = pdf
source = podcast transcript
```

The PDF is stronger for precise definitions. The transcript is useful as a secondary explanatory source.

## What Was Provided

- A RAG retrieval task with source documents and expected scoring behavior.
- Existing retrieval code to extend with relevance scoring and comparison logic.
- Lab guidance around rerankers, trustworthy answers, and evidence inspection.

## Extra Concepts From Lab Source

- LLM relevance scoring
- similarity and relevance score fusion
- dedicated rerankers
- cross-encoder reranking
- hybrid search
- domain-specific reranker fine-tuning
- reranker A/B testing
- reranking cost analysis

## What I Practiced

- Moving beyond "top-k results are enough"
- Comparing baseline vector retrieval with scored retrieval
- Explaining why a retrieved chunk is relevant
- Using source metadata to inspect retrieval behavior
- Building trust in a RAG answer by showing evidence

## Improvement Ideas

- Add a separate reranker model and compare it against LLM scoring.
- Track cost and latency per reranking strategy.
- Build a small relevance-labeled evaluation set for repeatable testing.

## Links to Topic Notes

- [[../RAG/RAG Basics]]
- [[../RAG/RAG Optimization]]
- [[../Prompting/Dynamic Prompting]]
- [[../APIs/OpenAI API]]

## What To Reuse Later

- Keep raw source files separate from processed artifacts.
- Attach source metadata to every chunk.
- Use baseline retrieval before adding reranking.
- Add a human-readable relevance explanation when trust matters.
- Compare retrieval behavior by source type.

## Key Takeaway

Reranking and relevance scoring make RAG easier to evaluate. They do not replace retrieval; they add a second inspection layer that explains which chunks deserve to ground the final answer.
