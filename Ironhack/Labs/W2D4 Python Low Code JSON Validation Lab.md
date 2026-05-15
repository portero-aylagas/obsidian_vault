# W2D4 Python Low Code JSON Validation Lab

**Source folder**
- `W2D4_python_for_low_code`

**Main files**
- `lab_api_json_validation_template_codex.ipynb`
- `lab_api_json_validation_solution_codex.ipynb`
- `lab_api_json_validation_solution_low_code_refactored_codex.ipynb`
- `data/products.json`
- `data/valid_product.json`
- `data/invalid_product.json`
- `data/malformed.json`

**Lab type**
- JSON validation and refactoring lab
- Template-heavy
- Main value: make model/API data safe enough for automation

## What This Lab Teaches

This lab focuses on validating product data and handling JSON safely.

Workflow:

```text
define schema
-> load JSON
-> validate product data
-> handle invalid/malformed files
-> batch process products
-> refactor validation flow
```

## Techniques Practiced

- Pydantic setup
- product data models
- field validation
- JSON loading
- malformed JSON handling
- valid vs invalid object handling
- batch validation
- result export
- refactoring validation code
- logging

## Important Architecture

```text
raw JSON -> schema model -> validation pass/fail -> cleaned output or error report
```

## Important Code Patterns

### Product model

```python
from pydantic import BaseModel, Field

class Product(BaseModel):
    name: str
    price: float = Field(gt=0)
    category: str
    in_stock: bool
```

Why it matters:
- The schema defines what valid data means.
- This is safer than trusting raw JSON.

### Validate one product

```python
try:
    product = Product(**data)
except ValidationError as error:
    print(error)
```

### Load JSON safely

```python
try:
    with open(path, "r", encoding="utf-8") as f:
        data = json.load(f)
except json.JSONDecodeError:
    print("Malformed JSON")
```

### Batch validation idea

```python
valid_products = []
invalid_products = []

for item in products:
    try:
        valid_products.append(Product(**item))
    except ValidationError as error:
        invalid_products.append({"item": item, "error": str(error)})
```

## What Was Provided

The lab includes templates and solution notebooks. A large amount of structure is provided. The learning value is understanding validation patterns and the refactored version.

## Extra Concepts From Lab Source

- API wrapper classes
- retry logic
- exponential backoff
- standardized error responses
- structured logging
- refactoring generated code
- explicit error context
- independently testable helper functions

## What I Practiced

- Defining data schemas
- Separating valid from invalid records
- Handling broken JSON files
- Refactoring validation into reusable functions
- Thinking about output safety

## Links to Topic Notes

- [[../Engineering/Code Quality and Automation]]
- [[../APIs/OpenAI API]]
- [[../Foundations/Data and Pipeline Foundations]]

## What To Reuse Later

- Use Pydantic when output structure matters.
- Validate before saving or passing data downstream.
- Store validation errors in a clear structure.
- Separate JSON loading, validation, and export logic.

## Improvement Ideas

- Add tests for valid, invalid, and malformed JSON.
- Add stricter field constraints.
- Return standardized success/error payloads.
- Use the same validation pattern for LLM structured outputs.

## Key Takeaway

This lab is important because AI applications often depend on structured data. Validation is what prevents bad generated or external data from breaking the next step in the pipeline.
