# Vendor Performance Analytics Dashboard

## Overview

This repository contains the vendor performance analytics dashboard project. It is designed to process vendor purchase, sales, and invoice data, create a consolidated vendor sales summary, and support exploratory analysis through Jupyter notebooks.

## Key Components

- `ingestion_db.py`: Loads raw CSV files from a `data/` directory into an SQLite database named `inventory.db`.
- `get_vendor_summary.py`: Reads database tables, merges purchase, sales, and freight data, calculates vendor-level metrics, and writes a cleaned `vendor_sales_summary` table back into the database.
- `vendor_sales_summary.csv`: A generated summary dataset with vendor-level performance metrics.
- `Google Collab Files/Exploratory Data Analysis.ipynb`: Notebook for data exploration and analysis.
- `Google Collab Files/Vendor Performance Analysis.ipynb`: Notebook focused on vendor performance insights.

## Project Structure

```
.
├── get_vendor_summary.py
├── ingestion_db.py
├── vendor_sales_summary.csv
├── Google Collab Files/
│   ├── Exploratory Data Analysis.ipynb
│   └── Vendor Performance Analysis.ipynb
└── Report/
```

> Note: `ingestion_db.py` expects raw CSV files under a `data/` directory. The `data/` folder is not included in the repository listing.

## Setup

1. Install required dependencies:

```bash
pip install pandas sqlalchemy
```

2. Place your raw input CSV files inside a `data/` folder at the repository root.

3. Run the ingestion script:

```bash
python ingestion_db.py
```

This will create or update `inventory.db` and store each CSV as a database table.

## Generate Vendor Summary

Run the summary creation script:

```bash
python get_vendor_summary.py
```

This script will:

- Query the imported database tables
- Compute vendor-level metrics such as gross profit, profit margin, stock turnover, and sales-to-purchase ratio
- Store the cleaned summary in the `vendor_sales_summary` table of `inventory.db`

## Analysis

Open the notebooks in `Google Collab Files/` to explore the data visually and generate vendor performance reports.

## Logging

The scripts write logs to:

- `logs/ingestion_db.log`
- `logs/get_vendor_summary.log`

If the `logs/` directory does not exist, create it before running the scripts.

## Notes

- The repository uses SQLite for lightweight data storage and analytics.
- Ensure that the raw CSV file names match the table naming conventions expected by `get_vendor_summary.py`.
- If you want to regenerate the CSV summary output, you can export the `vendor_sales_summary` table from SQLite after running the script.
