# Multi-Provider

**Labs**
- `week-2/submodule-3-api-integration/m2_02_integration-patterns.ipynb`

## Main Techniques
- Multiple providers
- Provider comparison
- Provider fallback
- Provider chaining
- Token usage tracking
- Budget management
- Streaming budget monitoring
- External data enrichment
- Environment-based configuration

## Example
### Basic provider wrapper shape
```python
def ask_openai(prompt, model="gpt-4o-mini"):
    response = openai_client.responses.create(
        model=model,
        input=prompt
    )

    return {
        "provider": "openai",
        "text": response.output_text,
        "usage": response.usage
    }
```

### Fallback
```python
result = ask_with_fallback(
    "Explain RAG simply",
    primary="openai",
    secondary="anthropic"
)
```

Fallback logic:

```python
try:
    return ask_openai(prompt)
except Exception:
    return ask_anthropic(prompt)
```

### Provider comparison
Ask the same question to two providers and compare the outputs and token usage.

```python
openai_answer = ask_openai("Explain machine learning in one sentence.")
anthropic_answer = ask_anthropic("Explain machine learning in one sentence.")
```

### Provider chaining
Use one provider to generate content and another to review it.

```python
draft = ask_openai("Write a paragraph about RAG.")
review = ask_anthropic(f"Review this paragraph and suggest improvements:\n\n{draft}")
```

### Token budget tracking
Use the API's returned usage data rather than estimating manually.

```python
usage = response["usage"]
input_tokens = usage["input_tokens"]
output_tokens = usage["output_tokens"]
```

### Budget manager idea
```python
class TokenBudgetManager:
    def __init__(self, daily_budget):
        self.daily_budget = daily_budget
        self.spent = 0

    def can_spend(self, estimated_cost):
        return self.spent + estimated_cost <= self.daily_budget
```

### Streaming budget idea
- Stream output progressively
- Stop or warn if usage exceeds the allowed budget

### External data enrichment
```python
weather_data = fetch_weather_data("Berlin")
prompt = f"Use this weather data to answer the question: {weather_data}"
```

### Environment configuration
```python
class Config:
    def __init__(self, environment="development"):
        self.environment = environment
        self.model = "gpt-4o-mini" if environment == "development" else "gpt-4o"
```

## What the Notebook Teaches

- Do not depend on one provider for every task
- Compare cost and quality
- Add fallback for resilience
- Track real usage from API responses
- Add external data before prompting when current data matters

## Key Idea
- This shifts the course from one-model thinking to system-level thinking.

## Progression
- Builds on [[OpenAI API]]
- Builds on [[Reliability Patterns]]
- Leads into [[../Frameworks/LangChain]]
