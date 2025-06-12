# Task 3: Matching Trajectory (ADS-B) and Noise Data

##  Objective

The primary goal of this task is to **match aircraft trajectory data (ADS-B)** with corresponding **ground-based noise measurements**, creating a unified dataset. This dataset serves as a foundation for applying **machine learning models** to predict aircraft noise levels.

---

##  Workflow Overview

### 1. Load and Preprocess ADS-B Data

- **File:** `data_2022_april.joblib`
- Loaded the joblib file and converted it into a `pandas` DataFrame (`adsb_df`)
- Standardized identifiers:
  - Converted `icao24` values to lowercase
  - Extracted unique aircraft IDs for mapping

---

### 2. Aircraft Type Mapping

- Used the `traffic` library to retrieve aircraft **type codes** based on `icao24`
- Created a dictionary `icao_to_typecode` mapping:
  ```python
  {icao24: typecode}

---

### 3. Noise Data Preprocessing
