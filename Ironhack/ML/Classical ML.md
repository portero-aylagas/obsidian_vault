# Classical ML

**Labs**
- `week-1/submodule-2-ml-neural-networks/m1_06_sklearn.ipynb`

## Main Techniques
- Train/test split
- Feature engineering
- Logistic regression
- Random forest
- KNN regression
- Linear regression
- PCA
- K-means clustering
- Model comparison

## Example
### Train/test split
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

### Scaling
```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

### Classification
```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### Random forest
```python
rf_model = RandomForestClassifier(n_estimators=100, random_state=42)
rf_model.fit(X_train, y_train)
rf_pred = rf_model.predict(X_test)
```

### Regression
```python
from sklearn.linear_model import LinearRegression

reg = LinearRegression()
reg.fit(X_train_house, y_train_house)
predictions = reg.predict(X_test_house)
```

### PCA
```python
pca = PCA(n_components=0.95)
X_pca_transformed = pca.fit_transform(X_scaled)
```

### K-means
```python
kmeans = KMeans(n_clusters=2, random_state=42, n_init=10)
clusters = kmeans.fit_predict(X_kmeans)
```

### Model comparison
```python
metrics = {
    "Model": ["Logistic Regression", "Random Forest"],
    "Accuracy": [
        accuracy_score(y_test, lr_pred),
        accuracy_score(y_test, rf_pred)
    ]
}
```

## What the Notebook Teaches

- Classification predicts categories
- Regression predicts numbers
- PCA reduces dimensionality
- K-means finds groups without labels
- Metrics are needed to compare models

## Key Idea
- Traditional ML introduces the train/evaluate pipeline before later LLM system topics.

## Progression
- Connects to [[Deep Learning]]
