# RAG Basics

**Labs**
- `week-3/rag_intro.ipynb`
- `week-3/rag_openai.ipynb`
- `W2D5_rag_with_open_ai`

## Main Techniques
- Document loading
- Chunking
- Embeddings
- Vector databases
- Similarity search
- Retrieval-augmented prompting
- Comparison with vs without RAG

## Core Pipeline
1. Load documents
2. Split into chunks
3. Create embeddings
4. Store them in a vector database
5. Retrieve relevant chunks
6. Insert them into the prompt
7. Ask the model to answer

## Examples

### Loading documents
The LangChain notebook uses document loaders such as `PyPDFLoader`.

```python
from langchain_community.document_loaders import PyPDFLoader

loader = PyPDFLoader("path/to/document.pdf")
documents = loader.load()
```

The direct OpenAI notebook shows the same idea without LangChain by creating sample documents manually.

```python
documents = [
    {"page_content": "Machine learning learns patterns from data."},
    {"page_content": "Deep learning uses neural networks with many layers."}
]
```

### Chunking
```python
chunk_size = 500
chunk_overlap = 50
```

### Recursive chunking
```python
from langchain_text_splitters import RecursiveCharacterTextSplitter

text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=500,
    chunk_overlap=50
)

chunks = text_splitter.split_documents(documents)
```

### Manual chunking idea
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

### Embeddings
```python
embeddings = OpenAIEmbeddings(model="text-embedding-3-small")
```

### Direct embedding call
```python
embedding_response = openai_client.embeddings.create(
    model="text-embedding-3-small",
    input="Machine learning enables systems to learn from data."
)

vector = embedding_response.data[0].embedding
```

### Vector store creation
```python
vectorstore = PineconeVectorStore.from_documents(
    documents=chunks,
    embedding=embeddings,
    index_name=index_name
)
```

### Direct Pinecone upsert idea
```python
vectors = [
    {
        "id": "chunk-1",
        "values": embedding,
        "metadata": {"text": chunk_text}
    }
]

index.upsert(vectors=vectors)
```

### Similarity search
```python
results = vectorstore.similarity_search(query, k=2)
```

### Similarity search with scores
```python
results_with_scores = vectorstore.similarity_search_with_score(query, k=2)

for doc, score in results_with_scores:
    print(score, doc.page_content)
```

### RAG prompt structure
```text
Context:
{retrieved_docs}

Question:
{question}
```

### Direct OpenAI-style retrieval
```python
query_embedding = embed_query(query, openai_client)
matches = index.query(vector=query_embedding, top_k=2, include_metadata=True)
```

### Formatting retrieved documents
```python
def format_docs(docs):
    return "\n\n".join(doc.page_content for doc in docs)
```

### Complete RAG function shape
```python
def answer_with_rag(question):
    docs = vectorstore.similarity_search(question, k=2)
    context = format_docs(docs)

    prompt = f"""
    Use the context to answer the question.

    Context:
    {context}

    Question:
    {question}
    """

    return llm.invoke(prompt)
```

### Without RAG vs with RAG
Without RAG:

```python
llm.invoke("What does the internal policy say about refunds?")
```

With RAG:

```python
answer_with_rag("What does the internal policy say about refunds?")
```

The second version can use retrieved private or external documents.

## Two Approaches in the Labs
- LangChain-based RAG
- Direct OpenAI + Pinecone RAG

## Key Idea
- RAG = retrieval + dynamic prompting

## Progression
- Builds on [[../Prompting/Dynamic Prompting]]
- Extended by [[RAG Optimization]]
- Related to [[../Frameworks/LangChain]]
