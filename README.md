# Analyzing Chronic Diseases and Behavioral Factors in the U.S.

An exploratory public-health analytics project examining chronic diseases and behavioral risk factors across the United States, with a primary focus on diabetes prevalence, healthcare access, socioeconomic disparities, and comorbidities.

## Project Overview

Chronic diseases such as diabetes, asthma, arthritis, depression, cancer, cardiovascular disease, and chronic obstructive pulmonary disease are major causes of mortality and healthcare expenditure in the United States. Diabetes alone affects an estimated 38 million Americans, while another 98 million have prediabetes, creating a substantial health and economic burden.

This project combines large-scale CDC health datasets to investigate where chronic diseases are most prevalent, which behavioral and socioeconomic factors are associated with diabetes, and how public-health resources could be directed toward the communities with the greatest need.

## Research Questions

- Which states and territories have the highest prevalence of diabetes?
- How is diabetes associated with income and access to healthcare?
- What barriers prevent people with diabetes from receiving timely medical care?
- Which chronic and mental-health conditions commonly occur alongside diabetes?
- How do smoking, alcohol use, food insecurity, and adverse childhood experiences vary geographically?
- What targeted interventions could reduce diabetes-related health disparities?

## Data Sources

### Behavioral Risk Factor Surveillance System (BRFSS)

The CDC's 2022 BRFSS dataset contains responses from more than **450,000 people** across all 50 states, Washington, D.C., Guam, Puerto Rico, and the U.S. Virgin Islands. The survey includes more than **250 questions** covering health conditions, behaviors, demographics, healthcare access, and social determinants of health.

[CDC BRFSS 2022 Data and Documentation](https://www.cdc.gov/brfss/annual_data/annual_2022.html)

### Chronic Disease Indicators (CDI)

The CDC's Chronic Disease Indicators dataset provides standardized state- and territory-level measures across 115 public-health indicators, including diabetes, cardiovascular disease, cancer, mental health, tobacco use, alcohol use, nutrition, and healthcare access.

[CDC U.S. Chronic Disease Indicators](https://data.cdc.gov/Chronic-Disease-Indicators/U-S-Chronic-Disease-Indicators/hksd-2xuw/about_data)

The analysis primarily uses 2022 data so that the BRFSS and CDI reporting periods align. Selected CDI visualizations cover 2019-2022 to show changes over time.

## Data Engineering

The BRFSS data was distributed in SAS Transport (`.xpt`) format. It was converted to CSV with Python, uploaded to Google Cloud Storage, and imported into BigQuery alongside the CDI dataset.

The workflow included:

- Removing index, empty, unrelated, and redundant columns
- Reviewing more than 300 BRFSS fields with a BigQuery-hosted data dictionary
- Preserving meaningful survey nulls to avoid distorting population aggregates
- Assigning a refusal code to a small number of missing general-response fields
- Confirming respondent IDs were unique
- Standardizing state identifiers across BRFSS and CDI
- Removing CDI fields with no relevant analytical value
- Linking individual survey responses to state-level chronic-disease indicators

## Analytical Approach

- BigQuery SQL for large-scale aggregation and state-level comparisons
- Python and Pandas for data preparation and result handling
- Plotly choropleth maps for geographic and multi-year analysis
- Demographic segmentation by income, age, gender, and geography
- Comparison of diabetic and general populations
- Comorbidity analysis across multiple chronic conditions
- Examination of healthcare access and social determinants of health

## Key Findings

### Geographic disparities

- Diabetes prevalence was highest in Guam and Puerto Rico among U.S. territories.
- Arkansas, Alabama, Mississippi, and West Virginia were among the states with the highest prevalence.
- Southern states consistently showed elevated diabetes risk.
- Washington, D.C., Colorado, Vermont, Montana, and Utah recorded comparatively low prevalence.
- Several Southern and Southwestern states experienced notable increases between 2019 and 2022.

### Income and healthcare access

- Regions with larger low-income populations often showed higher diabetes prevalence.
- Puerto Rico, Guam, West Virginia, and Louisiana demonstrated the combined burden of economic disadvantage and high diabetes prevalence.
- Low-income people with diabetes faced greater barriers to preventive care, medication, transportation, and routine medical visits.
- Younger adults with diabetes were especially vulnerable to delaying care because of cost.

### Mental health and comorbidities

- Depression frequently occurred alongside diabetes, reinforcing the connection between physical and mental health.
- Diabetes was also examined alongside asthma, cardiovascular disease, kidney disease, COPD, and cancer.
- States with poor mental-health indicators often had a substantial burden of multiple chronic conditions.

### Behavioral and social factors

- Smoking and alcohol-related behaviors varied considerably by state and age group.
- Food insecurity, difficulty paying bills, utility disruptions, and transportation barriers compounded health risks for people with diabetes.
- Adverse childhood experiences may contribute to long-term chronic-disease risk and warrant earlier intervention.
- Participation in diabetes education was insufficient in several high-risk states.

## Recommendations

- Expand insulin subsidies and affordable medication programs for low-income patients.
- Increase insurance coverage for preventive screenings, routine care, and diabetes management.
- Introduce sliding-scale healthcare costs for financially vulnerable populations.
- Direct community outreach and diabetes education toward high-prevalence states, including Mississippi and Georgia.
- Integrate diabetes treatment with mental-health screening and depression care.
- Improve transportation and telehealth support for communities with limited healthcare access.
- Invest in childhood-focused health and resilience programs in states with high adverse-childhood-experience indicators.
- Use state-level risk patterns to guide public-health funding and intervention design.

## Technology

`Google BigQuery` `Google Cloud Storage` `SQL` `Python` `Pandas` `Plotly` `Jupyter Notebook`

The notebook contains the data-engineering process, SQL queries, exploratory analysis, geographic visualizations, findings, and policy recommendations.

## Limitations and Future Work

- BRFSS responses are self-reported and may be affected by recall or response bias.
- CDI contains aggregated indicators, while BRFSS contains individual responses; associations should not be interpreted as causal relationships.
- Missing survey responses were preserved when imputation could distort population-level findings.
- Future work could compare additional years, study demographic disparities in greater depth, and apply statistical or predictive models to quantify risk.
- More granular county-level and neighborhood-level data could support locally targeted interventions.


## Project Context

This project was completed for **BA775** in 2024. It demonstrates cloud-based data engineering, large-scale SQL analysis, interactive data visualization, and the translation of health data into practical policy recommendations.
