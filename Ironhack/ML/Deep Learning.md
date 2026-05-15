# Deep Learning

**Labs**
- `week-1/submodule-2-ml-neural-networks/m1_04_deep-learning.ipynb`
- `W1D3_build_simple_neural_network`

## Main Techniques
- Feedforward neural network
- Dense layers
- ReLU
- Softmax
- MNIST classification
- Transformer zero-shot classification

## Example
### MNIST neural network
```python
model = keras.Sequential([
    layers.Dense(512, activation='relu', input_shape=(784,)),
    layers.Dense(256, activation='relu'),
    layers.Dense(10, activation='softmax')
])
```

```python
model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)
```

### Training
```python
history = model.fit(
    x_train,
    y_train,
    epochs=10,
    batch_size=128,
    validation_split=0.2
)
```

### Evaluation
```python
test_loss, test_accuracy = model.evaluate(x_test, y_test, verbose=0)

print(f"Test accuracy: {test_accuracy:.4f}")
print(f"Test loss: {test_loss:.4f}")
```

### Zero-shot transformer
```python
from transformers import pipeline

classifier = pipeline(
    "zero-shot-classification",
    model="facebook/bart-large-mnli"
)
```

```python
result = classifier(
    "This movie is fantastic!",
    ["positive", "negative", "neutral"]
)
```

### Batch classification
```python
texts = [
    "This movie is fantastic!",
    "I hate waiting in long lines.",
    "The service was acceptable."
]

results = classifier(texts, ["positive", "negative", "neutral"])
```

## What the Notebook Teaches

- Neural networks learn from labeled examples
- Transformers can classify text without task-specific training data
- Zero-shot classification uses candidate labels supplied at runtime

## Key Idea
- This topic bridges classical ML and modern foundation-model usage.

## Progression
- Builds on [[Classical ML]]
- Leads into [[../APIs/OpenAI API]]
