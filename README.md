# Aircraft Noise Prediction

# Task 1: Trajectory Calculation

## Objective

This module processes and visualizes aircraft trajectory data to analyze **air traffic patterns** and **environmental noise impacts**.

---

## Key Workflow Steps

### 1. Setup and Environment

Installed and imported the following Python libraries:
- `traffic`, `pandas`, `joblib`, `openpyxl`
- Visualization: `matplotlib`, `folium`
- Interactivity: `ipywidgets`

---

### 2. Data Loading

- Loaded aircraft trajectory data from a `.joblib` file (e.g., `data_2022_january.joblib`).
- Converted the loaded data into a `pandas` DataFrame (`df_adsb`).
- Displayed dataset preview and metadata for initial inspection.

---

### 3. Data Preprocessing

- Extracted the **date** from timestamps to enable grouping by flight.
- Sorted the dataset chronologically to maintain correct aircraft movement order.

---

### 4. Flight Identification

- Grouped data by aircraft ID (`icao24`) and date to define **individual flights**.
- Assigned unique `flight_id`s to each grouped flight.
- Aggregated metadata such as **first and last timestamps** for each flight.

---

### 5. Visualization Setup

- Created interactive controls using `ipywidgets` for:
  - Selecting an aircraft (`icao24`)
  - Choosing a date
- Set up for dynamic visualizations:
  - **Folium** for map-based trajectory plots
  - **Matplotlib** for analytical plots

---

## Purpose

Designed to serve as an analytical tool for:
- Evaluating **airspace usage**
- Investigating **noise exposure patterns**
- Supporting further **air traffic analysis**

---

*This README summarizes the logic implemented in the `TrajectoryTask.ipynb` notebook.*



![Simple Graph Plot](Images/SimpleGraph.png)

![3D Plot](Images/3DGraph.png)

![Folium Plot](Images/FoliumGraph.png)





