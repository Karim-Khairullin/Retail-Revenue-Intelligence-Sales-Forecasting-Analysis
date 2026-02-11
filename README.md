# Retail-Revenue-Intelligence-Sales-Forecasting-Analysis
Retail Revenue Intelligence &amp; Sales Forecasting Analysis
🧹 Data Cleaning & Preprocessing
Missing Values — Postal Code

The dataset contains 11 missing values in the postal_code column (approximately 0.1% of total records).

Since the geographic analysis in this project is conducted at the region, state, and city level, missing postal codes do not materially affect the analysis. Therefore:

No imputation was performed.

Rows were retained to preserve full sales information.

This decision avoids unnecessary data manipulation while maintaining analytical integrity.

Duplicate Records

Duplicate checks were performed using the combination of:

order_id

product_id

Some records share the same order_id and product_id but differ in sales values.

These entries likely represent:

Split transactions

Multiple line items within the same order

Partial payments or separate billing entries

Since each row reflects valid revenue data, no duplicate rows were removed. All records were retained to ensure accurate total sales aggregation.

Date Format Issues

The order_date and ship_date columns were initially stored as string (object) data types and contained day-first formatted values (e.g., 15/04/2018).

To enable time-series analysis and delivery time calculations:

Columns were converted to datetime format using dayfirst=True.

Parsing errors were handled using errors="coerce" to ensure robustness.

Conversion was validated to confirm correct datetime types.

This step was essential for:

Extracting year, month, and quarter features

Computing delivery time (ship_date - order_date)

Performing time-series forecasting
