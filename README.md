# Hospital Efficiency Analysis – Portuguese National Health System (SNS)

## Overview
In this project, we analyzed **real public healthcare data** from the Portuguese National Health System (SNS) between 2013 and 2025.

The goal was to understand how hospital beds are used over time and to see which regions and medical areas are under more pressure.

This project was developed as part of a postgraduate program in Analytics and Data Science, using official public data published by the SNS.



## Questions We Looked At
- How has hospital activity changed over the years?
- Are hospital beds being used efficiently?
- Which regions are under more pressure?
- Which medical specialties use the most bed-days?
- What trends can help with capacity planning?



## Data Sources
All data used in this project is **real, public, and anonymized**.
The datasets come from the official SNS Transparency Portal and represent real hospital activity in Portugal:
- Hospital admissions data  
- Hospital bed occupancy data  



## Data Preparation
Data preparation was done in **Power Query**, with a strong focus on data quality:

- We checked and fixed data types
- We cleaned text fields to avoid broken joins
- We reviewed missing values in key metrics
- Missing values were **not replaced with zero**, because zero has real meaning in healthcare data
- We added simple flags to keep track of incomplete records

These choices helped avoid wrong averages and misleading conclusions.



## Data Model
We built a simple **star schema** model in **Power BI**.

**Fact tables**
- Hospital admissions
- Bed occupancy

**Dimensions**
- Date
- Region
- Institution
- Location
- Medical specialty (for admissions)

This model allows us to analyze hospital activity and capacity together.



## Key Metrics
- Total hospital admissions
- Average length of stay
- Bed occupancy rate
- Total bed-days
- Relative hospital pressure (normalized)

We used a normalized pressure metric to compare regions in a fair way, even when their size is very different.



## Key Insights
- Hospital activity in Portugal has been mostly stable over the last decade.
- Big changes in the data are mainly linked to external events, such as COVID-19.
- Looking only at total volumes can be misleading; relative pressure gives a clearer picture.
- Lisbon and North regions are under higher pressure compared to other regions.
- Medical specialties use more bed-days mainly because patients stay longer, not because there are more admissions.



## Forecasting
We did a simple exploratory forecast using linear regression.

The goal was not to make precise predictions, but to understand the general direction of the trends.  
The results suggest recovery to normal levels rather than strong growth.



## Limitations & Next Steps
- The data is aggregated by year, so seasonality is not visible
- Forecasting is simple and exploratory
- No external variables were included

With more detailed data, this analysis could be improved.



## Tools Used
- Power BI
- Power Query
- DAX
- Python (pandas, scikit-learn, matplotlib)



## Team & My Role
This project was developed together with **Rita Noronha** as part of a postgraduate course.

**My main contributions were:**
- Data preparation and cleaning in Power Query
- Handling missing values and data quality checks
- Building the data model in Power BI
- Defining metrics and indicators
- Interpreting the results and insights

A full academic report in Portuguese is available for reference.
