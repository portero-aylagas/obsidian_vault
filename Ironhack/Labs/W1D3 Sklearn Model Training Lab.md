# W1D3 Sklearn Model Training Lab

**Source folder**
- `W1D3_sklearn_model_training_and_evaluation`

**Main files**
- `sklearn_model_training_and_evaluation.ipynb`
- `churn_prediction.ipynb`
- `breast_cancer_prediction.py`
- `churn_prediction.py`
- `conclusions_model_churn.md`

**Lab type**
- Guided and unguided sklearn lab
- Main value: understand classical ML workflow and model evaluation

## What This Lab Teaches

This lab practices two supervised learning problems:

```text
breast cancer prediction -> guided classification
customer churn prediction -> more business-oriented classification
```

## Techniques Practiced

- loading datasets
- exploratory data analysis
- preprocessing
- train/test split
- feature scaling
- KNN classification
- experimenting with `k`
- evaluating predictions
- writing model conclusions

## Important Architecture

```text
dataset -> preprocessing -> train/test split -> model training -> evaluation
```

## Important Code Patterns

### Train/test split

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    stratify=y,
    random_state=42
)
```

Why it matters:
- `stratify=y` preserves class proportions.
- This is useful when classes are imbalanced.

### Scaling before KNN

```python
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

Why it matters:
- KNN depends on distances.
- Features with larger numeric ranges can dominate if not scaled.

### KNN model

```python
knn = KNeighborsClassifier(n_neighbors=5)
knn.fit(X_train_scaled, y_train)

y_pred = knn.predict(X_test_scaled)
```

### Evaluate classification

```python
print(classification_report(y_test, y_pred))
print(confusion_matrix(y_test, y_pred))
```

### Experiment with `k`

```python
for k in range(1, 21):
    model = KNeighborsClassifier(n_neighbors=k)
    model.fit(X_train_scaled, y_train)
    score = model.score(X_test_scaled, y_test)
    scores.append(score)
```

## What Was Provided

The breast cancer exercise is guided. The churn exercise appears more open-ended and asks for analysis and recommendations.

## Extra Concepts From Lab Source

- feature scaling
- feature importance analysis
- model comparison
- ROC/AUC evaluation
- precision-recall curves
- cross-validation
- learning curves
- classification threshold optimization
- business impact analysis

## What I Practiced

- Applying the same ML workflow to different datasets
- Handling real-world columns in churn data
- Comparing model settings
- Translating model results into business recommendations

## Links to Topic Notes

- [[../ML/Classical ML]]
- [[../Foundations/Data and Pipeline Foundations]]

## What To Reuse Later

- Always split before evaluating.
- Fit scalers only on training data.
- Compare several model settings instead of trusting the first model.
- Write conclusions that connect metrics to user/business impact.

## Improvement Ideas

- Track experiments in a table instead of only notebook outputs.
- Compare KNN against a simple baseline model.
- Add cross-validation for more stable evaluation.

## Key Takeaway

This lab teaches the train/evaluate mindset. Even when later labs use LLMs, the habit of testing and comparing outputs stays important.
