# Engineering Diary

## Customer IQ & Retention Analytics Platform

This document records the major development stages, decisions, implementation work, and lessons learned while building the Customer IQ & Retention Analytics Platform.

---

## Project Objective

The objective of this project is to build an end-to-end customer intelligence and retention analytics platform using retail transaction data.

The platform combines:

* Data cleaning and validation
* Customer behavior analysis
* RFM analysis
* Customer segmentation
* Churn prediction
* Business metrics
* Geographic sales analysis
* Interactive Power BI dashboards

The final goal is to transform raw transaction data into actionable customer and business insights.

---

# Development Timeline

## Phase 1 — Project Setup

### Objective

Establish the initial project structure and organize the project resources.

### Project Structure

```text id="n8r6h4"
Customer-IQ-Retention-Analytics/
│
├── data/
├── docs/
├── notebooks/
├── powerbi/
└── .gitignore
```

### Key Decisions

* Keep raw and processed data organized under the `data` directory.
* Keep analytical notebooks under `notebooks`.
* Keep project documentation under `docs`.
* Keep Power BI files under `powerbi`.
* Use `.gitignore` to prevent unnecessary or sensitive files from being committed.

---

# Phase 2 — Data Understanding

## Objective

Understand the structure and characteristics of the Online Retail II dataset before performing analysis.

### Activities

* Loaded the dataset using Python and Pandas.
* Inspected the first records.
* Examined dataframe structure.
* Checked column names and data types.
* Reviewed dataset dimensions.
* Examined descriptive statistics.
* Identified potential data quality issues.

### Key Learning

The dataset is transaction-level data rather than customer-level data.

Therefore, customer analytics requires aggregation of transaction records into customer-level metrics.

---

# Phase 3 — Data Cleaning & Validation

## Objective

Prepare the transaction data for reliable analysis.

### Areas Investigated

* Missing values
* Duplicate records
* Invalid quantities
* Invalid prices
* Missing customer identifiers
* Cancelled transactions
* Data type consistency
* Transaction values
* Date fields

### Validation Principle

Data should be validated before calculating business metrics or building machine learning models.

The cleaning process focuses on preserving valid business information while removing or handling records that could distort analytical results.

---

# Phase 4 — Feature Engineering

## Transaction-Level Feature

A transaction value field was created:

```text id="1glg75"
Total Amount = Quantity × Price
```

This field provides the monetary value of each transaction line.

It is later used for:

* Total Sales
* Customer Monetary Value
* Sales analysis
* Customer segmentation
* Dashboard KPIs

---

# Phase 5 — RFM Analysis

## Objective

Convert transaction-level behavior into customer-level behavioral metrics.

RFM stands for:

### Recency

Measures how recently a customer made a purchase.

### Frequency

Measures how frequently a customer purchases.

### Monetary

Measures how much monetary value a customer generates.

### Customer-Level RFM

Each customer receives:

```text id="q3y2pt"
Customer ID
Recency
Frequency
Monetary
```

These metrics form the foundation for customer segmentation.

---

# Phase 6 — Customer Segmentation

## Objective

Group customers according to their purchasing behavior and value.

The project uses the following customer segments:

* Champions
* Loyal Customers
* Potential Loyalists
* At Risk
* Lost / Hibernating

### Purpose

Segmentation makes it easier to understand customer groups and identify where retention efforts may be relevant.

The segments are visualized in the Power BI Customer Intelligence dashboard.

---

# Phase 7 — Churn Prediction

## Objective

Estimate which customers may be at risk of churn.

The churn prediction dataset contains customer-level behavioral features including:

* Recency
* Frequency
* Monetary
* Churn Probability
* Predicted Churn
* Actual Churn

### Model Output

The model produces:

```text id="x3i0n8"
Churn Probability
Predicted Churn
```

The probability represents the model's estimated likelihood of churn.

The predicted churn field provides a binary classification used for dashboard analysis.

---

# Phase 8 — Churn Analysis

## Objective

Translate churn model output into business-friendly analysis.

The project calculates:

* Churn Rate
* At-Risk Customers
* Average Churn Probability
* Churn Probability Bands

### Churn Probability Bands

```text id="z8f7c2"
0–20%
20–40%
40–60%
60–80%
80–100%
```

These groups make it easier to understand the distribution of predicted churn risk.

---

# Phase 9 — Power BI Data Model

## Objective

Build the analytical layer for interactive reporting.

The Power BI project uses the following major tables:

```text id="j6n4wm"
Sales
Customer_RFM
Churn_Predictions
```

### Sales

Contains transaction-level information.

### Customer_RFM

Contains customer-level RFM metrics and customer segments.

### Churn_Predictions

Contains customer-level churn predictions and risk information.

---

# Phase 10 — Power BI Measures

Important measures created for the dashboard include:

### Total Quantity

```DAX id="b2k1qv"
Total Quantity = SUM(Sales[Quantity])
```

### Total Sales

```DAX id="f5r8mx"
Total Sales = SUM(Sales[Total Amount])
```

### Total Orders

```DAX id="a1w9kc"
Total Orders = DISTINCTCOUNT(Sales[Invoice])
```

### Average Order Value

