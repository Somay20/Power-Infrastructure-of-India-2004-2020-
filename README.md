# Power Infrastructure of India: SQL-Based Analysis (2004–2020)

## 📌 Project Overview

This project performs a detailed SQL-based analytical study of India’s power infrastructure from 2004 to 2020. The goal is to uncover regional and state-wise trends in power availability, capacity, and per capita access using clean, structured queries and metrics.

The analysis covers:
- Power availability vs deficit
- Installed capacity growth
- Per capita availability
- Power Index computation
- Regional and state-level efficiency classification

The outcomes support **policy-making**, **resource allocation**, and **performance benchmarking** across Indian states.

---

## 📂 Files Included

### SQL Scripts

| Filename | Purpose |
|----------|---------|
| `Data cleaning.sql` | Preprocessing and cleaning of the `power_infra` dataset (renaming columns, deriving metrics, region tagging) |
| `avg power avb and growth of installed cap.sql` | Calculates average power availability/deficit and installed capacity growth |
| `Efficiency verdict of states.sql` | Categorizes states as Efficient, Moderate, or Inefficient based on availability vs capacity growth |
| `Power Index category.sql` | Computes power index scores for each state and classifies into Low, Medium, High |
| `Power Index comparison.sql` | Compares state-wise power index before and after 2014 to detect improvements or declines |
| `Power Index by region.sql` | Aggregates power index scores at the regional level for `till 2014` and `2014–2020` |

### BI Dashboard

- `Power Infrastructure Dashboard.pbix`: Power BI dashboard visualizing key metrics and regional trends.

### Presentation

- `Power Infrastructure PPT.pdf`: A polished presentation summarizing objectives, methods, key findings, and SQL logic with charts and narratives.

---

## 🧹 Dataset Preparation

- Dataset: `power_infra` (table)
- Initial cleanup:
  - Extracted `fiscal_year` from FY format
  - Renamed columns to include units (`_cr`, `_mw`, `_kwh`)
  - Added `power_deficit_cr` and `deficit_per`
  - Created `region` column manually based on state location

---

## 📈 Key Analyses & Methods

### 1. **Power Deficit Trend (2004–2020)**
```sql
SELECT fiscal_year, 
       ROUND(AVG(power_avb_cr),2), 
       ROUND(AVG(power_deficit_cr),2)
FROM power_infra
GROUP BY fiscal_year;
