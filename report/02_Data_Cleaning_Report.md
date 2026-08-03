# 🧹 Adidas Sales Dataset - Data Cleaning Report
## 📌 Overview
This report documents the preprocessing and cleaning steps performed on the Adidas US Sales dataset to improve data quality and prepare it for analysis and visualization.
---
# 🎯 Objective

The objectives of the data cleaning process are:

- Improve data consistency.
- Remove unnecessary information.
- Standardize column names.
- Ensure accurate data types.
- Prepare the dataset for EDA and Power BI.

---

# 📂 Dataset

| Property | Description |
|----------|-------------|
| Dataset | Adidas US Sales |
| Input | Raw Dataset |
| Output | Cleaned Dataset |

---
# 🛠 Cleaning Process

## 1. Dataset Loading

The raw dataset was loaded into a Pandas DataFrame.
---
## 2. Backup Creation
A copy of the original dataset was created before making any modifications.
This preserves the raw data for future reference.
---
## 3. Duplicate Detection
The dataset was checked for duplicate records.
Duplicate rows can lead to incorrect calculations and misleading business insights.
---

## 4. Duplicate Removal
Duplicate records were removed to improve data quality and maintain data integrity.
---
## 5. Column Renaming
Column names were standardized using Python.
Changes included:
- Converting to lowercase
- Replacing spaces with underscores
- Improving readability

Example:

| Original | Renamed |
|-----------|----------|
| Invoice Date | invoice_date |
| Price per Unit | price_per_unit |
| Units Sold | units_sold |
| Total Sales | total_sales |
---
## 6. Empty Column Removal
Completely empty columns were removed because they provided no analytical value.
---
## 7. Missing Value Verification
The cleaned dataset was checked again to confirm that missing values were handled appropriately.
---
## 8. Data Type Verification
Data types were verified to ensure that:

- Dates were stored as DateTime.
- Numerical values were stored correctly.
- Text fields remained categorical.
---

# 📊 Output
After cleaning, the dataset became:
- Cleaner
- More consistent
- Easier to analyze
- Ready for visualization
- Suitable for Power BI dashboards
---
# 🚀 Benefits
The cleaned dataset can now be used for:
- Exploratory Data Analysis (EDA)
- Business Intelligence
- Power BI Dashboard Development
- Sales Trend Analysis
- Retail Performance Analysis
- Machine Learning Projects
---
# ✅ Conclusion
The data cleaning process successfully transformed the raw Adidas US Sales dataset into a structured, consistent, and analysis-ready dataset. This cleaned dataset provides a reliable foundation for generating business insights, creating interactive dashboards, and performing advanced analytics.