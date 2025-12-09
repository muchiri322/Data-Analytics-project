Online Retail Data Project

This project implements a complete data pipeline using the Online Retail Dataset, covering ingestion, storage, cleaning, transformation, and analysis. The goal is to ensure data quality and uncover insights related to revenue trends, customer behavior, and geographic product demand.

Project Structure

Below is the recommended folder organization for the project:

online_retail_project/
│
├── data/
│   ├── raw/
│   │   └── online_retail.xlsx
│   ├── processed/
│   │   └── online_retail_clean.csv
│   └── sql_exports/
│
├── notebooks/
│   ├── 01_data_ingestion.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_sql_storage.ipynb
│   └── 04_data_analysis.ipynb
│
├── scripts/
│   ├── ingestion.py
│   ├── cleaning.py
│   ├── load_to_sql.py
│   ├── analysis.py
│   └── utils.py
│
├── sql/
│   ├── create_raw_table.sql
│   ├── create_clean_table.sql
│   └── queries.sql
│
├── reports/
│   ├── monthly_revenue_2011.csv
│   ├── country_performance.csv
│   ├── top_customers.csv
│   └── global_product_demand.csv
│
└── README.md

PHASE 1 — Data Ingestion

Load and inspect the dataset using Python.

Tasks

Load the Excel file using pandas.

Explore the dataset using:

.head(), .shape(), .describe(), .info()

Convert InvoiceDate to a datetime object.

Ensure text fields (Description, Country) are strings.

PHASE 2 — Data Storage (SQL Layer)

Store the raw dataset in PostgreSQL.

Tasks

Create a PostgreSQL table with the following schema:

InvoiceNo
StockCode
Description
Quantity
InvoiceDate
UnitPrice
CustomerID
Country


Load raw data into PostgreSQL using SQLAlchemy.

Confirm:

Successful table creation

Appropriate data types

Correct row counts

PHASE 3 — Data Preparation (Cleaning & Transformation)

Enhance data quality to ensure accurate analysis.

Cleaning Rules
1. Quantity Validation

Remove rows where Quantity < 1.

2. Unit Price Validation

Remove rows where UnitPrice < 0.

3. Additional Cleaning

Remove cancellations (InvoiceNo starting with "C").

Drop rows with missing CustomerID.

Remove duplicate records.

4. Create New Fields

Revenue = Quantity × UnitPrice

Extract Year, Month, Day from InvoiceDate

5. Save the Cleaned Dataset

Load into SQL table:

online_retail_clean


Export optional CSV to data/processed/

PHASE 4 — Data Analysis (Python Only)

Perform analytical computations for leadership insights.

1. Time Series — Revenue by Month (2011)

Filter for Year = 2011

Group by month and compute revenue totals

Identify seasonal trends and monthly changes

2. Country Performance (Excluding the UK)

Aggregate revenue per country

Rank international markets

Identify Top 10 highest-revenue countries

Compute revenue + quantity sold

3. Top Customers by Revenue

Rank customers by total revenue

Identify Top 10 highest-spending customers

4. Global Product Demand

Compute total quantity sold per country

Exclude United Kingdom

Rank countries by product quantity demand

Flag high-opportunity international markets

Deliverables

By the end of the project, you will produce:

Raw PostgreSQL table: online_retail_raw

Cleaned PostgreSQL table: online_retail_clean

Python scripts for:

Ingestion

Cleaning

SQL loading

Analysis

Jupyter notebooks for each phase

Reports:

Monthly revenue trends

International country performance

Top customers

Global demand metrics
