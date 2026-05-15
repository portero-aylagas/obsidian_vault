# W1D3 Neural Network Lab

**Source folder**
- `W1D3_build_simple_neural_network`

**Main files**
- `lab_source/Ironhack Student Portal .html`

**Lab type**
- guided / self-guided
- Main value: understand the mechanics of training a simple neural network and see how pre-trained models transfer perception skills to another data type

## What This Lab Teaches

This lab connects two ideas:

```text
raw image data -> neural network -> binary classification
pre-trained model -> audio input -> transferred classification ability
```

The important learning is not just dog-vs-cat classification. It is seeing how model training differs from using an already-trained model.

## Techniques Practiced

- CIFAR-10 image loading
- binary class filtering
- image normalization
- train/test splitting
- dense neural-network architecture
- activation functions
- binary classification loss
- training and validation curves
- model-weight export
- pre-trained transformer inference for audio classification
- transfer learning intuition

## Important Architecture

```text
CIFAR-10
-> filter dog/cat classes
-> normalize pixels
-> flatten image tensors
-> Dense layers
-> sigmoid output
-> binary prediction
```

The second part shifts from training to inference:

```text
audio input
-> pre-trained transformer model
-> predicted audio class
```

## Important Code Patterns

### Normalize image pixels

```python
x_train = x_train.astype("float32") / 255.0
x_test = x_test.astype("float32") / 255.0
```

### Define a small binary classifier

```python
model = keras.Sequential([
    layers.Flatten(input_shape=(32, 32, 3)),
    layers.Dense(128, activation="relu"),
    layers.Dense(1, activation="sigmoid")
])
```

### Compile for binary classification

```python
model.compile(
    optimizer="adam",
    loss="binary_crossentropy",
    metrics=["accuracy"]
)
```

## What Was Provided

The lab source provides a guided structure, code templates, and explicit parameters to experiment with. The workspace currently contains the HTML source but no separate submitted notebook or script for this extra lab.

## What I Practiced

- reading basic neural-network training code
- connecting input shape to model architecture
- distinguishing training from inference
- interpreting accuracy and loss
- saving trained model artifacts
- understanding why pre-trained models are useful

## Links to Topic Notes

- [[../ML/Deep Learning]]
- [[../ML/Classical ML]]

## What To Reuse Later

- Normalize numeric inputs before training.
- Keep architecture, compile settings, and training settings conceptually separate.
- Use validation performance to detect whether training is actually improving generalization.
- Reach for pre-trained models when the goal is application behavior, not model research.

## Improvement Ideas

- Replace the dense image classifier with a small CNN.
- Track overfitting with train vs validation curves.
- Compare scratch training with transfer learning.
- Add confusion-matrix analysis for dog/cat errors.

## Key Takeaway

The lab is a bridge between model intuition and practical AI work: you see how a simple model learns, then why most application work often starts from pre-trained models.
