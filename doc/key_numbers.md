# Key Numbers (English) – Quick Reference

The full report for this project is written in Portuguese, so I kept this short page in English to make the main numbers easy to find for anyone reviewing the work.

All figures below come from **real, public, anonymized administrative data** published by the Portuguese National Health System (SNS) via the SNS Transparency Portal (2013–2025). This is a reference page (not a full report).



## 1) Data coverage (what we worked with)
**Datasets (SNS Transparency Portal):**
- *Atividade de Internamento Hospitalar* (Hospital admissions activity)
- *Ocupação do Internamento* (Bed occupancy / capacity indicators)

**Size (after loading the public datasets):**
- Admissions dataset: **16,734 rows**, **7 columns**
- Occupancy dataset: **7,126 rows**, **7 columns**

These are aggregated administrative records (by year / institution / region / specialty), not survey data.



## 2) Data quality notes (why we were careful)
Both datasets include a small number of missing values in key numeric fields (e.g., admissions, inpatient days, occupancy variables).

We did **not** replace nulls with zero during ETL, because in this context:
- **0** can mean “real zero activity”
- **null** means “no record / missing information”

Instead, we added simple “data missing” flags during ETL and handled display cases later when needed. This avoids distorting totals and averages.



## 3) Hospital activity over time (admissions)
- Admissions were **quite stable between 2015–2019**, around **~5 million episodes/year**.
- **2020 shows a clear drop**, aligned with COVID impact and reduced scheduled activity.
- Following years show a **gradual recovery**.
- The value for **2025 is lower due to incomplete data** in the dataset.

Across the period analyzed, the total volume of discharge episodes used in the analysis is **over 52 million**.
(Important: this refers to episodes, not unique patients.)



## 4) Average length of stay (by specialty type)
Typical patterns in the data:
- **Surgical** stays are shorter: around **~6 days**
- **Medical** stays are longer: around **~9–10 days**
- **Other beds** show the longest stays: around **~14–15 days**

These averages are stable over time and were calculated without treating missing values as zero.



## 5) Admissions split by specialty type (rough distribution)
- **Surgical:** ~**50%**
- **Medical:** ~**46%**
- **Other beds:** ~**4%**

So the vast majority of admissions are concentrated in medical + surgical activity.



## 6) Regional pressure (combining demand + bed use)
To compare regions more fairly, we used a **relative pressure index** (normalized), combining:
- admissions volume (episodes)
- bed-days / occupancy-related use

Key takeaway:
- **Lisbon and Vale do Tejo (LVT)** is the highest-pressure region in the comparison set (pressure index reported as **~1.95**).
- **North** follows with a similar high-pressure profile.
- **Centre** is moderate; **Algarve** and **Alentejo** are lower.

This is meant as a relative comparison across regions, not a clinical risk score.



## 7) Regional share of total bed occupancy (2013–2025)
The regional distribution is stable over time:
- **LVT:** ~**36%**
- **North:** ~**34%**
- **Centre:** ~**21%**
- **Algarve:** ~**4%**
- **Alentejo:** ~**4%**

Together, LVT + North account for ~70% of total bed occupancy share in the period.



## 8) Specialty with highest care burden (last 3 years)
Using total inpatient days (bed-days) for the last 3 years:
- **Medical specialty** has the highest total care burden
- **Surgical** is second (more frequent, but shorter stays)
- **Other beds** are smaller in volume, but can include long stays



## 9) Forecasting (exploratory)
We used simple linear regression as an introductory/exploratory approach (trend direction, not precise forecasting).

- Forecast for **2026 admissions**: **~3,794,926**
  (noting that 2025 appears incomplete and affects the trend)
- Forecast for **2026 “Lotação Praticada”**: **~466.46**
  (as reported in the project output; interpreted as a stable trend indicator)

These forecasts are included to demonstrate basic predictive techniques and support planning discussions, not to produce operational predictions.
