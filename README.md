# Corporate Expense Data Cleaning & Auditing Pipeline (Python & Pandas)

## Project Overview
This project addresses a common corporate data challenge: processing an unformatted, messy Excel export containing company expenses for March. The dataset was provided with multiple data quality issues, missing records, and formatting errors that made any immediate financial analysis impossible.

The goal was to build a reliable data-cleaning pipeline in Python using **Pandas** to audit the file, fix all structural anomalies, and compute verified financial aggregates for the Chief Financial Officer (CFO).

## Initial Data Quality Challenges
Before cleaning, a thorough audit of the raw dataset revealed several critical issues:
* **Missing Data:** Empty cells in structural columns such as departments and expense designations.
* **Data Type Mismatches:** The financial amounts were stored as text strings (`object`) due to currency formatting and hidden spaces, preventing any mathematical aggregation.
* **Text Formatting Issues:** Truncated strings, varying letter casing, and trailing white spaces that would create artificial duplicates during group-by operations.
* **Negative Transactions:** Detection of negative amounts representing supplier refunds or credit notes that required specific auditing.

## Technical Pipeline Steps (Jupyter Notebook)
The data engineering process followed a structured approach within the Jupyter Notebook:

1. **Initial Dataset Audit:** Used Pandas exploratory features (`.info()`, `.describe()`, and `.isna().sum()`) to map out missing values and identify bad data types.
2. **Text Standardization:** Applied string manipulation methods (`.str.strip()` and uniform casing) to clean up department names and item descriptions, ensuring clean categorical groupings.
3. **Missing Value Imputation:** Handled missing categorical variables using accounting logic (assigning generic placeholders like "Unassigned" rather than deleting rows, which would artificially lower total expenses).
4. **Financial Type Parsing & Conversion:** Cleaned the monetary column by stripping non-numeric characters and explicitly casting the values into floating-point numbers (`float`).
5. **Anomaly Auditing:** Isolated and analyzed specific anomalies, such as tracking negative values (totaling -836.09 euros across 5 transactions) to identify vendor refunds.
6. **Financial Aggregation:** Computed the final accurate operational budget for March and segmented expenses by department to highlight the top spending centers.

## Repository Contents
* `DataCleaning_Analysis.ipynb`: The complete, fully documented Jupyter Notebook containing the Python/Pandas code.
