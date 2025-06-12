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
- Added a new column typecode in adsb_df by mapping this dictionary
---

### 3. Preprocess Noise Data

Renamed key columns for clarity:
- `ATA/ATD` : `noise_time`
- `A/D` : `phase`
- `Abstand [m]` : `distance_m`
- `Höhenwinkel [°]` : 	`angle_deg`
- `Höhe [ft]` : `altitude_ft`

- Retained relevant fields: TLASmax, T10, LAE
- Converted noise_time to a datetime format

  ---
### 4. Matching Trajectory and Noise Records
  - 4.1  Timestamp Alignment
    
- Converted `adsb_df["timestamp"]` and `noise_time` to `datetime`
- Ensured both DataFrames had valid timestamps
- Dropped rows with missing `timestamp` or `typecode`

---

### 5. Final Output

The matched dataset contains:

- Timestamp-aligned and type-matched records
- Noise features (LAE, TLASmax, etc.)
- Corresponding trajectory metadata (position, altitude, etc.)

---

### This matching task needs to be repeated for each month's ADS-B data file (e.g., data_2022_april.joblib, data_2022_may.joblib, etc.).
- Once all monthly datasets are processed and matched, they can be combined into a single comprehensive dataset for model training and evaluation.
