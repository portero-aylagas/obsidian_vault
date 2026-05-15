# Reliability Patterns

**Labs**
- `week-2/submodule-3-api-integration/m2_01_api-fundamentals.ipynb`
- `W4D1_langchain_guardrails`
- `W4D4_n8n_error_handling_and_scheduled_workflows`

## Main Techniques
- Exponential backoff
- Jitter
- Retry strategy
- Circuit breaker
- Combined production client

## Examples

### Exponential backoff
```python
delay = base_delay * (2 ** attempt)
```

Example delay pattern:

```text
Attempt 0: 1 second
Attempt 1: 2 seconds
Attempt 2: 4 seconds
Attempt 3: 8 seconds
```

### Jitter
```python
delay = random.uniform(0, capped_delay)
```

Why jitter matters:

```text
Without jitter:
Client A retries at 2 seconds
Client B retries at 2 seconds
Client C retries at 2 seconds

With jitter:
Client A retries at 1.3 seconds
Client B retries at 2.7 seconds
Client C retries at 1.9 seconds
```

### Retry loop
```python
for attempt in range(max_retries):
    try:
        return api_call()
    except Exception:
        time.sleep(delay)
```

## Circuit Breaker States
- Closed
- Open
- Half-open

### Circuit breaker idea
```python
if failure_count >= threshold:
    state = "open"
```

```python
if state == "open" and enough_time_has_passed:
    state = "half-open"
```

### Circuit breaker call pattern
```python
if circuit_breaker.can_call():
    try:
        result = api_call()
        circuit_breaker.record_success()
    except Exception:
        circuit_breaker.record_failure()
else:
    raise Exception("Circuit is open")
```

### Combined production client
- Retry handles temporary failures
- Circuit breaker handles persistent failures
- Together they prevent retry storms and repeated bad calls

### Practical failure examples
- Timeout: retry may help
- Rate limit: retry with delay may help
- Service outage: circuit breaker should stop repeated calls
- Invalid API key: retry will not help

## Key Idea
- A working API call is not enough.
- You also need retry control and graceful failure handling.

## Progression
- Builds on [[OpenAI API]]
- Connects to [[Multi-Provider]]
