# Brazilian E-Commerce Public Dataset by Olist — Data Analysis

## Overview

This project is an end-to-end data analysis of the Olist Brazilian E-Commerce dataset, one of the most comprehensive real-world e-commerce datasets available publicly. It covers over 100,000 orders made on Olist's marketplace between 2016 and 2018, spanning customers, sellers, products, payments, deliveries, and reviews.

The aim is to extract meaningful business insights from raw data — understanding sales performance, customer behaviour, product trends, and delivery patterns through systematic exploration and analysis.

## Dataset

The dataset is sourced from Kaggle: [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

It consists of 9 inter-related tables:

| Table | Description |
|-------|-------------|
| olist_customers_dataset | Customer IDs and location |
| olist_geolocation_dataset | ZIP code coordinates |
| olist_order_items_dataset | Items, prices, and freight per order |
| olist_order_payments_dataset | Payment type and value |
| olist_order_reviews_dataset | Review scores and comments |
| olist_orders_dataset | Order status and all timestamps |
| olist_products_dataset | Product dimensions and category |
| olist_sellers_dataset | Seller location |
| product_category_name_translation | Portuguese to English category names |

Raw CSV files are not stored in this repository. Notebooks load the data directly from Kaggle via `kagglehub`.

## Approach

The analysis is structured day by day. Each day focuses on one phase of the data analysis workflow:

- Data loading and cleaning
- Exploratory data analysis
- Sales and revenue trends
- Customer behaviour analysis
- Product and category insights
- Delivery and logistics patterns

Each day has its own folder containing the Colab notebook and a README describing what was done and why.

## Tech Stack

- Python
- Pandas
- Google Colab
- KaggleHub

## Structure

```
Day 1/
    Olist_Dataset.ipynb
    README.md
Day 2/
    ...
```
