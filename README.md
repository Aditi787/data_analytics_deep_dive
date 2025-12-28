# 📊 Exploratory Data Analysis (EDA)

Brazilian E-Commerce Dataset (Olist)

## 🔍 Objective

The goal of this EDA is to understand the structure, quality, and business relevance of the Olist Brazilian e-commerce dataset before performing any modeling or deep-dive analysis. The focus is on identifying data grain, key relationships across tables, and potential data quality issues that could impact downstream insights.

## 🗂 Dataset Overview

The analysis uses multiple relational datasets capturing the end-to-end e-commerce lifecycle:

Customers – customer identity and geographic location
Orders – order lifecycle and delivery timestamps
Order Items – product-level pricing and freight details
Payments – payment methods, installments, and values
Products – product metadata and physical attributes
Sellers – seller identity and geographic distribution
Geolocation – zip-code level latitude and longitude data

Each dataset operates at a different grain (customer, order, item, payment), making grain validation a critical first step.

## 🔎 Key Data Quality & Structural Checks

Grain validation:
Orders can contain multiple items and payments.
Customers may place multiple orders (customer_unique_id).

## Missing values:

Timestamp fields are conditionally missing based on order status (expected behavior).
Product dimension and weight attributes show notable gaps.

## Duplicates:

Geolocation data contains multiple latitude/longitude entries per zip code prefix, requiring aggregation before joins.

## Data consistency:

Order status must be considered when analyzing delivery times or cancellations to avoid biased metrics.

## 📈 Initial Observations & Insights

### Customer & Seller Geography:
Demand and supply are concentrated in a few Brazilian states, which has implications for delivery times and logistics costs.

### Order & Delivery Behavior:
Rich timestamp data enables full funnel analysis (purchase → approval → delivery), but requires careful filtering by order status.

### Payments:
Credit cards dominate payment methods, with installment payments being common. Revenue calculations must aggregate payment records at the order level.

### Products & Freight:
Product prices and freight costs are highly skewed, suggesting opportunities for freight optimization and improved seller onboarding standards.

## ⚠️ Key Analytical Considerations

Always aggregate items and payments to order level before revenue analysis.
Deduplicate or average geolocation coordinates before spatial analysis.
Condition delivery metrics on delivered orders only.
Treat missing product attributes as a data quality limitation, not a modeling error.

