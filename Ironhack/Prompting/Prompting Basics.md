# Prompting Basics

**Labs**
- `week-2/submodule-1-prompt-engineering/m2_02_advanced-prompt-techniques.ipynb`
- `week-2/submodule-1-prompt-engineering/m2_03_prompt_competition.ipynb`

## Main Techniques
- Zero-shot prompting
- One-shot prompting
- Few-shot prompting
- Role prompting
- Emotional prompting
- Chain-of-thought prompting
- Prompt iteration
- Temperature and sampling control
- Reproducibility with `seed`

## Examples

### Zero-shot
Ask directly without giving examples.

```text
Write a haiku about AI.
```

```text
Summarize the concept of overfitting in 2 sentences.
```

### One-shot
Give one example so the model can imitate the format.

```text
Q: What is prompt engineering?
A: Prompt engineering is the practice of designing effective model inputs.

Q: Why is it useful?
A:
```

```text
Classify the sentiment of the sentence.

Sentence: "I love this course."
Sentiment: Positive

Sentence: "This task is frustrating."
Sentiment:
```

### Few-shot
Give several examples to establish a stronger pattern.

```text
Q: Apple
A: Fruit

Q: Carrot  
A: Vegetable

Q: Banana
A:
```

```text
Convert the input into JSON.

Input: Alice, 25, Data Analyst
Output: {"name": "Alice", "age": 25, "job": "Data Analyst"}

Input: Bob, 31, Teacher
Output: {"name": "Bob", "age": 31, "job": "Teacher"}

Input: Clara, 29, Designer
Output:
```

### Role prompting
Give the model a role, specialty, or communication style.

```text
The assistant is a senior data scientist.
Explain overfitting in simple terms.
```

```text
The assistant is a patient Python tutor teaching complete beginners.
Explain what a list is and give one example.
```

### Emotional prompting
Add urgency, importance, or emotional context.

```text
This is important for my presentation tomorrow.
Explain AI ethics clearly and carefully.
```

```text
I am nervous about an interview and need a very clear explanation.
Explain the difference between supervised and unsupervised learning.
```

### Chain-of-thought
Ask the model to reason in steps.

```text
Solve step by step: A train travels 120 km in 2 hours...
```

```text
A shop sells 15 notebooks on Monday and 23 on Tuesday.
How many notebooks were sold in total? Explain step by step.
```

### Prompt iteration
Start with a weak prompt, then improve it by adding constraints.

**Weak prompt**
```text
Explain machine learning.
```

**Improved prompt**
```text
Explain machine learning to a business student.
Use simple language, one real-world example, and keep it under 150 words.
```

### Output length control
Use explicit constraints in the prompt and also use API parameters when needed.

```text
Explain neural networks in exactly 3 bullet points.
```

```text
Describe a pencil in one sentence of no more than 12 words.
```

## Parameter Controls
- `temperature`: more stability vs more creativity
- `top_p`: narrower or broader token sampling
- `max_tokens`: limit output length
- `frequency_penalty`: reduce repetition
- `presence_penalty`: encourage novelty
- `seed`: improve reproducibility

### Low temperature example
More deterministic, useful for extraction and classification.

```python
params = {
    "temperature": 0.0,
    "max_tokens": 100
}
```

### High temperature example
More variation, useful for brainstorming and creative writing.

```python
params = {
    "temperature": 1.3,
    "max_tokens": 150,
    "presence_penalty": 0.5
}
```

### Seed example
Useful when you want more reproducible experiments.

```python
params = {
    "temperature": 0.7,
    "seed": 42
}
```

## Key Idea
- Prompting is empirical.
- You test different phrasing and settings, then compare results.

## Progression
- Builds on [[../APIs/OpenAI API]]
- Leads into [[Dynamic Prompting]]
