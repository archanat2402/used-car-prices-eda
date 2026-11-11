# 🚗 Exploratory Data Analysis: Used Car Prices

## 📋 Project Overview

This project focuses on performing **Exploratory Data Analysis (EDA)** on a used car dataset from CarDekho to understand the factors associated with used-car selling prices.

The objective is to explore the dataset, identify data quality issues, understand relationships between different vehicle features, and discover meaningful patterns that influence used-car prices.

The analysis was performed using **Python, Pandas, NumPy, Matplotlib and Seaborn** in Google Colab.

## 🎯 Project Objectives

- Understand the structure and characteristics of the used car dataset.
- Identify and handle missing values and duplicate records.
- Perform data cleaning and preprocessing.
- Analyse selling price distributions and detect outliers.
- Explore relationships between vehicle age, mileage, fuel type, transmission and selling price.
- Perform brand-wise and categorical analysis.
- Visualize important patterns and correlations.

## 📊 Dataset Information

**Dataset Name:** CarDekho Used Car Dataset (Car Details v3)

**Dataset Source:** [Kaggle – CarDekho Used Car Dataset](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho)

The dataset contains information about used cars listed for sale in India, including their specifications, manufacturing year, mileage, fuel type, transmission and selling prices.

### Dataset Details

| Description | Value |
|---|---:|
| Original Records | 8,128 |
| Original Columns | 13 |
| Records After Cleaning | 6,926 |
| Columns After Feature Engineering | 19 |
| Duplicate Rows Removed | 1,202 |

### Important Dataset Features

| Feature | Description |
|---|---|
| `name` | Car name and model |
| `year` | Manufacturing year |
| `selling_price` | Selling price in INR |
| `km_driven` | Distance driven in kilometres |
| `fuel` | Fuel type |
| `seller_type` | Seller category |
| `transmission` | Manual or automatic |
| `owner` | Previous ownership category |
| `mileage` | Vehicle mileage |
| `engine` | Engine capacity |
| `max_power` | Maximum engine power |
| `torque` | Engine torque |
| `seats` | Number of seats |

## ⚙️ Data Cleaning and Preprocessing

The following preprocessing steps were performed:

1. **Data Inspection:** Examined dataset dimensions, column names, data types, unique values and summary statistics.

2. **Missing Value Analysis:** Identified missing values in technical specification columns such as `torque`, `seats`, `engine`, `mileage` and `max_power`.

3. **Missing Value Handling:** Investigated missing-value patterns without applying unnecessary imputation.

4. **Duplicate Removal:** Removed 1,202 exact duplicate records, reducing the dataset from 8,128 to 6,926 records.

5. **Data Type Conversion:** Extracted numerical values from mileage, engine capacity and maximum power columns.

6. **Invalid Value Handling:** Identified invalid specification values and handled them appropriately.

7. **Mileage Standardization:** Separated `kmpl` and `km/kg` measurements to avoid mixing different mileage units.

8. **Feature Engineering:** Created a new `age` feature using the manufacturing year.

9. **Brand Extraction:** Extracted manufacturer names from car names to create a separate `brand` feature.

10. **Outlier Investigation:** Used the IQR method to investigate unusual values in selling price and kilometres driven.

After preprocessing, the final analysis dataset contained **6,926 records and 19 columns**.

## 🔍 Missing Value Analysis

Missing values were examined using percentage-based visualizations and a heatmap.

The analysis identified missing values in five technical specification columns:

- `torque`
- `seats`
- `engine`
- `mileage`
- `max_power`

The missing values frequently occurred together, indicating a shared missing-data pattern among some listings.

### Missing Values Visualization

![Missing Values Analysis](visualizations/Missing%20Values%20Analysis.jpeg)

## 📈 Exploratory Data Analysis and Visualizations

### 1. Outlier Analysis

The Interquartile Range (IQR) method was used to identify potential outliers in selling price and kilometres driven.

- 328 selling-price records (4.74%) were above the upper IQR boundary.
- 167 kilometre-driven records (2.41%) were above the upper IQR boundary.
- High-priced listings were investigated and retained when they represented plausible premium vehicles.
- Three implausible kilometre values were handled separately in the cleaned feature.

### Visualization

![Outlier Analysis](visualizations/Outlier%20Analysis.jpeg)

### 2. Selling Price Distribution

The selling-price distribution was analysed using statistical measures and visualizations.

Key observations:

- Mean selling price: Approximately INR 517,271.
- Median selling price: INR 400,000.
- The distribution showed strong positive skewness (5.57).
- A log10 transformation reduced the skewness to approximately -0.16.

This indicates that a small number of expensive vehicles influence the overall price distribution.

### Visualization

![Selling Price Distribution](visualizations/Selling%20Price%20Distribution.jpeg)

### 3. Vehicle Age vs Selling Price

The relationship between vehicle age and selling price was explored.

Key observations:

- Older vehicles generally had lower selling prices.
- Vehicle age showed a strong negative correlation with log selling price (r = -0.72).
- Newer vehicles generally had higher median selling prices.

This analysis highlights the relationship between vehicle depreciation and resale value.

### Visualization

