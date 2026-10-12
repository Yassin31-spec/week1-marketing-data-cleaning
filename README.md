# 🛠️ Week 1 — Data Collection, Preprocessing & Cleaning Report

## Overview
This repository contains the Week 1 deliverables for a simulated professional marketing analytics workflow. The goal was to collect, clean, and preprocess marketing campaign data (impressions, clicks, conversions, costs, customer metadata) to produce a reliable dataset ready for downstream analysis and modeling.

## 🎯 Task Objective & Scope
The objective of Week 1 was to simulate the initial phase of professional marketing analytics by:
- Collecting relevant marketing campaign and customer data.
- Performing comprehensive data cleaning and quality control.
- Engineering features and KPIs to enable subsequent performance modeling.
- Documenting every step for transparency and reproducibility.

Scope:
- Multi-channel online advertisement and campaign metrics.
- Customer-level aggregate metrics and campaign acceptance behavior.
- Preprocessing steps to produce an analysis-ready dataset.

## 📋 Key Steps & Execution Details

### 1. Dataset Identification & Extraction
- Sourced publicly available marketing campaign data focusing on online ad metrics (impressions, clicks, conversions, costs).
- Extracted attributes required to map multi-channel performance: campaign_id, channel, date, impressions, clicks, conversions, cost, customer_id, product_category, purchase_amount, etc.

### 2. Data Cleaning & Quality Control
- Handling Missing Values
  - Audited the dataset for null or incomplete entries.
  - Applied safe imputation for fields where plausible (e.g., fill missing campaign channel with "unknown" when appropriate) and removed records that lacked essential identifiers.
- Removing Duplicates & Outliers
  - Removed duplicate customer IDs and duplicate event records.
  - Filtered invalid historical records (e.g., impossible birth years like prior to 1940).
  - Applied statistical or domain-based rules to cap or remove extreme outliers that would distort analyses.
- Consistency Correction
  - Standardized dates to YYYY-MM-DD.
  - Normalized categorical labels (e.g., channel labels to lowercase canonical values).
  - Checked and corrected currency/number formats.

### 3. Advanced Feature Engineering
- Transformed raw attributes into actionable KPIs:
  - Click-Through Rate (CTR) = clicks / impressions
  - Conversion Rate = conversions / clicks
  - Cost Per Click (CPC) = cost / clicks
  - Cost Per Acquisition (CPA) = cost / conversions
- Aggregated customer-level metrics:
  - Total customer spending across product categories
  - Aggregate campaign acceptance counts (e.g., number of campaigns a customer responded to)
  - Unified purchasing channel indicator (e.g., online / in-store / hybrid)
- Created time-based features (week, month, campaign_age_days) for temporal analysis.

### 4. Structured Documentation & Deliverables
- Ensured final dataset is structured and optimized for analysis: clean schema, consistent datatypes, documented columns.
- Documented each cleaning and transformation step to ensure transparency and replicability.

## 🔍 Data Dictionary (example)
- campaign_id: Unique identifier for the campaign
- date: Event or reporting date (YYYY-MM-DD)
- channel: Marketing channel (e.g., search, social, display, email)
- impressions: Number of ad impressions
- clicks: Number of ad clicks
- conversions: Number of conversions attributed to the campaign
- cost: Campaign spend (currency)
- customer_id: Anonymized customer identifier
- product_category: Category of purchased product
- purchase_amount: Amount spent by customer in transaction
- ctr: Click-through rate (computed)
- conversion_rate: Conversion rate (computed)
- total_spend: Aggregated customer spend across categories (computed)

> Note: Update/add fields in this section to match your final cleaned schema.

## 🔗 Resources & Deliverables
- Cleaned Dataset & Audit File: [View Cleaned Google Sheet](https://docs.google.com/spreadsheets/d/17XXI0e6WLXAoPrWBWc44pboSR8wcWm8aBWKCkjr4mGY/edit?usp=sharing)
- Detailed Marketing Analysis Sheet: [View Marketing Analysis Google Sheet](https://docs.google.com/spreadsheets/d/1pj86M86VokcqFV1j0yhLGZ6fso-zp8zwXgGnC58_wP8/edit?usp=sharing)

## Reproducibility & How to Run
1. Source data: place raw CSV/JSON files into the `data/raw/` directory.
2. Run preprocessing scripts:
   - Example: `python src/preprocess.py --input data/raw/campaigns.csv --output data/cleaned/campaigns_clean.csv`
3. Run feature engineering scripts:
   - Example: `python src/features.py --input data/cleaned/campaigns_clean.csv --output data/processed/features.csv`
4. Validation: run `python src/validate.py --input data/processed/features.csv` to generate the validation/audit report.

Adjust script names and CLI arguments to match your actual implementation.

## Folder structure (suggested)
- data/
  - raw/                 # raw datasets (do not modify)
  - cleaned/             # cleaned outputs
  - processed/           # feature-engineered data ready for analysis
- notebooks/             # EDA and analysis notebooks
- src/                   # preprocessing, feature engineering, and validation scripts
- reports/               # audit logs, data quality reports, summaries
- README.md

## Audit & Quality Control
- Include a detailed audit log (reports/audit_report.md or .csv) documenting:
  - Number of records before/after cleaning
  - Records removed and why (duplicates, invalid dates, missing IDs)
  - Imputation decisions and proportions
  - Outlier thresholds and counts

## Next Steps / Recommendations
- Share Google Sheet links and any access permissions so collaborators can view results.
- Use the processed dataset to build baseline campaign performance models (e.g., attribution, response models).
- Add unit tests and data validation checks to the preprocessing pipeline (e.g., using Great Expectations or pytest).

## Attribution
- Prepared by: Week 1 — Data Collection, Preprocessing & Cleaning
