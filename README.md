# 🚗 Exploratory Data Analysis: Used Car Prices

An end-to-end exploratory data analysis of 8,128 used car listings from CarDekho (India), built with Python, Pandas, Matplotlib and Seaborn. The project covers data quality assessment, cleaning, feature engineering and visual analysis of the factors linked to a car's selling price.

**Author:** Archana T, Data Science Intern

## Dataset

- **Source:** [CarDekho Used Car Data (Car Details v3)](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho) on Kaggle
- **File used:** `Car details v3.csv`
- **Size:** 8,128 rows and 13 columns (6,926 rows after removing duplicates)
- **Columns:** name, year, selling price (INR), kilometres driven, fuel, seller type, transmission, owner, mileage, engine, max power, torque, seats

The dataset is downloaded automatically by the notebook using `kagglehub`, so it is not stored in this repository.

## Key Questions

1. How is the selling price distributed, and are there unusual values?
2. How do vehicle age and kilometres driven relate to selling price?
3. Do fuel type and transmission show a difference in price?
4. Do dealers and individual sellers price cars differently?

## Methodology

1. **Structural overview:** shape, data types, memory usage, first and last records
2. **Data quality assessment:** missing values (bar chart and heatmap) and duplicate records
3. **Cleaning and feature engineering:** unit text converted to numbers, invalid values set to missing, `age` and `brand` features created
4. **Univariate and bivariate analysis:** summary statistics, outlier detection, and 5+ charts, each followed by a written interpretation
5. **Findings, limitations and conclusion**

Every data change is documented in the notebook together with the reason for it.

## Key Findings

1. **Price is strongly right-skewed.** The mean (INR 517,271) is well above the median (INR 400,000). A log10 transformation reduces the skew from 5.57 to -0.16.
2. **Age is the factor most strongly related to price.** The correlation between age and log price is -0.72, and the median price falls about 69% between age 2 and age 10.
3. **Engine power is more closely related to price than engine size.** Maximum power has r = +0.65 with log price, compared with +0.47 for engine size.
4. **Brand sets the price tier.** BMW, Audi and Mercedes-Benz have median prices about 10 times that of Chevrolet. Maruti has the most listings but one of the lowest median prices.
5. **Price gaps by transmission and seller type are partly an age effect.** Automatic and dealer cars are priced higher, but they are also about 2 years younger.

## Data Quality Actions

- 1,202 exact duplicate rows (14.79%) removed
- About 3% of listings have no technical specifications; these were not imputed
- Invalid zero values in `max_power` and `mileage` set to missing
- Three implausible `km_driven` values set to missing in a separate column
- `km/kg` mileage values (CNG/LPG cars) excluded from the `kmpl` column

## Limitations

- The dataset has no listing ID, so duplicates were identified by identical values in all columns.
- Age uses 2020 as the reference year, because the collection date is not stated.
- Group comparisons are not adjusted for age or car segment, so they show association, not cause and effect.
- No predictive model was built. A regression on log price using age, brand and maximum power is a suitable next step.

## Repository Structure

```
used-car-prices-eda/
├── Used_Car_Prices_EDA.ipynb   # Full analysis notebook
├── requirements.txt            # Python dependencies
├── README.md
├── visualizations
```

## Conclusion

This analysis examined 6,926 unique used car listings after removing duplicates and fixing invalid values. Vehicle age (r = -0.72), maximum power (r = +0.65) and brand are the factors most strongly linked to selling price. Price is strongly right-skewed, so a log scale suits further analysis. Dealer, automatic and diesel cars are priced higher. For dealer and automatic cars, part of the gap is linked to age, while the diesel gap is not explained by age and may reflect car segment. Each cleaning decision is documented above, because several of them (duplicates, invalid values) changed the data. A suitable next step is a regression model on log price using age, brand and maximum power.
