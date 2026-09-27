# Dataset Documentation

---

# Dataset Information

**Dataset Name:**
Online Retail II

**Project:**
Customer IQ & Retention Analytics Platform

**Source:**
Kaggle

**Original Source:**
UCI Machine Learning Repository

**Dataset License:**
Publicly available for learning and research

**Status:**
Selected

**Date Selected:**
26 July 2026

---

# Business Profile

| Attribute | Information |
|-----------|-------------|
| Business Type | Online Retail (E-commerce) |
| Store Type | Non-store Online Retail |
| Country | United Kingdom (UK) |
| Time Period | 01-Dec-2009 to 09-Dec-2011 (Approx. 2 Years) |
| Products Sold | All-Occasion Giftware |
| Customer Type | Individual Customers and Wholesalers |
| Data Type | Customer Transaction Data |

---

# Business Understanding

## Business Problem

Businesses often lose valuable customers without understanding why they stop purchasing. The goal of this project is to analyze customer purchasing behaviour, identify valuable customer segments, predict potential churn, and generate actionable business insights that improve customer retention.

## Why This Dataset?

This dataset contains approximately two years of customer transaction history, including invoice details, customer identifiers, product information, purchase quantities, prices, and transaction timestamps.

These attributes make it suitable for:

- Customer Behaviour Analysis
- RFM (Recency, Frequency, Monetary) Analysis
- Customer Segmentation
- Customer Retention Analysis
- Churn Prediction
- Business Intelligence Reporting
- Machine Learning

---

# Dataset Structure

| Attribute | Value |
|-----------|-------|
| Total Records | 1,067,371 |
| Total Columns | 8 |
| Data Format | CSV |
| Dataset Size | ~92 MB |
| Observation Unit | One row represents one product purchased within a customer invoice. |
| Primary Business Entity | Customer Transactions |

---

# Column Documentation

| Column | Data Type | Business Meaning | Used in Project | Notes |
|---------|-----------|------------------|-----------------|-------|
| Invoice | String | Transaction (Invoice) identifier | Yes (Transaction Analysis & Data Cleaning) | A single invoice can contain multiple products. |
| StockCode | String | Product identifier | Yes (Product Analysis & Customer Purchasing Behaviour) | The same product can appear in multiple invoices. |
| Description | String | Product name | Yes (Business Reporting & Product Analysis) | Human-readable product description. |
| Quantity | Integer | Number of units purchased | Yes (Customer Behaviour Analysis & Revenue Calculation) | Negative values may represent returns or cancelled transactions. |
| InvoiceDate | String *(to be converted to DateTime)* | Date and time of transaction | Yes (RFM Analysis, Trend Analysis & Time-Series Analysis) | Will be converted to datetime during preprocessing. |
| Price | Float | Unit price of the product | Yes (Revenue Analysis & Monetary Value Calculation) | Used with Quantity to calculate Total Revenue. |
| Customer ID | Float *(Identifier)* | Unique customer identifier | Yes (Customer Segmentation, RFM & Churn Analysis) | Missing values require investigation before customer-level analysis. |
| Country | String | Customer's country | Yes (Geographic Analysis & Dashboard Reporting) | Used for country-wise customer and sales analysis. |

---

# Data Quality Notes

## Initial Data Quality Assessment

| Observation | Status |
|-------------|--------|
| Total Records | 1,067,371 |
| Total Columns | 8 |
| Missing Values in Description | 4,382 |
| Missing Values in Customer ID | 243,007 |
| Missing Values in Other Columns | None observed |
| Negative Quantity Values | Present |
| Negative Price Values | Present |
| InvoiceDate Data Type | Stored as String |
| Dataset Successfully Loaded | Yes |

---

# Cleaning Decisions

**Current Status:** Not Started

No cleaning operations have been performed yet.

The project follows the professional workflow:

```
Understand Data
      ↓
Identify Problems
      ↓
Investigate Problems
      ↓
Make Cleaning Decisions
      ↓
Clean the Data
```

Cleaning decisions will only be made after understanding the cause of missing values, negative values, duplicates, and other data quality issues.

---

# Feature Engineering Notes

**Current Status:** Not Started

Planned derived features include:

- Total Amount = Quantity × Price
- Purchase Year
- Purchase Month
- Purchase Day
- Purchase Hour
- Recency
- Frequency
- Monetary Value (RFM)

Additional engineered features will be documented during the preprocessing stage.

---

# Initial Observations

- The dataset contains over one million retail transaction records collected over approximately two years.
- Each row represents one product purchased within a customer invoice.
- A single invoice can contain multiple products.
- Invoice numbers are not unique because one invoice can include multiple purchased items.
- Customer ID contains missing values that require investigation before customer-level analysis.
- Description contains a small number of missing values.
- InvoiceDate is currently stored as a string and will later be converted into a datetime data type.
- Quantity contains negative values, which may represent product returns or cancelled transactions.
- Price contains negative values, which may represent refunds, adjustments, or data inconsistencies.
- Quantity and Price anomalies will be investigated before making any cleaning decisions.
- The dataset appears suitable for customer analytics, customer segmentation, churn prediction, and business intelligence reporting.

---

# Current Dataset Status

| Task | Status |
|------|--------|
| Dataset Selected | ✅ Completed |
| Dataset Downloaded | ✅ Completed |
| Dataset Organized | ✅ Completed |
| Dataset Loaded into Pandas | ✅ Completed |
| Initial Exploration (`head()`) | ✅ Completed |
| Dataset Structure Analysis (`info()`) | ✅ Completed |
| Statistical Summary (`describe()`) | ✅ Completed |
| Missing Value Analysis | ⏳ In Progress |
| Duplicate Analysis | ⏳ Pending |
| Data Cleaning | ⏳ Pending |
| Feature Engineering | ⏳ Pending |

---

# Version History

| Version | Date | Changes |
|----------|------|---------|
| v1.0 | 26-Jul-2026 | Dataset selected and documented. |
| v1.1 | 27-Jul-2026 | Added dataset structure, column documentation, initial data quality assessment, observations, and project progress after initial data exploration using Pandas (`head()`, `info()`, and `describe()`). |