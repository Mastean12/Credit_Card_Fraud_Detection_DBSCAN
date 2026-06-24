# Credit Card Fraud Detection Using DBSCAN

## Project Overview

This project applies **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)**, an unsupervised machine learning algorithm, to identify anomalous credit card transactions that may indicate fraudulent activity.

Unlike supervised learning models that require labeled data, DBSCAN detects unusual observations based on data density and clustering behavior.

---

## Business Problem

Financial institutions process thousands of transactions every day. Detecting fraudulent transactions quickly is essential to reduce financial losses and improve security.

Traditional classification models require labeled fraud cases, which are often rare and highly imbalanced. This project explores anomaly detection using DBSCAN to identify suspicious transactions without relying on labels during training.

---

## Dataset

### Credit Card Fraud Detection Dataset

The dataset contains anonymized credit card transactions with:

- Time of transaction
- Transaction amount
- PCA-transformed features (V1–V28)
- Fraud label (`Class`)

Target Variable:

| Class | Meaning |
|---------|---------|
| 0 | Normal Transaction |
| 1 | Fraudulent Transaction |

---

## Project Workflow

### 1. Data Exploration

- Loaded transaction data
- Examined dataset structure
- Checked class distribution
- Verified missing values

### 2. Feature Selection

Selected:

```python
Amount
Time
```

for anomaly detection.

---

### 3. Feature Scaling

Applied StandardScaler to normalize numerical features.

```python
from sklearn.preprocessing import StandardScaler
```

---

### 4. DBSCAN Clustering

Implemented DBSCAN using:

```python
DBSCAN(
    eps=0.5,
    min_samples=5
)
```

Noise points were labeled as:

```text
-1
```

and treated as potential anomalies.

---

### 5. Anomaly Detection

Identified transactions that did not belong to any cluster and classified them as anomalies.

---

### 6. Visualization

Generated scatter plots showing:

- Normal transaction clusters
- Noise points (anomalies)
- Cluster structure

---

## Results

### Dataset Sample

| Metric | Value |
|----------|---------|
| Total Transactions | 10,000 |
| Actual Fraud Cases | 16 |
| Normal Transactions | 9,984 |

---

### DBSCAN Clustering Results

| Cluster | Count |
|----------|---------|
| Cluster 0 | 9,952 |
| Cluster 1 | 7 |
| Noise (-1) | 41 |

---

### Anomalies Detected

```text
41 anomalous transactions detected
```

---

### Comparison with Actual Fraud Labels

| Metric | Value |
|----------|---------|
| Actual Frauds | 16 |
| Detected Anomalies | 41 |
| Frauds Found Among Anomalies | 0 |

---

## Key Findings

- DBSCAN successfully identified unusual transactions.
- The detected anomalies did not correspond to actual fraud cases.
- Using only `Amount` and `Time` was insufficient for capturing fraud behavior.
- Fraud detection typically requires more informative features beyond transaction timing and value.

---

## Lessons Learned

### DBSCAN Strengths

- Detects anomalies automatically
- Does not require labeled data
- Finds clusters of arbitrary shapes
- Useful for exploratory anomaly detection

### Limitations

- Sensitive to parameter selection (`eps`, `min_samples`)
- Struggles with very large datasets
- May fail when fraud patterns resemble normal behavior

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn

---

## Machine Learning Concepts Covered

- Unsupervised Learning
- Clustering
- Density-Based Clustering
- DBSCAN
- Anomaly Detection
- Feature Scaling
- Fraud Detection

---

## Future Improvements

- Use PCA-transformed features (V1–V28)
- Optimize DBSCAN hyperparameters
- Compare with Isolation Forest
- Compare with Local Outlier Factor (LOF)
- Evaluate HDBSCAN for large-scale anomaly detection

---

## Author

Stephen Mariga Ndegwa

Data Analyst | Machine Learning Enthusiast | AI Engineer

Focused on building practical machine learning solutions for business intelligence, fraud detection, predictive analytics, and artificial intelligence applications.
