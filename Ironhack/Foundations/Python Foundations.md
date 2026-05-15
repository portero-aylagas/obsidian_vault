# Python Foundations

**Labs**
- `week-1/submodule-1-ai-basics-python/m1_04_python.ipynb`

## Main Techniques
- Variables and data types
- Lists
- Dictionaries
- Sets
- Conditionals
- Loops
- Functions
- Classes
- `pandas`
- JSON parsing
- Extracting fields from nested API responses

## Examples

### Variables and strings
```python
name = "Python"
age = 30
message = f"Hello, {name}"
```

### Lists
```python
fruits = ["apple", "banana", "orange"]
first_fruit = fruits[0]
fruits.append("grape")
```

### Dictionaries
```python
student = {
    "name": "Alice",
    "age": 25,
    "course": "AI Bootcamp"
}

name = student["name"]
age = student.get("age")
```

### Conditionals
```python
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
else:
    grade = "C"
```

### Loops
```python
for fruit in fruits:
    print(fruit)

for i in range(5):
    print(i)
```

### Functions
```python
def greet(name):
    return f"Hello, {name}!"
```

### Classes
```python
class Student:
    def __init__(self, name, age, course):
        self.name = name
        self.age = age
        self.course = course
```

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

