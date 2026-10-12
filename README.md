# CH20 – Air Quality Insight

**DS Sprint 2026 | U23AD491 – Data Science | Skill Based Assessment 2**
**Name:** Pradeep P  **Reg No:** 722824104175

## Problem Statement
How do weather, location and time relate to changes in air quality? The goal is to find which stations, periods and conditions need monitoring priority.

## Dataset
> The raw files were not provided, so the data was **generated programmatically (synthetic)** in the notebook. It is hourly for 2024 across 8 stations, and the 5 data-quality issues from the question were built in on purpose.

| File | Key fields |
|---|---|
| air_quality.csv | timestamp, station, PM2.5, PM10, NO2, AQI |
| stations.csv | location, land-use type |
| weather.csv | wind, temperature, humidity, rain |
| traffic.csv | traffic volume, peak flag |
| calendar.csv | weekday, holiday, season |

**Cleaned dataset:** 70,272 rows × 18 columns, 0 missing values.

## Repository Structure
```
├── data/        raw CSVs, cleaned_air_quality.csv, selected_features.csv
├── notebook/    CH20_Round2_Air_Quality_EDA_FE.ipynb
├── excel/       CH20_Air_Quality_Analysis.xlsx
├── ppt/         CH20_Air_Quality_Insight_Pitch.pptx
└── README.md
```

## Work Done
- **Round 2 – EDA and Feature Engineering (Python):** cleaning, merging, EDA, feature engineering, feature selection, PCA and modelling.
- **Round 3 – Excel:** formulas, pivot tables and pivot charts, plus a summary sheet.
- **Round 4 – Pitch:** 10-slide business presentation.

## Data Cleaning
- 914 duplicate readings removed
- Station names unified (44 spellings → 8)
- 9,646 missing sensor readings filled, 1,078 weather and traffic gaps filled
- 184 impossible values removed, 51 extreme values capped (IQR)

## Key Findings
| Question | Result |
|---|---|
| Worst station | Ukkadam (mean AQI 190.6); best is Vadavalli (67.2) |
| Peak time | 8 AM (AQI 181.2), second peak at 6 PM |
| Wind vs PM2.5 | Correlation −0.55, so calm air means higher PM2.5 |
| Traffic | Peak hours AQI 163.2 vs 130.7 off-peak |
| Rain | PM2.5 falls 41.7% (70.0 → 40.8) |
| Peak season | Winter (mean AQI 212.3), worst month February |

## Model
Target is AQI, using a time-based 80/20 split. PM2.5, PM10 and NO2 were excluded as inputs to avoid leakage.

| Model | RMSE | R² |
|---|---|---|
| Linear Regression | 51.14 | 0.620 |
| Random Forest | 40.46 | 0.762 |
| Random Forest + lag feature | 33.44 | 0.838 |

## Recommendations
1. Prioritise monitoring at Ukkadam, Singanallur and Kuniyamuthur during rush hours.
2. Issue alerts when wind is low and traffic is at peak.
3. Start winter action plans before December each year.

## Tools
Python (Pandas, NumPy, Matplotlib, Seaborn, scikit-learn), Microsoft Excel, PowerPoint.
