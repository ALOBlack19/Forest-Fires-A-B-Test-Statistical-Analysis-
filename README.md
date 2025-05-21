# 🌲 Forest Fires A/B Test — Statistical Analysis

### 📘 Bonus Assignment — DS: Statistics and Probability  
**Institution**: Cornerstone International Community College of Canada — *CICCC*  
**Student**: Amir Lima Oliveira  
**Date**: May 20th, 2025

---

## 📌 Objective

This project performs an **A/B (two-sample) hypothesis test** using environmental data from Montesinho Natural Park in Portugal. The goal is to determine whether days with **higher FFMC (Fine Fuel Moisture Code)** — an important fire-weather index — result in significantly **larger burned areas** compared to lower FFMC days.

---

## 🗃 Dataset Information

- **Title**: Forest Fires  
- **Source**: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/162/forest+fires)  
- **Description**: Contains meteorological and fire area data collected from January 2000 to December 2003 in Montesinho Natural Park, Portugal.  
- **Attributes**:  
  - Meteorological variables: temperature, humidity, wind, rain  
  - Fire weather indices: FFMC, DMC, DC, ISI  
  - Response variable: **area** (burned forest area in hectares)

---

## 🧪 Methodology

### 1. Data Cleaning

- Removed duplicate rows
- Standardized string values in `month` and `day` columns
- Verified missing values and outliers

### 2. Feature Engineering

- Created a new categorical variable `FFMC_Group` based on the median FFMC:
  - `High` if FFMC >= median
  - `Low` if FFMC < median

### 3. Hypothesis Test

- **Null Hypothesis (H₀)**: There is no significant difference in burned area between high and low FFMC days  
- **Alternative Hypothesis (H₁)**: There is a significant difference in burned area between high and low FFMC days  
- **Significance level**: α = 0.05  
- **Test used**: Welch’s t-test (appropriate for unequal variances)

### 4. Assumption Checks

- Distribution of burned area is **skewed**, violating normality assumption
- Used **Levene’s test** to check variance equality (result supported Welch’s test choice)

### 5. Confidence Interval Calculation

Calculated a **95% confidence interval** for the difference in means between the two groups.

---

## 📊 Key Results

| Metric                  | Value                      |
|-------------------------|----------------------------|
| T-statistic             | 1.134                      |
| P-value                 | 0.2575                     |
| 95% Confidence Interval | (-4.35, 16.20)             |
| Conclusion              | ❌ Fail to reject H₀        |

> **Interpretation**: The difference between groups was not statistically significant. FFMC, although important for fire behavior, did not explain the burned area in this dataset.

---

## 🧠 Discussion & Limitations

- The **burned area data is highly skewed**, with many small fires and a few large events
- Small sample size for rain events limited the ability to control for weather
- The dataset covers a single region and time period (2000–2003 in Montesinho)
- Assumptions of parametric tests may be violated due to the nature of the data

---

## 💡 Future Work

- Compare additional fire-weather indices (e.g., ISI, DMC)
- Apply **non-parametric tests** (e.g., Mann–Whitney U) to overcome skewed distributions
- Integrate **real-world weather data** via Meteostat API for historical validation
- Use **bootstrapping** to estimate robust confidence intervals
- Build **predictive models** using regression or ensemble algorithms

---

## 📁 Files Included

| File Name                         | Description                              |
|----------------------------------|------------------------------------------|
| `forestfires.csv`                | Raw dataset from UCI repository          |
| `forest_fire_analysis.ipynb`     | Jupyter Notebook with full analysis      |
| `Forest_Fire_AB_Test_Report.pdf` | Final academic report                    |
| `requirements.txt`               | Python dependencies                      |
| `README.md`                      | Project overview (this file)             |

---

## ⚙️ Dependencies

To install all required libraries, run:


pip install -r requirements.txt

--- 

## 📬 Contact

Amir Lima Oliveira
📍 Vancouver, BC, Canada
🔗 LinkedIn: https://www.linkedin.com/in/amirloliveira/

---

## 📚 Credits

P. Cortez and A. Morais.
"A Data Mining Approach to Predict Forest Fires using Meteorological Data."
In J. Neves, M. F. Santos and J. Machado Eds., New Trends in Artificial Intelligence, Proceedings of the 13th EPIA 2007 - Portuguese Conference on Artificial Intelligence, December, Guimaraes, Portugal, pp. 512–523, 2007.
APPIA, ISBN-13 978-989-95618-0-9
Available at: http://www.dsi.uminho.pt/~pcortez/fires.pdf

## License
This dataset is licensed under a Creative Commons Attribution 4.0 International (CC BY 4.0) license.

This allows for the sharing and adaptation of the datasets for any purpose, provided that the appropriate credit is given.

```bash