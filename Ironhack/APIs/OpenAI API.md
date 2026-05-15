# OpenAI API

**Labs**
- `week-1/submodule-3-generative-ai-apis/m1_08_generative-ai.ipynb`
- `W1D5_compare_whisper_vs_google_STT`
- `W2D5_rag_with_open_ai`
- `W4D3_arxiv_n8n_notion_research_summarizer`

## Main Techniques
- `client.responses.create`
- `client.chat.completions.create`
- Reasoning models
- Instructions
- Temperature
- Multi-turn context
- Image input
- Structured outputs
- Moderation-style classification

## Examples

### Client setup
```python
import os
from openai import OpenAI
from dotenv import load_dotenv

load_dotenv()

client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))
```

### Basic generation
```python
response = client.responses.create(
    model="gpt-4o",
    input="What is machine learning?"
)

print(response.output_text)
```

### Reasoning-style request
```python
response = client.responses.create(
    model="gpt-5",
    reasoning={"effort": "low"},
    input="Solve this step by step: If a train travels 120 km in 2 hours, how long for 300 km?"
)
```

### Temperature
Use higher temperature when you want more variety.

```python
response = client.responses.create(
    model="gpt-4o",
    input="Write a creative story about AI.",
    temperature=0.9
)
```

Use low temperature when you want stable output.

```python
response = client.responses.create(
    model="gpt-4o",
    input="Classify this as positive, negative, or neutral: I love it.",
    temperature=0
)
```

### Instructions
```python
response = client.responses.create(
    model="gpt-4o",
    instructions="You are a creative writing assistant. Write in a poetic style.",
    input="Write a short story about AI."
)
```

### Messages format
```python
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Explain neural networks in one sentence."}
    ]
)
```

### Developer and user roles
```python
response = client.responses.create(
    model="gpt-5",
    input=[
        {"role": "developer", "content": "Talk like a pirate."},
        {"role": "user", "content": "Are semicolons optional in JavaScript?"}
    ]
)
```

### Multi-turn context
```python
response1 = client.responses.create(
    model="gpt-4o-mini",
    input="My name is Alice"
)

response2 = client.responses.create(
    model="gpt-4o",
    input="What's my name?",
    previous_response_id=response1.id
)
```

### Image input
```python
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {
            "role": "user",
            "content": [
                {"type": "text", "text": "What's in this image?"},
                {"type": "image_url", "image_url": {"url": "https://example.com/cat.jpg"}}
            ]
        }
    ]
)
```

### Structured extraction
```python
from pydantic import BaseModel

class CalendarEvent(BaseModel):
    name: str
    date: str
    participants: list[str]
```

### Research paper extraction
```python
class ResearchPaperExtraction(BaseModel):
    title: str
    authors: list[str]
    abstract: str
    keywords: list[str]
```

### Moderation-style classification
```python
class ContentCompliance(BaseModel):
    is_violating: bool
    category: str | None = None
    explanation: str | None = None
```

### Parsed structured output idea
```python
completion = client.chat.completions.parse(
    model="gpt-4o-2024-08-06",
    messages=[
        {"role": "system", "content": "Extract the event information."},
        {"role": "user", "content": "Alice and Bob are going to a science fair on Friday."}
    ],
    response_format=CalendarEvent
)

event = completion.choices[0].message.parsed
```

## What the Notebook Teaches

- Use direct text generation for simple tasks
- Use instructions or roles to control behavior
- Use multi-turn context when the model needs memory
- Use structured outputs when software needs fields
- Use image input for multimodal tasks
- Use classification schemas for moderation-like tasks

## Key Idea
- This is the first direct LLM application layer in the course.
- Most later topics build on these calls and response patterns.

## Progression
- Leads into [[../Prompting/Prompting Basics]]
- Supports [[../APIs/Reliability Patterns]]
- Supports [[../APIs/Multi-Provider]]
