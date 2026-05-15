# W1D2 Titanic JSON Lab

**Source folder**
- `W1D2_Data_Manipulation_JSON_Handling`

**Main file**
- `titanic_analysis.ipynb`

**Lab type**
- Data manipulation and JSON handling lab
- Main value: connect tabular data work with structured JSON output

## What This Lab Teaches

This lab uses Titanic passenger data to practice:

```text
load data -> inspect data -> engineer features -> analyze groups -> export JSON -> validate JSON
```

## Techniques Practiced

- CSV loading with `pandas`
- missing-value analysis
- feature engineering
- grouping and comparison
- custom classes
- JSON export
- JSON validation

## Important Architecture

```text
CSV data -> cleaning and feature engineering -> analysis -> JSON export -> validation
```

## Important Code Patterns

### Load CSV

```python
df = pd.read_csv(CSV_FILE)

print(df.shape)
print(df.head())
```

Why it matters:
- This is the basic pattern for starting any tabular-data project.

### Missing-value analysis

```python
missing_count = df[col].isna().sum()
missing_percent = (missing_count / len(df)) * 100
```

Why it matters:
- Before modeling or exporting data, you need to know what is incomplete.

### Feature engineering

```python
df_features["FamilySize"] = df_features["SibSp"] + df_features["Parch"] + 1
```

Why it matters:
- Feature engineering converts raw columns into more useful signals.
- This idea appears again in classical ML labs.

### Class-based representation

```python
class Passenger:
    def __init__(self, passenger_id, name, survived):
        self.passenger_id = passenger_id
        self.name = name
        self.survived = survived
```

Why it matters:
- This is an early step from raw dictionaries/dataframes into explicit domain objects.

### JSON validation

```python
with open(JSON_FILE, "r", encoding="utf-8") as f:
    json_data = json.load(f)

print(json_data.keys())
```

Why it matters:
- Later AI systems often produce JSON.
- You need to verify that saved JSON can actually be loaded and used.

## What Was Provided

This appears to be a guided lab with a structured notebook and clear stages.

## Extra Concepts From Lab Source

- advanced feature engineering
- title extraction
- ratio features
- derived categorical features
- distribution statistics
- correlation analysis
- exploratory data visualization
- JSON Schema validation

## What I Practiced

- Turning raw data into cleaner data
- Creating derived columns
- Comparing groups
- Exporting structured data
- Validating output files

## Links to Topic Notes

- [[../Foundations/Data and Pipeline Foundations]]
- [[../ML/Classical ML]]
- [[../Engineering/Code Quality and Automation]]

## What To Reuse Later

- Always inspect data before transforming it.
- Validate exported JSON by loading it again.
- Keep feature engineering steps explicit and readable.
- Use classes only when they clarify the domain.

## Improvement Ideas

- Add a repeatable validation schema for exported records.
- Separate notebook exploration from reusable transformation functions.
- Add tests for missing-value and type-conversion edge cases.

## Key Takeaway

This lab connects data analysis with structured output. That is useful later for LLM extraction, Pydantic validation, and API payload design.