```DAX id="d7p3ls"
Average Order Value =
DIVIDE([Total Sales], [Total Orders])
```

### Average Recency

```DAX id="h4t6ny"
Average Recency =
AVERAGE(Customer_RFM[Recency])
```

### Average Customer Value

```DAX id="m9q2rx"
Average Customer Value =
AVERAGE(Customer_RFM[Monetary])
```

### At-Risk Customers

```DAX id="c8v1za"
At-Risk Customers =
CALCULATE(
    COUNTROWS(Churn_Predictions),
    Churn_Predictions[Predicted_Churn] = 1
)
```

### Average Churn Probability

```DAX id="r5k7bd"
Average Churn Probability =
AVERAGE(Churn_Predictions[Churn_Probability])
```

### Churn Rate

```DAX id="e3n6pq"
Churn Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS(Churn_Predictions),
        Churn_Predictions[Predicted_Churn] = 1
    ),
    COUNTROWS(Churn_Predictions)
)
```

---

# Phase 11 — Power BI Dashboard Development

## Dashboard Page 1 — Executive Overview

Purpose:

Provide a high-level summary of business performance and customer health.

Key elements:

* Total Sales
* Total Customers
* Total Orders
* Average Order Value
* Total Quantity
* Sales Trend Over Time
* Customer Segmentation
* Predicted Churn Rate

---

## Dashboard Page 2 — Customer Intelligence

Purpose:

Understand customer behavior and value using RFM analysis.

Key elements:

* Total Customers
* Average Recency
* Average Customer Value
* RFM Customer Distribution
* Customer Value by Segment
* Recency vs Frequency

---

## Dashboard Page 3 — Churn & Retention

Purpose:

Analyze customer churn risk and identify customers requiring attention.

Key elements:

* Churn Rate
* At-Risk Customers
* Average Churn Probability
* Churn by Customer Segment
* Churn Probability Distribution
* High-Risk Customer Analysis table

---

## Dashboard Page 4 — Sales & Product Analytics

Purpose:

Analyze sales performance and geographic contribution.

Key elements:

* Total Sales
* Total Quantity
* Monthly Sales Trend
* Sales by Country

---

# Phase 12 — Dashboard Design

A consistent visual theme was used across all dashboard pages.

### Primary Background

```text id="r8c4mv"
#071A2F
```

### Visual Panel Background

```text id="k2x7np"
#123B3A
```

### Main Accent

```text id="s4d9qa"
#00D4FF
```

### Supporting Colors

```text id="t6y1bc"
Green  → #22C55E
Purple → #A855F7
Gold   → #FFB000
Coral  → #FF5C8A
```

### Text Colors

```text id="u3m8zf"
White        → #FFFFFF
Light Text   → #D5E3E8
Subtitle     → #7FD8E8
```

The design goal was to maintain strong visual contrast while keeping all dashboard pages consistent.

---

# Engineering Decisions

## Decision 1 — Customer-Level Analysis

Transaction-level data alone is not sufficient for retention analysis.

Therefore, transaction records were aggregated into customer-level metrics before performing RFM and churn analysis.

---

## Decision 2 — RFM as a Segmentation Framework

RFM was selected because it provides a practical way to describe customer behavior using purchase recency, purchase frequency, and monetary contribution.

---

## Decision 3 — Separate Churn Predictions

Churn predictions were maintained in a separate customer-level table rather than mixing prediction outputs directly into the transaction-level dataset.

This keeps transaction data and model outputs logically separated.

---

## Decision 4 — Power BI for Business Reporting

Power BI was selected as the reporting layer because it supports:

* Interactive filtering
* KPI visualization
* Customer segmentation
* Churn analysis
* Geographic analysis
* Business-friendly dashboards

---

# Current Project Status

## Completed

* [x] Project structure
* [x] Dataset understanding
* [x] Data cleaning and validation
* [x] Transaction-level feature engineering
* [x] RFM analysis
* [x] Customer segmentation
* [x] Churn prediction
* [x] Churn analysis
* [x] Power BI measures
* [x] Executive dashboard
* [x] Customer intelligence dashboard
* [x] Churn & retention dashboard
* [x] Sales & product analytics dashboard

## Current Stage

The analytical and Power BI dashboard components are complete.

The remaining work focuses on project documentation, repository organization, final validation, and GitHub publication.

---

# Lessons Learned

Throughout the project, several important concepts were reinforced:

1. Data understanding should happen before modeling.
2. Data quality directly affects analytical results.
3. Transaction-level data often needs customer-level aggregation for customer analytics.
4. RFM provides a useful framework for understanding customer behavior.
5. Machine learning outputs should be translated into business-friendly metrics.
6. Dashboard design should prioritize readability and business questions.
7. Consistent visual design improves dashboard usability.
8. Documentation is an important part of a complete data analytics project.

---

# Final Project Flow

```text id="v6h3ks"
Online Retail II
       ↓
Data Understanding
       ↓
Data Cleaning & Validation
       ↓
Feature Engineering
       ↓
RFM Analysis
       ↓
Customer Segmentation
       ↓
Churn Prediction
       ↓
Business Metrics
       ↓
Power BI Dashboards
       ↓
Customer & Business Insights
```
