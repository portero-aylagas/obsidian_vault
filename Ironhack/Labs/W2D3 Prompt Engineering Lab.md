# W2D3 Prompt Engineering Lab

**Source folder**
- `W2D3_prompt_engineering`

**Main file**
- `prompt_engineering_lab.ipynb`

**Lab type**
- Prompt engineering practice lab
- Main value: treat prompts as testable artifacts, not one-off text

## What This Lab Teaches

This lab starts with simple prompts and improves them through testing.

Workflow:

```text
create baseline prompt
-> run it multiple times
-> observe failures
-> refine prompt
-> compare outputs
```

## Techniques Practiced

- zero-shot prompting
- sentiment analysis prompting
- product description prompting
- data extraction prompting
- repeated runs
- inconsistency detection
- prompt failure diagnosis
- prompt refinement
- temperature control
- seed/reproducibility ideas

## Important Architecture

```text
task -> prompt variant -> model call -> output comparison -> prompt revision
```

## Important Code Patterns

### OpenAI helper function

```python
def call_openai(
    prompt,
    system_message="You are a helpful assistant.",
    temperature=0.7,
    max_tokens=None,
    seed=None
):
    params = {
        "model": MODEL,
        "messages": [
            {"role": "system", "content": system_message},
            {"role": "user", "content": prompt}
        ],
        "temperature": temperature
    }
```

Why it matters:
- The helper makes experiments repeatable.
- You can change temperature, max tokens, and seed without rewriting the whole API call.

### Repeated prompt testing

```python
responses = []

for i in range(10):
    response = call_openai(prompt, temperature=0.7)
    responses.append(response)
```

Why it matters:
- LLM output can vary.
- A prompt that works once may fail on repeated runs.

### Baseline prompt idea

```text
Analyze the sentiment of this customer review:
"The product arrived late but the quality is excellent."
```

### Refined prompt idea

```text
Classify the sentiment as one of:
- positive
- negative
- mixed
- neutral

Return only valid JSON:
{
  "sentiment": "...",
  "reason": "..."
}

Review:
"The product arrived late but the quality is excellent."
```

## What Was Provided

The notebook is structured with project scenario, task areas, goals, and step-by-step exercises. Much of the workflow is provided, but the learning comes from modifying and comparing prompts.

## Extra Concepts From Lab Source

- temperature experimentation
- meta-prompting for prompt improvement
- multi-task prompting
- prompt evaluation frameworks
- format-adherence checks
- output consistency testing
- systematic failure analysis
- technique selection for prompt patterns

## What I Practiced

- Seeing prompt failures through repetition
- Adding constraints to reduce ambiguity
- Comparing vague prompts with specific prompts
- Understanding that extraction tasks need stricter formatting

## Links to Topic Notes

- [[../Prompting/Prompting Basics]]
- [[../Prompting/Dynamic Prompting]]
- [[../APIs/OpenAI API]]

## What To Reuse Later

- Always test important prompts more than once.
- Define allowed labels for classification tasks.
- Ask for strict output formats when downstream code depends on the answer.
- Keep prompt experiments organized so you can compare versions.

## Improvement Ideas

- Store prompt versions in separate files.
- Add an evaluation table for each run.
- Use Pydantic/structured outputs for extraction tasks.
- Add an LLM-as-judge rubric once evaluation is introduced later.

## Key Takeaway

The main lesson is that prompt engineering is empirical. You improve prompts by testing, observing failures, and refining constraints.
