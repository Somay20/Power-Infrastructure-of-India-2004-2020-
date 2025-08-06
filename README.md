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

## 📊 Summary of Analysis

### 🔍 Trend Insights
- Revealed spikes in power deficit during **2006–08** and **2011–12**.
- Significant improvements post-2013 due to policy changes and grid integration.

---

### ⚡ 2. Installed Capacity Growth
- Used **CTEs** to compute installed capacity growth from first recorded year to 2020.
- **Top contributors**: Gujarat, Maharashtra, Karnataka — due to industrial demand and renewable investments.

---

### 🧮 3. Efficiency Verdicts
States were classified based on the balance between installed capacity growth and power availability growth:

- 🟢 **Efficient**: Availability kept up with capacity expansion.
- 🟡 **Moderate**: Moderate alignment between availability and capacity.
- 🔴 **Inefficient**: High capacity growth with relatively low availability growth.

---

### 📈 4. Power Index Computation
Power Index was calculated using weighted growth scores:

| Metric                  | Weight |
|------------------------|--------|
| Installed Capacity      | 30%    |
| Power Availability      | 30%    |
| Per Capita Availability | 40%    |

**Steps:**
1. Calculated % growth of each metric.
2. Applied **min-max normalization** to scale between 0 and 1.
3. Used weighted average to compute **Power Index**.

**Time Periods Compared:**
- Till 2014
- 2014–2020

---

### 🌐 5. Regional Trends
- **South and Northeast** regions showed the **strongest growth post-2014**.
  
  ✅ **South**: Led by **Tamil Nadu** and **Karnataka** via renewables (wind, solar), and central support (UDAY, One Nation One Grid).

  ✅ **Northeast**: Benefited from **DDUGJY** and **NERPSIP** schemes improving transmission and rural electrification.

---

## 🔑 Key Insights

- ⚡ **Bihar** showed the **highest increase** in power availability (~425%).
- ☀️ **Karnataka** & **Tamil Nadu** emerged as solar and wind leaders.
- 🏝️ **Andaman & Nicobar** had a massive jump in index due to focused electrification drives.
- 🏙️ **Delhi** and **Gujarat** experienced **index declines post-2014**, possibly due to early saturation.

---

## 🛠️ Tools Used
- **SQL (MySQL Workbench)** — Complex queries, CTEs, growth calculations
- **Power BI** — Interactive visualizations and dashboards
- **Google Slides** — Final presentation deck

---

## 👤 Author

**Somay Agarwal**  
_Data Enthusiast | Problem Solver | Aspiring Consultant_

---

## 📎 Notes

- **Per capita metrics** use **2011 Census** population data.
- **Telangana** bifurcation (June 2014) was accounted for in data and analysis.


