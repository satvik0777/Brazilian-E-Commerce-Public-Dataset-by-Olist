# Day 1 — Data Loading and Cleaning

**Notebook:** [Olist_Dataset.ipynb](Olist_Dataset.ipynb)

---

## Objective

The goal for Day 1 was to get all 9 Olist datasets into a usable state — loaded, inspected, and cleaned — so that actual analysis can begin from Day 2 onwards without worrying about data quality issues.

---

## What Was Done

### 1. Setup

Installed the required libraries: `kagglehub` (with pandas support) and `pandas`. All datasets are loaded directly from Kaggle using `kagglehub.load_dataset()` so no CSV files need to be stored in the repo.

### 2. Loading All 9 Datasets

| Variable | Dataset |
|----------|---------|
| `cd_df` | olist_customers_dataset |
| `ogd_df` | olist_geolocation_dataset |
| `ooid_df` | olist_order_items_dataset |
| `oopd_df` | olist_order_payments_dataset |
| `oord_df` | olist_order_reviews_dataset |
| `ood_df` | olist_orders_dataset |
| `opd_df` | olist_products_dataset |
| `osd_df` | olist_sellers_dataset |
| `pcnt_df` | product_category_name_translation |

### 3. Inspection

- Called `.info()` on all 9 DataFrames to check column names, data types, and non-null counts.
- Called `.isnull().sum()` on all 9 DataFrames to identify which columns had missing values and how many.

### 4. Cleaning

Only the datasets that actually had null values were touched.

**Order Reviews (`oord_df`)**

`review_comment_title` and `review_comment_message` had a large number of nulls. This is expected — many customers leave a star rating without writing any text. Both columns were filled with `'No comment'`.

**Orders (`ood_df`)**

All 5 timestamp columns were converted from object strings to proper `datetime` dtype. Null delivery dates were not dropped — they exist because orders that were cancelled, shipped but not yet delivered, or still in processing legitimately have no delivery date. Instead, a new `completion_status` column was derived:

- `Delivered` — order_status is `delivered`
- `Stuck / In Progress` — order_status is `shipped`, `processing`, `approved`, or `invoiced`
- `Cancelled` — order_status is `cancelled` or `unavailable`
- `Other` — anything else

**Products (`opd_df`)**

- Rows missing `product_category_name` were dropped since they cannot be meaningfully categorised.
- Missing physical dimension values (`weight`, `length`, `height`, `width`) were filled with the median of each column, which is more robust to outliers than the mean.

### 5. Result

| Dataset | Outcome |
|---------|---------|
| Customers | No nulls — ready to use |
| Geolocation | No nulls — ready to use |
| Order Items | No nulls — ready to use |
| Order Payments | No nulls — ready to use |
| Order Reviews | Comment nulls filled with 'No comment' |
| Orders | Timestamps converted; completion_status column added |
| Products | Rows with no category dropped; dimension nulls filled with median |
| Sellers | No nulls — ready to use |
| Category Translation | No nulls — ready to use |

---

## Next

Day 2 will cover Exploratory Data Analysis — order volume over time, top product categories, payment method breakdown, and review score distribution.
