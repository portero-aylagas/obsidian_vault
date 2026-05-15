# Data and Pipeline Foundations

**Labs**
- `week-1/submodule-1-ai-basics-python/m1_04_python.ipynb`

## Main Techniques
- `pandas`
- JSON parsing
- Extracting fields from nested API responses
- Structured data handling
- Small reusable processing steps
- API-style response inspection

## Examples

### Basic pandas
```python
import pandas as pd

data = {
    "name": ["Alice", "Bob", "Charlie"],
    "age": [25, 30, 35],
    "score": [85, 90, 88]
}

df = pd.DataFrame(data)
print(df["age"].mean())
```

### JSON parsing
```python
import json

json_string = '{"name": "Alice", "age": 25}'
data = json.loads(json_string)
print(data["name"])
```

### Nested API response extraction
```python
generated_text = response_data["choices"][0]["message"]["content"]
```

## Why It Matters
- Every later notebook depends on these foundations.
- Prompts, chat histories, tool outputs, and retrieved documents are all handled with Python data structures.

## Progression
- Supports [[../APIs/OpenAI API]]
- Supports [[../Engineering/Code Quality and Automation]]
