# DataXLAbs_Intern_Task-1-
Data Analytics internship TASK 1 : Data Cleaning and Preprocessing 

# Project Overview
This project focuses on the end-to-end data cleaning and preprocessing workflow of the **Customer Personality Analysis** dataset from Kaggle. The dataset contains marketing data covering 2,240 customers across 29 distinct features. 

To demonstrate analytical flexibility, the data was thoroughly cleaned using two separate approaches: **Microsoft Excel** and **Python (Pandas)**. Both workflows successfully yielded identical, standardized data layouts with zero errors.

## Tools & Technologies Used
* **Microsoft Excel:** Applied text-to-columns preprocessing, conditional filters, column-wide mathematical imputation, and rapid find-and-replace text manipulations.
* **Python 3 / Pandas:** Executed programmatic string manipulations, handled missing feature entries, optimized data schemas, and safely processed copies under Copy-on-Write validation rules.

## Data Cleaning Methodology & Action Steps

### 1. Handling File Layout & Structural Integrity
* **Challenge:** The raw source file utilized Tab separators (`\t`), causing data strings to clump compactly upon initial loading.
* **Excel Fix:** Used the **Text to Columns** data delimiter parsing feature to map fields into distinct column grids.
* **Python Fix:** Read the path explicitly passing the `sep='\t'` keyword argument within `pd.read_csv()`.

### 2. Treatment of Missing Values (`income`)
* **Anomaly:** Identified exactly 24 null rows hidden inside the customer income column records.
* **Treatment:** Imputed all 24 missing records using the column's **Median** value (`51381.5`). This approach effectively preserves the structural index size (2,240 rows) while preventing data skewing.

### 3. Structural Duplicates & Data Consistency Checks
* **Action:** Checked the global table structure for duplicate instances across features. Zero duplicates were detected, verifying standard record uniqueness.

### 4. Redundant Feature Pruning
* **Action:** Inspected individual column unique values and isolated `z_costcontact` and `z_revenue`. Because both columns held identical constant values for all 2,240 rows (providing zero statistical variance), they were completely dropped from the final deliverables.

### 5. Categorical Data Standardization
Text values in categorical metrics were mismatched and chaotic. They were mapped into unified, high-level categorical buckets:
* **`marital_status` Cleanup:** Standardized irregular expressions (`Alone` $\rightarrow$ `Single`; `Together` $\rightarrow$ `Partnered`; `Absurd`/`YOLO` $\rightarrow$ `Other`).
* **`education` Cleanup:** Unified standard academic tiers (`Graduation` $\rightarrow$ `Graduate`; `PhD`/`Master` $\rightarrow$ `Postgraduate`; `2n Cycle`/`Basic` $\rightarrow$ `Undergraduate`).

### 6. Schema Optimization
* Converted lowercase transformations across all column headers to create uniform snake_case mapping.
* Optimized the customer acquisition column `dt_customer` from generic string objects into explicit structural `datetime64` timeline entries.

## Repository Structure & Deliverables
* `/data/marketing_campaign.csv`: The untouched, raw source dataset.
* `/data/Cleaned_Data_Excel.xlsx`: The final cleaned master file processed via MS Excel.
* `/data/Cleaned_Data_Python.csv`: The final clean programmatic dataset exported from Pandas.
* `/scripts/TASK_1_python_idle.py`: The bug-free script file executing the workflow sequentially.
