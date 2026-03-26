
**Author:** Amantle Michelle Makati  
**Date:** March 2026

This Dataset was from Kaggle the link is below: 
https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series
---

# Title: A Calibrated Deep Learning Framework for Regional Mortality Projections and Policy Intervention Analysis

## 📌 Overview & Objectives
Public health officials often face "reporting noise" and extreme volatility when tracking pandemic trends. Traditional models frequently fail to capture the non-linear momentum of an outbreak, leading to delayed policy responses. 

**The primary objectives of this project were:**
* To develop a comparative analytical pipeline tracking COVID-19 progression across high-impact US regions.
* To move beyond static counts by analyzing the **velocity of cases** and the specific **lag in fatalities**.
* To provide actionable insights—such as 30-day forecasts and policy simulations—to inform the timing and duration of localized interventions.

Dataset Features & Schema
Feature,Description
UID,Unique numeric identifier for each geographic row.
"iso2, iso3, code3",Standardized 2-character and 3-character ISO country codes.
FIPS,Federal Information Processing Standard code used to identify US counties.
Admin2,The specific County-level administrative unit.
Province_State,The State or Province of the reported data.
Country_Region,"The name of the Country or Region (e.g., US)."
"Lat, Long_",Geographic coordinates (Latitude and Longitude) for mapping.
Combined_Key,"A unique string identifier combining the Admin2, State, and Country names."
Date Columns,Daily time-series columns containing the raw counts of confirmed cases or deaths.

## ⚙️ Project Workflow
1.  **Data Preprocessing:** Cleaning raw CDC/JHU data, handling missing values (NaN to 0), and clipping outliers.
2.  **Exploratory Data Analysis (EDA):** Using ACF/PACF diagnostics to identify a consistent 7-day weekly reporting cycle.
3.  **Benchmarking:** Training a baseline ARIMA model against an advanced RNN-LSTM architecture.
4.  **Uncertainty Calibration:** Implementing **MC Dropout** to generate reliability intervals (PICP).
5.  **Deployment:** Generating a Regional Risk Dashboard and simulating policy interventions (e.g., Lockdowns).

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Deep Learning:** TensorFlow / Keras
* **Data Science:** Pandas, NumPy, Scikit-learn, Statsmodels
* **Visualization:** Matplotlib, Seaborn

## 📊 Model Selection & Evaluation Metrics
The project utilized a dual-metric approach to compare the "Accuracy" of the guess against the "Reliability" of the uncertainty bands.

| Metric | ARIMA (Baseline) | RNN-LSTM (Proposed) | Improvement |
| :--- | :---: | :---: | :---: |
| **MAPE (Error)** | 141.93% | **101.45%** | **40.48%** |
| **PICP (Coverage)** | N/A | **42.64%** | Reflected high volatility |

## 📋 Regional Impact Dashboard
A resource-focused dashboard was implemented to provide a "jargon-free" signal to policymakers based on raw projected totals.

| State | Projected Daily Deaths (Avg) | Status | Action |
| :--- | :---: | :---: | :--- |
| **Arizona** | 0.38 | 🟢 LOW | Surveillance |
| **California** | 0.38 | 🟢 LOW | Surveillance |
| **Florida** | 0.38 | 🟢 LOW | Surveillance |
| **Illinois** | 0.38 | 🟢 LOW | Surveillance |
| **New York** | 0.38 | 🟢 LOW | Surveillance |

## 🛡️ Policy Intervention Simulation
The project includes a **"What-If" engine** that simulates a **50% Case Reduction**. By comparing the base forecast against the intervention line, the model quantifies **Potential Deaths Averted**.

---

## 💻 How to Run the Project

This project is contained within a single Jupyter Notebook (`.ipynb`). You can run it easily using **Google Colab** (cloud-based) or **VS Code** (local-based).

### **Option 1: Google Colab (Recommended for Beginners)**
1.  Upload the `.ipynb` file to your Google Drive.
2.  Right-click the file and select **Open with > Google Colaboratory**.
3.  **Upload Data:** If the notebook requires a CSV file, click the **Folder icon** on the left sidebar and drag your dataset into the "content" area.
4.  **Install Dependencies:** Run the first cell or a new cell with:
    `!pip install tensorflow pandas numpy matplotlib seaborn statsmodels scikit-learn`
5.  Go to the top menu and select **Runtime > Run all**.

### **Option 2: VS Code (For Local Development)**
1.  **Open Folder:** Open VS Code and open the folder containing your project.
2.  **Set Up Environment:** Open a terminal in VS Code (`Ctrl + ~`) and install the required libraries:
    `pip install jupyter tensorflow pandas numpy matplotlib seaborn statsmodels scikit-learn`
3.  **Select Kernel:** Open the `.ipynb` file. In the top-right corner, click **Select Kernel** and choose your Python installation.
4.  **Run:** Click **Run All** at the top of the notebook. Ensure your data file is in the same folder as the notebook.
