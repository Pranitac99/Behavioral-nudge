# Behavioral Nudge A/B Test: Reducing CO₂ Emissions

## Overview
This project simulates an A/B experiment to evaluate whether CO₂-based behavioral nudges can reduce household electricity-related emissions.

Using smart meter data from London households, we analyze how shifting electricity usage from peak to off-peak hours impacts carbon emissions.

---

## Problem
Electricity generated during peak hours often has higher carbon intensity. Encouraging users to shift consumption to off-peak hours can reduce emissions.

---

## Approach

### Data
- London Smart Meter dataset (half-hourly household energy usage)
- ~50 households sampled for analysis

### Feature Engineering
- Aggregated half-hourly data into daily household metrics
- Created:
  - total energy consumption
  - peak and off-peak usage
  - off-peak share


### Experiment Design
- Randomly assigned households to control and treatment groups
- Simulated a behavioral nudge shifting 10% of peak usage to off-peak
- Measured impact on CO₂ emissions

### Results
- CO₂ reduction: ~1.6%
- Statistically significant (p < 0.001)

### Conclusion
Behavioral nudges can reduce carbon emissions by encouraging off-peak electricity usage.

Even small percentage improvements can scale to meaningful environmental impact.



### SQL Transformation
Used SQL to aggregate raw time-series data into daily features:

```sql
SELECT
    user_id,
    date,
    SUM(energy_kwh) AS total_kwh,
    SUM(CASE WHEN is_peak = 1 THEN energy_kwh ELSE 0 END) AS peak_kwh,
    SUM(CASE WHEN is_peak = 0 THEN energy_kwh ELSE 0 END) AS offpeak_kwh
FROM energy
GROUP BY user_id, date;
'''

Tech Stack
Python
SQL (SQLite)
Pandas
NumPy
SciPy
VS Code / Jupyter Notebook
Note

This project uses the "Smart Meters in London" dataset available on Kaggle.

Source: https://www.kaggle.com/datasets/jeanmidev/smart-meters-in-london

The dataset contains anonymized household electricity consumption data and is used here for educational and analysis purposes.

This project simulates an A/B experiment using historical data. No real intervention was conducted.