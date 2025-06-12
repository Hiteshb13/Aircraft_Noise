# Task 2: Processing Noise Data from Ground-Based Monitors

## Objective

This task focuses on importing, cleaning, and preparing noise measurement data collected from multiple **ground-based aircraft noise monitors**. The cleaned dataset is optimized for further analysis and modeling of **aircraft noise exposure**.

---

## 1. Noise Data Source

- **File:** `Kopie von Fluglärmdaten 2022 (002).xlsx`
- **Sheets:** `MP1` to `MP9` (each representing a unique noise monitoring point)
- **Tool Used:** `pandas.read_excel()` with `sheet_name=[...]` to load all sheets at once

---

## 2. Combining Data

- Merged all sheets using:
  ```python
  combined_noise_df = pd.concat(noise_data.values())
  
---

## 3. Timestamp Handling

Key columns:  
- **ATA/ATD:** Timestamp of noise event (landing or takeoff)
- **Flugzeugtyp:** Aircraft type (used to match with typecode)
- **Max dB(A) or LASmax:** (maximum recorded noise)
- **LAE:** Target variable (Sound Exposure Level)
  
---

 ## 4. Data Cleaning
 
- **Converted ATA/ATD to datetime with:** Format: `%d.%m.%Y %H:%M:%S`
- Localized to "Europe/Berlin"
- Then converted to UTC using `.dt.tz_convert("UTC")`
- Dropped rows with missing or failed timestamps
    
---

 ## 5.Final Step: Saving the Cleaned Noise Data

- `ATA/ATD` (UTC timestamp)
- `Flugzeugtyp` (aircraft type)
- `A/D or phase` (converted to START / LANDUNG)
- `LAE` (the label you predict)
- Any additional filtered or cleaned columns from the original file
 
