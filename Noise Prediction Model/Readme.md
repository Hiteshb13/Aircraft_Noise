# Aircraft Noise Prediction Using Random Forest Regressor

This project focuses on predicting the **Effective Perceived Noise Level (LAE)** from aircraft flyovers using a full year's worth of ADS-B and noise monitoring data.

---

## Dataset Overview

- **Data Sources**: ADS-B trajectory data matched with noise monitoring station data.
- **Structure**:
  - Each flight is identified by an `event_id` and contains multiple time steps (~10–20 rows per flight).
  - Features include:
    - Flight dynamics: `latitude`, `longitude`, `altitude`, `groundspeed`, etc.
    - Acoustic metrics: `Leq`, `LASmax`, `LAE`
    - Metadata: `runway`, `AzB-Klasse`, `MP`, `phase`, etc.

---

## Objective

To develop a machine learning model that accurately estimates the **LAE** per flight event using historical ADS-B and noise data.

---

##  Methodology

### 1. Data Preprocessing
- Concatenated monthly datasets covering January to December.
- Mapped categorical features (e.g. `phase`: `Landung` → 1, `Start` → 0).
- Applied one-hot encoding to `Runway`, `MP`, and `AzB-Klasse`.
- Scaled numerical features using `StandardScaler`.

### 2. Feature Selection
- Selected relevant base features and encoded dummy variables.
- Grouped data by `event_id`, extracted fixed-length sequences per flight, and flattened them into single feature vectors.

### 3. Model Training
- Utilized a **RandomForestRegressor** with the following settings:
  - `n_estimators=100`
  - `max_depth=7`
  - `min_samples_leaf=2`
- Split data into 80% training and 20% testing sets.
- Evaluated predictions against ground truth `LAE`.

---

##  Results

| Metric     | Value   |
|------------|---------|
| **R² Score** | 0.9085   | ------| ~0.91   |
| **RMSE**     | 1.3594   | ------| ~1.36   |
| **MSE**      | 1.8480   |
| **MAE**      | ~1.0–1.4 |

- The model generalizes well across unseen test data.
- **Actual vs Predicted LAE** plots confirm strong alignment.
- Learning curve indicates effective training with minimal overfitting.

---

##  Visualizations

- **Scatter plot** of actual vs predicted LAE values.

---

## Potential Extensions

- Integrate other models like XGBoost or LightGBM.
- Try variable-length sequence modeling or temporal networks.
- Deploy as an API or integrate with live aircraft tracking systems.

---

## Tools & Libraries

- Python, Pandas, NumPy
- Scikit-learn (Random Forest, Metrics)
- TensorFlow/Keras (for MLP comparison)
- Matplotlib, Seaborn

---

## Contact

For questions or collaborations, feel free to reach out or open an issue in this repository.
