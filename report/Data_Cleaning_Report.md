# Adidas Data Cleaning Report

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

### Initial Assessment

`Campaign` has the highest missingness at approximately 23.74%. This column requires careful treatment because missing campaign information may represent either missing data or transactions that were not associated with a campaign.

Numerical columns such as `Customer_Rating`, `Shipping_Days`, `Marketing_Spend_USD`, `Discount_Rate`, and `Customer_Age` will require a documented imputation strategy.

Categorical columns such as `City`, `Size`, `Gender`, and `Campaign` will require categorical-value handling.

---

## 6. Duplicate Analysis

### Exact Duplicate Rows

The dataset contains:

- **45 duplicate rows**

### Duplicate Order IDs

The dataset also contains:

- **45 duplicated `Order_ID` records**

The profiling results show that duplicated order records appear to represent exact repeated records in the dataset. These records require verification before removal.

### Planned Action

Before deleting duplicates, the cleaning phase will:

1. Identify duplicate rows.
2. Compare duplicated records.
3. Confirm whether they are exact duplicates.
4. Remove only confirmed duplicate records.

---

## 7. Categorical Data Quality Issues

The profiling phase identified several inconsistent categorical representations.

### Country

The dataset contains case inconsistencies such as:

- `Saudi Arabia`
- `SAUDI ARABIA`

- `India`
- `INDIA`

- `Germany`
- `GERMANY`

- `Pakistan`
- `PAKISTAN`

- `Australia`
- `AUSTRALIA`

These values represent the same countries and should be standardized.

### Category

Values contain whitespace variations, for example:

- `Running`
- ` Running `

- `Outdoor`
- ` Outdoor `

- `Basketball`
- ` Basketball `

These values should be stripped and standardized.

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

## 8. Numerical Data Quality Issues

The statistical summary identified potentially invalid or suspicious values.

### Quantity

- Minimum: `-1`
- Maximum: `150`

A negative quantity is invalid for a normal sales transaction and requires investigation.

### Discount Rate

- Minimum: `-0.20`
- Maximum: `3.00`

A discount rate should normally fall within the range:

`0 ≤ Discount_Rate ≤ 1`

Therefore, negative values and values greater than 1 require validation.

**Important:** valid decimal discount rates must not be rounded to whole numbers. For example, `0.10` must not be converted to `0`.

### Revenue

- Minimum: `-1,000`
- Maximum: `500,000`

These extreme values require business-rule validation and anomaly investigation.

### Customer Age

- Minimum: `5`
- Maximum: `150`

The values outside a reasonable customer-age range require validation.

### Shipping Days

- Minimum: `-2`
- Maximum: `90`

Negative shipping days are invalid and require correction or treatment.

---

## 9. Data Quality Risks Identified

The main data-quality problems identified during profiling are:

1. Missing values in nine columns.
2. 45 duplicate rows.
3. 45 duplicated Order IDs.
4. Case inconsistencies in country values.
5. Leading/trailing whitespace in category values.
6. Case inconsistencies in sales-channel values.
7. Invalid negative quantity.
8. Invalid discount-rate values outside the expected range.
9. Suspicious revenue outliers.
10. Invalid customer-age values.
11. Negative shipping-day values.

---

## 10. Planned Cleaning Strategy

### Step 1 — Preserve Raw Data

The original raw dataset will remain unchanged.

A working copy will be used for cleaning.

### Step 2 — Handle Confirmed Duplicates

Only confirmed exact duplicate records will be removed.

### Step 3 — Standardize Text Categories

Operations will include:

- Removing leading and trailing whitespace.
- Standardizing case.
- Consolidating equivalent category labels.

### Step 4 — Handle Missing Values

The method will be selected according to the column's business meaning and data type.

Potential strategies include:

- KNN imputation for selected numerical variables.
- Median or group-based imputation where appropriate.
- Explicit `Unknown` category for selected categorical variables.
- Business-rule-based handling for campaign-related missingness.

### Step 5 — Handle Invalid Values

Examples include:

- Invalid negative quantity.
- Invalid discount rates.
- Invalid customer ages.
- Negative shipping days.

These values will be investigated and corrected using documented rules.

### Step 6 — Validate Business Logic

Financial relationships will be checked, including:

`Revenue = Quantity × Unit Price × (1 − Discount Rate)`

and:

`Profit = Revenue − Cost`

The exact formula will be validated against the dataset before any correction is applied.

### Step 7 — ML-Based Processing

After basic data cleaning, selected machine-learning techniques may be applied:

- KNN Imputation for suitable numerical missing values.
- Isolation Forest for anomaly detection.

Anomalies will initially be flagged rather than automatically deleted.

---

## 11. Conclusion

The profiling phase confirms that the Adidas dataset contains realistic data-quality challenges suitable for an end-to-end data analytics project.

The main challenges are missing values, duplicate records, inconsistent categorical labels, invalid numerical values, and extreme financial observations.

The next phase is:

**`02_Data_Cleaning.ipynb`**

In that notebook, the identified problems will be handled systematically and the cleaned dataset will be exported as:

`data/processed/Adidas_Cleaned_Data.xlsx`

The cleaned dataset will then be used for ML-based data processing, feature engineering, exploratory analysis, and Power BI visualization.
