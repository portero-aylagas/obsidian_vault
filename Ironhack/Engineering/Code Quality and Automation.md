# Code Quality and Automation

**Labs**
- `week-2/submodule-2-python-low-code/m2_02_automation-with-python.ipynb`
- `W4D1_langchain_guardrails`
- `W4D4_n8n_error_handling_and_scheduled_workflows`

## Main Techniques
- Helper functions
- Refactoring
- Separation of concerns
- API wrappers
- Standardized response objects
- Retry handling inside wrappers
- Unit testing with `pytest`
- Edge-case testing
- Test-driven development

## Examples

### Messy function before refactoring
The notebook starts from code that does too many things in one place.

```python
def process_users(users_data):
    results = []

    for user in users_data:
        if '@' not in user.get('email', ''):
            continue

        name = user.get('name', '').strip().title()
        age = datetime.now().year - user.get('birth_year', 2000)

        results.append({
            "name": name,
            "email": user["email"],
            "age": age
        })

    return results
```

Problem:
- validation, formatting, age calculation, and loop logic are mixed together
- harder to test
- harder to reuse
- harder to change safely

### Helper function
Break a big task into one small reusable unit.

```python
def is_valid_email(email):
    return bool(email and '@' in email)
```

### Formatting helper
```python
def format_name(name):
    return name.strip().title() if name else ""
```

### Age helper
```python
from datetime import datetime

def calculate_age(birth_year):
    if not birth_year:
        return None

    return datetime.now().year - birth_year
```

### Refactored user processing
After extracting helpers, the main function becomes easier to read.

```python
def process_users(users_data):
    results = []

    for user in users_data:
        email = user.get("email", "")

        if not is_valid_email(email):
            continue

        results.append({
            "name": format_name(user.get("name")),
            "email": email,
            "age": calculate_age(user.get("birth_year"))
        })

    return results
```

### Refactoring
Move logic out of one large function into smaller focused functions.

```python
def make_api_request(url, headers, params, timeout=10):
    return requests.get(url, headers=headers, params=params, timeout=timeout)
```

```python
def parse_user_data(response_json):
    return {
        "name": response_json.get("name"),
        "email": response_json.get("email")
    }
```

### API function before refactoring
This style works in a notebook but becomes fragile in a real app.

```python
def process_api_data(api_url, api_key, user_id):
    headers = {"Authorization": f"Bearer {api_key}"}
    params = {"user_id": user_id}

    response = requests.get(api_url, headers=headers, params=params)
    response.raise_for_status()

    data = response.json()
    return {
        "id": data["id"],
        "name": data["name"],
        "email": data["email"]
    }
```

Better structure:
- one function builds headers
- one function makes the request
- one function parses data
- one function coordinates the workflow

### Coordinator function after refactoring
```python
def process_api_data(api_url, api_key, user_id):
    headers = build_auth_headers(api_key)
    params = {"user_id": user_id}
    response = make_api_request(api_url, headers, params)
    return parse_user_data(response.json())
```

### API wrapper
Instead of repeating direct model calls everywhere, wrap them.

```python
class OpenAIWrapper:
    def __init__(self, client, model="gpt-4o-mini"):
        self.client = client
        self.model = model

    def chat(self, prompt):
        return self.client.responses.create(
            model=self.model,
            input=prompt
        )
```

### Standardized response object
The notebook introduces the idea of returning predictable response shapes.

```python
from dataclasses import dataclass
from typing import Any

@dataclass
class APIResponse:
    success: bool
    data: Any | None = None
    error: str | None = None
    usage: dict | None = None
```

### Wrapper with error handling
```python
class OpenAIWrapper:
    def __init__(self, client, model="gpt-4o-mini"):
        self.client = client
        self.model = model

    def chat(self, prompt):
        try:
            response = self.client.responses.create(
                model=self.model,
                input=prompt
            )

            return APIResponse(
                success=True,
                data=response.output_text,
                usage=getattr(response, "usage", None)
            )
        except Exception as error:
            return APIResponse(
                success=False,
                error=str(error)
            )
```

### Using the wrapper
```python
ai = OpenAIWrapper(client)
response = ai.chat("What is Python?")

if response.success:
    print(response.data)
else:
    print(response.error)
```

### Why wrappers matter
- API key handling is centralized
- model selection is centralized
- retries can be added in one place
- errors have a consistent shape
- tests can mock the wrapper instead of calling the real API

### Unit testing
```python
def test_is_valid_email():
    assert is_valid_email("user@example.com") is True
    assert is_valid_email("invalid-email") is False
```

### Edge-case testing
```python
def test_format_name_empty():
    assert format_name("") == ""
    assert format_name(None) == ""
```

### Testing a processing function
```python
def test_process_users_skips_invalid_email():
    users = [
        {"name": "alice", "email": "alice@example.com", "birth_year": 2000},
        {"name": "bob", "email": "invalid-email", "birth_year": 1995}
    ]

    result = process_users(users)

    assert len(result) == 1
    assert result[0]["name"] == "Alice"
```

### Testing wrapper success with a fake client
```python
class FakeResponse:
    output_text = "Hello"
    usage = {"input_tokens": 5, "output_tokens": 2}

class FakeResponses:
    def create(self, model, input):
        return FakeResponse()

class FakeClient:
    responses = FakeResponses()

def test_openai_wrapper_success():
    wrapper = OpenAIWrapper(FakeClient())
    response = wrapper.chat("Say hello")

    assert response.success is True
    assert response.data == "Hello"
```

### Testing wrapper failure
```python
class FailingResponses:
    def create(self, model, input):
        raise RuntimeError("API unavailable")

class FailingClient:
    responses = FailingResponses()

def test_openai_wrapper_failure():
    wrapper = OpenAIWrapper(FailingClient())
    response = wrapper.chat("Say hello")

    assert response.success is False
    assert "API unavailable" in response.error
```

### TDD loop
The notebook introduces the basic test-driven development rhythm.

```text
Red: write a failing test
Green: write the simplest code that passes
Refactor: improve the code while tests stay green
```

### What to test
- valid inputs
- invalid inputs
- empty values
- missing fields
- API success
- API failure
- edge cases
- output shape

## Why It Matters
- AI code should not stay as one-off notebook code.
- These techniques turn experiments into maintainable software.
- This is one of the most important topics if you want to build real AI applications instead of isolated demos.

## Progression
- Builds on [[../Foundations/Data and Pipeline Foundations]]
- Supports [[../APIs/Reliability Patterns]]
