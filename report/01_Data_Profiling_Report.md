# 📊 Adidas Sales Dataset - Data Profiling Report

## 📌 Overview

This report presents the initial assessment of the Adidas US Sales dataset before any preprocessing or transformation. Data profiling helps understand the dataset's structure, quality, completeness, and potential issues that need to be addressed before analysis.

---
# 🎯 Objective
The primary objectives of data profiling are:
- Understand the dataset structure.
- Identify missing values.
- Detect duplicate records.
- Verify data types.
- Examine statistical summaries.
- Evaluate data quality before cleaning.
---
# 📂 Dataset Information

| Property | Description |
|----------|-------------|
| Dataset | Adidas US Sales |
| File Format | Excel (.xlsx) |
| Domain | Retail Sales |
| Purpose | Business Intelligence & Sales Analytics |
---
# 🔍 Profiling Activities
## 1. Dataset Loading
The dataset was successfully imported into a Pandas DataFrame for further analysis.
---
## 2. Dataset Structure
The following information was examined:
- Number of rows
- Number of columns
- Column names
- Data types
- Memory usage
---
## 3. Initial Inspection
The first few records were displayed using:
- `head()`
- `tail()`
- `sample()`
This ensured that the dataset was loaded correctly.
---
## 4. Data Types
Each column's data type was verified to ensure consistency.
Expected data types include:
- Object
- Integer
- Float
- DateTime
---

## 5. Missing Value Analysis
Missing values were calculated for every column.

This helped determine whether data imputation or column removal would be required.

---
## 6. Duplicate Analysis

Duplicate records were identified to prevent repeated transactions from affecting future analysis.
---
## 7. Descriptive Statistics

Statistical summaries were generated for all numerical variables, including:

- Mean
- Median
- Standard Deviation
- Minimum
- Maximum
- Quartiles
---
## 8. Categorical Feature Analysis
Categorical variables were identified for future grouping and visualization.

Examples include:

- Retailer
- Region
- State
- City
- Product
- Sales Method
---
## 9. Numerical Feature Analysis
Numerical variables were identified for statistical analysis.

Examples include:
- Price per Unit
- Units Sold
- Total Sales
- Operating Profit
- Operating Margin

---
# 📈 Summary
The profiling process provided a comprehensive overview of the dataset and highlighted the overall data quality.
---
# ✅ Conclusion
The Adidas US Sales dataset is well-structured and suitable for further preprocessing. The insights obtained during profiling provide a strong foundation for the data cleaning, exploratory data analysis (EDA), and Power BI dashboard development stages.