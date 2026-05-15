# W2D5 RAG Chunking Lab

**Source folder**
- `W2D5_different_ways_to_chunk_podcast_and_pdf`

**Main file**
- `RAG_pdf_podcast.ipynb`

**Lab type**
- RAG preprocessing and chunking lab
- Main value: compare chunking strategies before building retrieval systems

## What This Lab Teaches

This lab focuses on how to split documents for RAG.

Workflow:

```text
load PDF
-> extract text
-> fixed-size chunking
-> recursive character chunking
-> token-based chunking
-> semantic chunking
-> compare chunk quality
```

## Techniques Practiced

- PDF loading
- text extraction
- fixed-size chunking
- recursive character chunking
- token-based chunking
- semantic chunking
- chunk comparison
- chunk visualization
- retrieval-readiness analysis

## Important Architecture

```text
document loader -> chunking strategy -> chunk metadata -> retrieval-ready text units
```

## Important Code Patterns

### PDF loading

```python
from langchain_community.document_loaders import PyPDFLoader

loader = PyPDFLoader(str(pdf_path))
documents = loader.load()
```

### Fixed-size chunking

```python
def chunk_text(text, chunk_size=500, chunk_overlap=50):
    chunks = []
    start = 0

    while start < len(text):
        end = start + chunk_size
        chunks.append(text[start:end])
        start = end - chunk_overlap

    return chunks
```

### Recursive character chunking

```python
splitter = RecursiveCharacterTextSplitter(
    chunk_size=500,
    chunk_overlap=50
)

chunks = splitter.split_documents(documents)
```

Why it matters:
- Recursive splitting tries to preserve boundaries like paragraphs and sentences.

### Token-based chunking

```text
Split based on model token limits rather than raw character count.
```

Why it matters:
- LLMs operate on tokens, not characters.
- Token chunking can better control prompt size.

### Semantic chunking

```text
Group text based on meaning instead of only length.
```

Why it matters:
- Better chunk boundaries can improve retrieval quality.
- It is more expensive and complex than simple splitting.

## What Was Provided

This lab appears to be a structured notebook with multiple chunking strategies already scaffolded.

## Extra Concepts From Lab Source

- semantic chunking
- retrieval-quality testing
- chunk overlap optimization
- hybrid chunking
- metadata preservation
- chunk boundary analysis
- chunk-size distribution analysis

## What I Practiced

- Comparing chunking strategies side by side
- Seeing how preprocessing affects RAG quality
- Thinking about chunk size, overlap, and semantic boundaries
- Recognizing that chunking is a design choice, not a neutral step

## Links to Topic Notes

- [[../RAG/RAG Basics]]
- [[../RAG/RAG Optimization]]
- [[../Prompting/Dynamic Prompting]]

## What To Reuse Later

- Start simple with recursive chunking.
- Use overlap when context may span boundaries.
- Use token-based chunking when model limits matter.
- Use semantic chunking only when retrieval quality justifies extra complexity.
- Inspect chunks manually before building the full RAG pipeline.

## Improvement Ideas

- Add retrieval test questions.
- Compare which chunks are returned for each question.
- Score chunk usefulness.
- Add reranking after retrieval.

## Key Takeaway

Chunking is one of the most important RAG decisions. Bad chunks produce bad retrieval, even if the model is strong.
