# Behavioral Nudge A/B Test: Reducing CO₂ Emissions

## Approach
This project analyzes whether behavioral nudges can reduce carbon emissions by encouraging users to shift electricity usage to off-peak hours.

Using smart meter data, we simulate an A/B experiment:
- **Control group**: no intervention  
- **Treatment group**: nudges encouraging off-peak usage  

We compare energy consumption patterns and resulting CO₂ emissions between the two groups.

---

## Results
- Treatment group increased off-peak usage  
- Adjusted CO₂ emissions decreased compared to control  
- Statistical testing (t-test) confirms the difference is significant  

---

## Conclusion
Behavioral nudges can reduce carbon emissions by encouraging off-peak electricity usage.

Even small percentage improvements can scale to meaningful environmental impact.

---

## SQL Transformation
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
```

---

## Tech Stack
- Python
- SQL (SQLite)
- Pandas
- NumPy
- SciPy
- VS Code / Jupyter Notebook

---

## Dataset
This project uses the **"Smart Meters in London"** dataset available on Kaggle.

Source: https://www.kaggle.com/datasets/jeanmidev/smart-meters-in-london

The dataset contains anonymized household electricity consumption data and is used here for educational and analysis purposes.

---

## Note
This project simulates an A/B experiment using historical data. No real intervention was conducted.