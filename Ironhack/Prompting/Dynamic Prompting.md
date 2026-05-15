# Dynamic Prompting

**Labs**
- `week-3/00_dynamic_prompting.ipynb`

## Main Techniques
- Build prompts at runtime
- Inject variables
- Inject tone and format
- Inject external context
- Build conversation memory dynamically

## Examples

### Dynamic prompt
The prompt is built from a variable instead of being hardcoded.

```python
question = "What is machine learning?"
prompt = f"Answer concisely: {question}"
```

```python
topic = "photosynthesis"
prompt = f"Explain {topic} for a 12-year-old student."
```

### Style injection
You can inject presentation rules such as tone, length, and audience.

```python
def ask_with_style(question, tone="professional", max_sentences=2):
    return (
        f"Answer in a {tone} tone. "
        f"Keep the answer to {max_sentences} sentences. "
        f"Question: {question}"
    )
```

```python
def build_prompt(topic, audience="beginner", format_type="bullet points"):
    return (
        f"Explain {topic} for a {audience}. "
        f"Use {format_type}."
    )
```

### Input injection
The user input is inserted directly into the prompt template.

```python
user_question = "What is overfitting?"
prompt = f"Answer the following question clearly: {user_question}"
```

### Context injection
External information is inserted into the prompt so the model can answer using that material.

```python
prompt = f"""
Use the following context to answer the question.

Context:
{context}

Question:
{question}
"""
```

```python
context = "Paris is the capital of France. It is known for the Eiffel Tower."
question = "What is the capital of France?"

prompt = f"""
Use the context below to answer.

Context:
{context}

Question:
{question}
"""
```

### Template + variables pattern
Separate the fixed instruction from the changing data.

```python
template = "Summarize the following article in {length} sentences:\n\n{article}"

prompt = template.format(
    length=3,
    article="Machine learning is a field of AI that learns patterns from data..."
)
```

### Conversation memory
- Build the `messages` list turn by turn.
- The prompt becomes accumulated history.

```python
messages = [
    {"role": "system", "content": "You are a concise tutor."},
    {"role": "user", "content": "What is Python?"},
    {"role": "assistant", "content": "Python is a programming language."},
    {"role": "user", "content": "What are its main use cases?"}
]
```

### Why this matters for applications
- A chatbot uses dynamic prompting because every user message is different.
- A support bot injects customer data dynamically.
- A RAG system injects retrieved context dynamically.
- An agent injects tool results dynamically.

## Key Idea
- Prompts are just strings.
- Once you understand that, you can build them from user input, database content, retrieved chunks, or previous messages.

## Progression
- Extends [[Prompting Basics]]
- Becomes the foundation for [[../RAG/RAG Basics]]
