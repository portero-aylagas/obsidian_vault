# W1D1 HomeGuard System Lab

**Source folder**
- `W1D1_programming_foundation_exercises`

**Main file**
- `homeguard_system.ipynb`

**Lab type**
- foundations lab
- Scenario-based exercise
- Main value: understand how small Python concepts combine into a mini-system

## What This Lab Teaches

This lab uses a smart home monitoring scenario to practice turning small programming building blocks into a more realistic workflow.

The central idea is:

```text
sensors -> readings -> abnormality checks -> alerts -> system integration
```

## Techniques Practiced

- Dictionaries for structured sensor data
- Lists of sensors
- Conditional logic
- Functions
- Random/simulated sensor readings
- Alert generation
- Classes
- Basic system integration

## Important Architecture

```text
sensor model -> reading simulation -> rule checks -> alert output
```

## Important Code Patterns

### Sensor as dictionary

```python
def create_sensor(sensor_id, location, sensor_type, threshold=None):
    return {
        "id": sensor_id,
        "location": location,
        "type": sensor_type,
        "threshold": threshold
    }
```

Why it matters:
- This is an early example of representing real-world objects with dictionaries.
- Later API responses, JSON payloads, and tool outputs use the same mental model.

### Abnormal reading check

```python
def is_abnormal_reading(sensor, reading_value):
    sensor_type = sensor["type"]

    if sensor_type == "temperature":
        return reading_value < 50 or reading_value > sensor["threshold"]

    if sensor_type == "motion":
        return reading_value is True

    return False
```

Why it matters:
- This shows rule-based logic.
- Later, AI systems often combine rule-based checks with model calls.

### Processing a reading

```python
def process_reading(sensor, reading_value):
    if is_abnormal_reading(sensor, reading_value):
        return f"Alert: abnormal reading in {sensor['location']}"

    return None
```

## What Was Provided

This lab appears to be highly guided. The notebook includes:

- background story
- system requirements
- step-by-step sections
- starter structure
- integration steps

## Extra Concepts From Lab Source

- sensor-data preprocessing
- threshold-based anomaly detection
- system-mode-dependent rules
- alert severity levels
- event logging
- simulation loops
- object-oriented sensor modeling

## What I Practiced

- Reading a scenario and turning it into code
- Creating data structures
- Writing functions with clear inputs and outputs
- Using conditionals for decision logic
- Combining small functions into a larger flow

## Links to Topic Notes

- [[../Foundations/Data and Pipeline Foundations]]
- [[../Engineering/Code Quality and Automation]]

## What To Reuse Later

- Represent entities as dictionaries when the structure is simple.
- Split logic into small functions.
- Keep checking functions separate from processing functions.
- Build systems as a sequence of small steps.

## Improvement Ideas

- Replace random readings with real input data.
- Store alert history for later trend analysis.
- Add tests around threshold edge cases.

## Key Takeaway

This lab is not about AI yet. It is about the Python control flow and data structures needed to later build AI pipelines.
