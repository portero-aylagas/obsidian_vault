# W1D4 Product Listing Vision Lab

**Source folder**
- `W1D4_api_calling_chatgpt`

**Main files**
- `api_calling_chatgpt.ipynb`
- `api_calling_chatgpt_2.ipynb`
- `conclusions.md`
- `outputs/products_listings.json`
- `outputs/token_tracking.json`

**Lab type**
- API and multimodal generation lab
- Main value: connect product metadata and images to structured LLM output

## What This Lab Teaches

This lab builds a product-listing generator.

Pipeline:

```text
load fashion dataset -> inspect product data -> encode image -> build prompt -> call model -> parse listing -> save JSON
```

## Techniques Practiced

- OpenAI client setup
- Hugging Face dataset loading
- product metadata inspection
- PIL image handling
- base64 image encoding
- vision input to model
- product listing prompt design
- batch processing multiple products
- JSON parsing
- Responses API refactor
- Pydantic structured output
- token tracking

## Important Architecture

```text
product data -> image encoding -> vision prompt -> structured output -> usage tracking
```

## Important Code Patterns

### Load product dataset

```python
dataset = load_dataset(
    "ashraq/fashion-product-images-small",
    split="train[:100]"
)
```

### Convert PIL image to base64

```python
def pil_to_base64(img):
    buffer = BytesIO()
    img.save(buffer, format="PNG")
    return base64.b64encode(buffer.getvalue()).decode("utf-8")
```

Why it matters:
- Vision models need the image in a request-friendly format.

### Multimodal message shape

```python
messages = [
    {
        "role": "user",
        "content": [
            {"type": "text", "text": prompt},
            {
                "type": "image_url",
                "image_url": {
                    "url": f"data:image/png;base64,{image_base64}"
                }
            }
        ]
    }
]
```

### Product listing schema idea

```python
class ProductListing(BaseModel):
    title: str
    description: str
```

### Save generated listings

```python
products_df.to_json(
    "outputs/products_listings.json",
    orient="records",
    indent=2
)
```

## What Was Provided

This appears to be a guided lab with substantial notebook structure and refactoring prompts.

## Extra Concepts From Lab Source

- multimodal prompting
- prompt parameterization
- A/B testing for generated outputs
- token and cost tracking
- batch-processing cost estimation
- prompt optimization for cost control
- output quality scoring
- automated output validation
- regeneration based on quality thresholds
- platform-specific structured export
- API error handling
- secret management with environment variables

## What I Practiced

- Calling a multimodal model
- Turning product data into prompts
- Comparing prompt-based JSON with API-enforced structured output
- Recognizing why raw generated strings are fragile
- Tracking token usage

## Links to Topic Notes

- [[../APIs/OpenAI API]]
- [[../Engineering/Code Quality and Automation]]
- [[../Prompting/Prompting Basics]]

## What To Reuse Later

- Use schemas instead of asking for "JSON" only in the prompt.
- Store parsed structured data, not only raw model text.
- Track token usage early when processing many rows.
- Separate image encoding from model-calling logic.

## Improvement Ideas

- Add retry handling for failed model calls.
- Save raw and parsed outputs for debugging.
- Compare prompts with a small evaluation set before batch runs.

## Key Takeaway

This lab is a practical bridge from "call an LLM" to "build a repeatable AI data pipeline with multimodal input and structured output."
