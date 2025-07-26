# Task 3: Machine Learning – Predicting Test Processing Delays

## Objective

- To predict the delay in days between the creation_date and signout_date of a lab test order using available features in the dataset.

## Problem Formulation

- Target Variable: delay_days = (signout_date - creation_date).days

- Type of Problem: Supervised Regression

- Goal: Build a machine learning model that estimates how many days a lab test will take to be processed based on order details.

## Step 1: Feature Engineering
Create target:

```python
df['delay_days'] = (df['signout_date'] - df['creation_date']).dt.days
```

### Potential Features:

- test_category, sub_category

- test, service

- payment_method

- facility, receiving_centers, processing_centers

- Day-of-week or month from creation_date to detect time patterns:

```python
df['creation_dayofweek'] = df['creation_date'].dt.dayofweek
df['creation_month'] = df['creation_date'].dt.month
```

### Encoding Categorical Variables:

- Use OneHotEncoding or TargetEncoding depending on cardinality.

## Step 2: Model Selection

Try several regression algorithms:

- Baseline: Linear Regression

- Tree-Based Models:

    - Random Forest Regressor

    - Gradient Boosting Regressor (e.g., XGBoost or LightGBM)

## Step 3: Training and Evaluation

- Train-test split (e.g., 80/20)

- Cross-validation for robustness

- Metrics:

    - Mean Absolute Error (MAE)

    - Root Mean Squared Error (RMSE)

    - R² Score

```python
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
```

## Step 4: Model Interpretation

- Use feature importance (from tree models) to understand drivers of delays

- Matplotlib and Seaborn Plots for deeper interpretability

## Expected Impact

- Improve resource planning by predicting delays

- Alert staff/facilities about potential late results

- Identify bottlenecks linked to specific tests, facilities, or time periods