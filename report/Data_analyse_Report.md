# Adidas Data Analyse Report

## 1. Project Overview

This report documents the data profiling results and the planned data-cleaning strategy for the Adidas Business Analytics project.

The project follows this workflow:

Raw Data → Data Profiling → Data Cleaning → ML-Based Data Processing → Feature Engineering → Exploratory Data Analysis → Power BI Dashboard → Business Insights

The profiling was performed using the `Messy_Raw_Data` sheet from the Adidas synthetic dataset.

---

## 2. Dataset Overview

| Metric | Value |
|---|---:|
| Total Rows        | 3,045 |
| Total Columns     | 28 |
| Unique Order IDs  | 3,000 |
| Unique Customer IDs | 862 |
| Unique Countries (raw values) | 13 |
| Unique Regions    | 5 |
| Unique Products   | 24 |

The dataset contains sales, customer, product, marketing, operational, and financial information.

---

## 3. Dataset Structure

### Sales and Financial Data

- `Quantity`
- `Unit_Price_USD`
- `Discount_Rate`
- `Revenue_USD`
- `Cost_USD`
- `Profit_USD`

### Customer Data

- `Customer_ID`
- `Gender`
- `Customer_Segment`
- `Customer_Rating`
- `Customer_Age`
- `Customer_Lifetime_Value_USD`

### Product and Location Data

- `Country`
- `Region`
- `City`
- `Category`
- `Product`
- `Size`

### Operations and Marketing Data

- `Sales_Channel`
- `Payment_Method`
- `Campaign`
- `Returned`
- `Order_Status`
- `Shipping_Days`
- `Inventory_Available`
- `Marketing_Spend_USD`

---

## 4. Data Type Assessment

The dataset contains:

- `datetime64[ns]`: `Order_Date`
- `int64`: `Quantity`, `Inventory_Available`
- `float64`: financial, rating, age, shipping, and marketing fields
- `object`: categorical and identifier fields

`Order_Date` was already detected as a datetime column during profiling.

---

## 5. Missing Value Analysis

The following columns contain missing values:

| Column | Missing Values | Missing Percentage |
|---|---:|---:|
| Campaign | 723 | 23.74% |
| Customer_Rating | 303 | 9.95% |
| City | 243 | 7.98% |
| Size | 213 | 7.00% |
| Shipping_Days | 211 | 6.93% |
| Marketing_Spend_USD | 183 | 6.01% |
| Gender | 182 | 5.98% |
| Discount_Rate | 154 | 5.06% |
| Customer_Age | 153 | 5.02% |


## 6. Duplicate Analysis

### Exact Duplicate Rows

The dataset contains:

- **45 duplicate rows**

### Duplicate Order IDs

The dataset also contains:

- **45 duplicated `Order_ID` records**

The profiling results show that duplicated order records appear to represent exact repeated records in the dataset. These records require verification before removal.


### Sales Channel

The dataset contains case variations such as:

- `Wholesale`
- `wholesale`

- `Marketplace`
- `marketplace`

- `Mobile App`
- `mobile app`

- `Online Store`
- `online store`

- `Retail Store`
- `retail store`

These should be standardized into consistent categories.

---


### Discount Rate

- Minimum: `-0.20`
- Maximum: `3.00`

A discount rate should normally fall within the range:

`0 ≤ Discount_Rate ≤ 1`

Therefore, negative values and values greater than 1 require validation.

**Important:** valid decimal discount rates must not be rounded to whole numbers. For example, `0.10` must not be converted to `0`.


### Customer Age

- Minimum: `5`
- Maximum: `150`

The values outside a reasonable customer-age range require validation.

### Shipping Days

- Minimum: `-2`
- Maximum: `90`

Negative shipping days are invalid and require correction or treatment.

---
