# Retail Sales Analysis with PySpark

A small learning project to practise PySpark on a real retail dataset (~1M transactions).

## Dataset
[Online Retail II (UCI)](https://archive.ics.uci.edu/dataset/502/online+retail+ii): all transactions of a UK-based online retailer between Dec 2009 and Dec 2011.

## What it does
- Reads the data with an explicit schema and parses timestamps
- Cleans it: missing customer IDs, cancelled invoices, non-positive quantities/prices, duplicates
- Aggregates revenue by product and by country with `groupBy`
- Builds weekly product-level demand features with window functions: 4-week moving average, previous-week quantity, week-over-week change
- Runs a monthly revenue analysis for the top 5 countries in Spark SQL
- Writes results to Parquet

## How to run
1. Install Java 17 or 21.
2. `pip install -r requirements.txt`
3. Download `online_retail_II.xlsx` from the UCI page and place it in `data/`.
4. Open and run `retail_sales_pyspark.ipynb`.

## Results
<!-- Add your own findings after running the notebook: rows removed by cleaning, top products, top countries, weekly trend observations. -->

## Limitations
- Weeks with zero sales for a product are not filled in, so moving averages and lag values skip those weeks. A forecasting setup would fill missing weeks with 0 first.
- Runs locally (`local[*]`); the dataset is small enough that Spark is used here for learning, not because the data requires it.
