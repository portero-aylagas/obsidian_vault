# W2D4 News Summarizer Lab

**Source folder**
- `W2D4_api_and_integration_patterns_lab`

**Main files**
- `main.py`
- `summarizer.py`
- `llm_providers.py`
- `news_api.py`
- `config.py`
- `test_summarizer.py`

**Lab type**
- API integration and production-patterns lab
- Main value: one of the best examples of code quality, wrappers, fallback, cost tracking, and tests

## What This Lab Teaches

This lab builds a news summarization pipeline using multiple APIs and providers.

Pipeline:

```text
fetch NewsAPI headlines
-> summarize article with OpenAI
-> analyze sentiment with Anthropic
-> fallback if primary provider fails
-> track tokens and cost
-> generate report
```

## Techniques Practiced

- NewsAPI integration
- OpenAI summarization
- Anthropic sentiment analysis
- provider fallback
- provider chaining
- token counting
- cost tracking
- budget checks
- rate limiting
- sequential processing
- async processing
- report generation
- unit testing
- mocking external APIs

## Important Architecture

```text
config.py
Environment variables and model/API settings

news_api.py
Fetches articles from NewsAPI

llm_providers.py
OpenAI, Anthropic, fallback, rate limiting, cost tracking

summarizer.py
Article summarization, sentiment analysis, reporting

main.py
Runtime entry point

test_summarizer.py
Unit tests and mocks
```

## Important Code Patterns

### Cost tracker

```python
class CostTracker:
    def __init__(self):
        self.total_cost = 0.0
        self.requests = []
```

### Track one request

```python
def track_request(self, provider, model, input_tokens, output_tokens):
    input_cost = (input_tokens / 1_000_000) * pricing["input"]
    output_cost = (output_tokens / 1_000_000) * pricing["output"]
    cost = input_cost + output_cost

    self.total_cost += cost
```

Why it matters:
- This turns API usage into measurable cost.
- Cost tracking is required for real apps.

### Provider fallback

```python
try:
    response = self.ask_openai(prompt)
    return {"provider": "openai", "response": response}
except Exception:
    response = self.ask_anthropic(prompt)
    return {"provider": "anthropic", "response": response}
```

Why it matters:
- The system is less fragile because it has a backup provider.

### Rate limiting

```python
elapsed = time.time() - self.openai_last_call

if elapsed < self.openai_interval:
    time.sleep(self.openai_interval - elapsed)
```

### Provider chaining

```text
OpenAI: summarize article
Anthropic: analyze sentiment of summary
```

Why it matters:
- Different models/providers can be assigned different roles.

### Async processing

```python
semaphore = asyncio.Semaphore(max_concurrent)

async def process_with_semaphore(article):
    async with semaphore:
        return await self.summarize_article_async(article)
```

## What Was Provided

This lab likely started from a complete or near-complete template. The important learning is understanding the module boundaries and production patterns.

## Extra Concepts From Lab Source

- response caching
- persistence for processed outputs
- scheduled batch processing
- provider expansion
- trend/topic analytics
- multi-provider chaining
- fallback logic
- rate limiting
- budget checks
- async/concurrent processing

## What I Practiced

- Reading a multi-module codebase
- Understanding wrapper classes
- Handling external APIs
- Adding resilience with fallback
- Tracking usage/cost
- Running and understanding tests

## Links to Topic Notes

- [[../APIs/Multi-Provider]]
- [[../APIs/Reliability Patterns]]
- [[../Engineering/Code Quality and Automation]]
- [[../APIs/OpenAI API]]

## What To Reuse Later

- Keep provider logic in its own module.
- Centralize cost tracking.
- Make fallback behavior explicit.
- Add tests around external API boundaries.
- Use async only when it clearly improves throughput.

## Improvement Ideas

- Replace estimated token counting with direct API usage when available.
- Add retry with jitter around provider calls.
- Add structured output for sentiment analysis.
- Add persistent report export.
- Add clearer typed result objects.

## Key Takeaway

This is a high-value engineering lab. It shows how to move from isolated model calls to a more realistic multi-provider AI service.