![Vehicle Age vs Selling Price](visualizations/Vehicle%20Age%20vs%20Selling%20Price.jpeg)

### 4. Price by Fuel Type and Transmission

Selling prices were compared across different fuel types and transmission categories.

Key observations:

- Diesel cars had a median selling price of INR 520,000.
- Petrol cars had a median selling price of INR 310,000.
- Automatic cars had a median selling price of INR 850,000.
- Manual cars had a median selling price of INR 385,000.

These differences represent group-level comparisons and may also be influenced by vehicle age, brand and segment.

### Visualization

![Price by Fuel Type and Transmission](visualizations/Price%20by%20Fuel%20Type%20and%20Transmission.jpeg)

### 5. Correlation Analysis

A correlation heatmap was created to understand the relationships between numerical vehicle features and log selling price.

Important observations:

| Feature | Correlation with Log Price |
|---|---:|
| Vehicle Age | -0.72 |
| Maximum Power | +0.65 |
| Engine Capacity | +0.47 |
| Mileage | +0.02 |

Vehicle age showed the strongest negative relationship, while maximum power showed a positive relationship with log selling price.

### Visualization

![Correlation Heatmap](visualizations/Correlation%20Heatmap.jpeg)

### 6. Brand-Wise Analysis

The dataset was analysed to understand the distribution of listings and selling prices across different car manufacturers.

Key observations:

- Maruti had the highest number of listings (2,165).
- Hyundai followed with 1,267 listings.
- Mahindra had 723 listings.
- Among brands with at least 30 listings, BMW, Audi and Mercedes-Benz had the highest median selling prices.

### Visualization

![Brand Analysis](visualizations/Brand%20Analysis.jpeg)

### 7. Categorical Analysis

Categorical features such as ownership, seller type and seating capacity were explored.

Key observations:

- First-owner vehicles formed the largest ownership group (4,242; 61.2%).
- Individual sellers accounted for 6,218 listings (89.8%).
- Five-seat vehicles were the most common (5,254; 75.9%).
- Median selling prices generally decreased as the number of previous owners increased.

### Visualization

![Categorical Analysis](visualizations/Categorical%20Analysis.jpeg)

## 💡 Key Findings

1. **Selling Price Distribution:** Used-car selling prices showed a strongly right-skewed distribution, making the median more representative than the mean.

2. **Vehicle Age:** Older vehicles generally had lower selling prices, with a negative correlation of -0.72 with log price.

3. **Engine Power:** Maximum power showed a positive correlation of +0.65 with log selling price.

4. **Engine Capacity:** Engine capacity showed a positive correlation of +0.47 with log selling price.

5. **Brand Differences:** Premium brands such as BMW, Audi and Mercedes-Benz had higher median selling prices among brands with sufficient listings.

6. **Ownership:** First-owner vehicles represented the largest group in the dataset.

7. **Data Quality:** Removing duplicate records and handling invalid values improved the consistency of the dataset.

8. **Mileage:** Mileage showed almost no linear correlation with log selling price (+0.02).

## 🛠️ Technologies and Libraries Used

| Technology | Purpose |
|---|---|
| Python | Programming and analysis |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Google Colab | Development environment |
| Kaggle | Dataset source |
| GitHub | Project hosting and documentation |

## 📁 Project Structure

```text
used-car-prices-eda/
│
├── visualizations/
│   ├── Brand Analysis.jpeg
│   ├── Categorical Analysis.jpeg
│   ├── Correlation Heatmap.jpeg
│   ├── Missing Values Analysis.jpeg
│   ├── Outlier Analysis.jpeg
│   ├── Price by Fuel Type and Transmission.jpeg
│   ├── Selling Price Distribution.jpeg
│   └── Vehicle Age vs Selling Price.jpeg
│
├── Python_&_Pandas_EDA_TASK_1.ipynb
│
├── README.md
│
└── requirements.txt
```

## ⚠️ Limitations

- The dataset does not contain a unique listing ID, so identical rows may not always represent accidental duplicates.
- Vehicle age was calculated using 2020 as the reference year because the dataset collection date was not specified.
- Group comparisons do not account for every factor influencing selling prices.
- Some categorical groups have relatively small sample sizes.
- Missing technical specifications were not imputed.
- The 87 `km/kg` mileage values were excluded from the `kmpl` comparison.
- Correlation indicates association, not causation.
- No predictive machine learning model was developed in this project.

## 🎯 Conclusion

This project explored the CarDekho used car dataset through data cleaning, preprocessing, feature engineering, statistical analysis and visualization.

After removing duplicate records and handling invalid values, 6,926 records were used for the final analysis.

The findings showed that vehicle age, maximum power, engine capacity and brand are meaningfully associated with used-car selling prices. The analysis also demonstrated the importance of understanding missing values, identifying outliers and exploring relationships between numerical and categorical variables.

Overall, this project provided practical experience in **Python-based data analysis, Pandas, exploratory data analysis, statistical interpretation and data visualization**.

---

**Project Type:** Exploratory Data Analysis (EDA)  
**Domain:** Data Analytics  
**Programming Language:** Python  
**Environment:** Google Colab  
**Dataset:** CarDekho Used Car Data (Car Details v3)
