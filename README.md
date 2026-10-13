# 🛒 Brazilian E-Commerce — Olist Dataset Analysis

[![Open Day 1 in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/satvik0777/Brazilian-E-Commerce-Public-Dataset-by-Olist/blob/main/olist/day1/Olist_Dataset.ipynb)

A day-by-day exploratory data analysis of the [Olist Brazilian E-Commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — one of the richest real-world e-commerce datasets available publicly, covering 100k+ orders placed on Olist's marketplace between 2016 and 2018.

---

## 📁 Project Structure

```
olist/
└── day1/
    └── Olist_Dataset.ipynb   ← Data loading & cleaning
```

> 📌 Raw CSV files are not included in this repo (too large). The notebooks load data directly from Kaggle via `kagglehub`.

---

## 📅 Progress Log

| Day | Topic | Notebook |
|-----|-------|----------|
| Day 1 | Data Loading & Cleaning | [Olist_Dataset.ipynb](olist/day1/Olist_Dataset.ipynb) |
| Day 2 | *(coming soon)* Exploratory Data Analysis | — |
| Day 3 | *(coming soon)* Sales Trends | — |
| Day 4 | *(coming soon)* Customer Behaviour | — |

---

## 📦 Dataset

The Olist dataset consists of **9 inter-related tables**:

| Table | Description |
|-------|-------------|
| `olist_customers_dataset` | Customer info and unique IDs |
| `olist_geolocation_dataset` | ZIP code lat/long coordinates |
| `olist_order_items_dataset` | Items within each order |
| `olist_order_payments_dataset` | Payment type and value per order |
| `olist_order_reviews_dataset` | Customer review scores and comments |
| `olist_orders_dataset` | Order status and timestamps |
| `olist_products_dataset` | Product dimensions and category |
| `olist_sellers_dataset` | Seller location info |
| `product_category_name_translation` | Portuguese → English category names |

---

## 🛠️ Tech Stack

- **Python** (Pandas)
- **Google Colab** (notebook environment)
- **KaggleHub** (dataset loading)

---

## 📓 Day 1 — Data Loading & Cleaning

**Notebook:** [`olist/day1/Olist_Dataset.ipynb`](olist/day1/Olist_Dataset.ipynb)

### What was done

#### 1. Setup & Data Loading
- Installed `kagglehub` and `pandas`
- Loaded all 9 Olist CSV files directly from Kaggle using `kagglehub.load_dataset()`
- Each file mapped to a clearly named DataFrame variable

#### 2. Dataset Inspection
- Called `.info()` on all 9 DataFrames to check shape, column names, and dtypes
- Called `.isnull().sum()` on all 9 DataFrames to identify missing values

#### 3. Data Cleaning

**Order Reviews (`oord_df`)**
- `review_comment_title` and `review_comment_message` had significant nulls (customers who rated without writing)
- Filled both with `'No comment'`

**Orders (`ood_df`)**
- Converted all 5 timestamp columns to proper `datetime` dtype
- Null delivery dates exist because not all orders were delivered — instead of dropping rows, created a new `completion_status` column with values: `Delivered`, `Stuck / In Progress`, `Cancelled`, `Other`

**Products (`opd_df`)**
- Dropped rows missing `product_category_name` (un-categorisable)
- Filled missing physical dimensions (weight, length, height, width) with the **median** of each column

#### 4. Result
All 9 datasets are clean and ready for analysis. No data loss on the core transactional tables.

---

## 🚀 How to Run

1. Open any notebook badge link (Colab badge at the top)
2. The notebook loads data directly from Kaggle — no manual CSV upload needed
3. Run all cells top to bottom

---

## 👤 Author

**Satvik** — CS/IT Student, NTCC Internship Project
