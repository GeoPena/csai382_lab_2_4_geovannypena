# RUN.md
## Reproducibility Instructions for Lab 2.4 ETL Notebook

This document provides step-by-step instructions to reproduce the ETL pipeline and metrics generated in `lab_2_4_repro_logging` notebook.

---

### 1. Clone the repository


git clone https://github.com/GeoPena/csai382_lab_2_4_geovannypena.git
cd csai382_lab_2_4_geovannypena

### 2. Set up Python environment

(Optional) Create a virtual environment:

python -m venv venv
source venv/bin/activate      # macOS/Linux
venv\Scripts\activate         # Windows


Install dependencies:

pip install -r requirements.txt

###3. Verify input data

Ensure the CSV files are in the data/ folder:

data/menu_items.csv

data/order_details.csv

###4. Open the notebook

Open lab_2_4_repro_logging in Databricks (or Jupyter).

Ensure the notebook points to the local data/ folder.

###5. Run the notebook cells in order

Logging setup — initializes logging and creates a timestamped log file in logs/.

Reproducibility setup — fixes random seeds and captures environment (requirements.txt).

Compute data hashes — generates data_hashes.json to track CSV integrity.

Load CSV files — loads menu_items.csv and order_details.csv into Pandas DataFrames.

Clean and standardize data — trims text, converts dates/times, and ensures numeric types.

Join datasets — merges menu items with order details.

Create final tidy table — selects relevant columns and adds quantity.

Compute metrics:

Top 5 items by quantity ordered

Revenue by category

Busiest hour of the day

Save metrics output — saves to a timestamped CSV file (e.g., metrics_YYYYMMDD_HHMM.csv).

Run quality tests — asserts required columns exist and metrics are valid.

###6. Verify results

Check the log file in logs/ for successful run messages.

Check the output CSV file for computed metrics.

Confirm that top_items, revenue_by_category, and busiest_hour are correctly calculated.

###7. Optional: PySpark section

Ensure your cluster supports Spark.

Compare Spark results with Pandas metrics and log the findings.

Notes

Do not modify raw CSV files after computing data_hashes.json; this ensures reproducibility.

Always run notebook cells in order to avoid dependency errors.

All logs are timestamped and saved in logs/ for traceability.