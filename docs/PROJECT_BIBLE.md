# Customer IQ & Retention Analytics Platform

> **Project Bible — Single Source of Truth**

---

## 1. Project Identity

**Project Name:** Customer IQ & Retention Analytics Platform

**Project Type:** End-to-End Data Analytics & Customer Intelligence Project

**Project Owner:** Poojitha Maramreddy

**Domain:** Retail / E-commerce Analytics

**Primary Dataset:** Online Retail II

**Current Status:** Analytical and Power BI dashboard development completed

---

# 2. Project Vision

The Customer IQ & Retention Analytics Platform is designed to transform raw retail transaction data into customer and business intelligence.

The platform combines transactional analysis, customer segmentation, churn prediction, and interactive business intelligence dashboards to provide a complete view of customer behavior and business performance.

---

# 3. Business Problem

Businesses can lose customers without clearly understanding:

* Which customers are valuable
* Which customers are loyal
* Which customers are becoming inactive
* Which customers may be at risk of churn
* How customer behavior differs between segments
* Which markets contribute to sales
* How sales performance changes over time

The purpose of this project is to use data-driven analysis to address these questions.

---

# 4. Project Objectives

The project aims to:

1. Understand and clean retail transaction data.
2. Validate the quality of the dataset.
3. Calculate customer-level RFM metrics.
4. Segment customers based on behavior and value.
5. Predict customer churn risk.
6. Analyze churn probability.
7. Identify customers at risk of churn.
8. Analyze sales performance.
9. Analyze geographic sales contribution.
10. Present the results through interactive Power BI dashboards.

---

# 5. Technology Stack

## Programming & Analysis

* Python
* Pandas
* NumPy

## Database & Querying

* SQL

## Machine Learning

* Scikit-learn

## Visualization

* Matplotlib
* Power BI

## Version Control

* Git
* GitHub

---

# 6. Dataset

## Online Retail II

The project uses the Online Retail II dataset containing transaction-level records from an online retailer.

Major fields include:

* Invoice
* StockCode
* Description
* Quantity
* InvoiceDate
* Price
* Customer ID
* Country

The dataset provides the foundation for all customer, sales, RFM, and churn analysis.

---

# 7. Analytical Architecture

The project follows this overall pipeline:

```text
Raw Data
   ↓
Data Understanding
   ↓
Data Cleaning & Validation
   ↓
Feature Engineering
   ↓
Customer-Level Aggregation
   ↓
RFM Analysis
   ↓
Customer Segmentation
   ↓
Churn Prediction
   ↓
Business Metrics
   ↓
Power BI Dashboard
```

---

# 8. Data Layers

## Layer 1 — Raw Transaction Data

Contains the original transaction-level records.

Primary table:

```text
Sales
```

---

## Layer 2 — Customer Analytics

Contains customer-level behavioral metrics.

Primary table:

```text
Customer_RFM
```

Main metrics:

* Customer ID
* Recency
* Frequency
* Monetary
* Segment

---

## Layer 3 — Churn Analytics

Contains model-generated customer churn information.

Primary table:

```text
Churn_Predictions
```

Main fields:

* Customer ID
* Recency
* Frequency
* Monetary
* Churn Probability
* Predicted Churn
* Actual Churn

---

# 9. Feature Engineering

## Total Amount

The transaction value is calculated using:

```text id="q7n4vx"
Total Amount = Quantity × Price
```

This provides the monetary value of each transaction line.

---

# 10. RFM Framework

RFM is the primary customer behavior framework used in this project.

## Recency

How recently the customer purchased.

Lower recency generally indicates a more recent purchase.

## Frequency

How frequently the customer purchased.

Higher frequency indicates more purchasing activity.

## Monetary

How much monetary value the customer generated.

Higher monetary value indicates greater customer contribution.

---

# 11. Customer Segments

The project uses five customer segments:

### Champions

Highly engaged customers with strong purchasing behavior.

### Loyal Customers

Customers who demonstrate consistent purchasing activity.

### Potential Loyalists

Customers showing positive purchasing behavior with potential for stronger loyalty.

### At Risk

Customers whose behavior indicates reduced recent engagement.

### Lost / Hibernating

Customers with relatively weak or inactive purchasing behavior.

These segment definitions are analytical classifications used for the project and should not be interpreted as universal industry standards.

---

# 12. Churn Prediction

The churn component estimates the probability that a customer may churn.

The model produces two primary outputs:

```text
Churn Probability
Predicted Churn
```

### Churn Probability

A probability value representing the model's estimated likelihood of churn.

### Predicted Churn

A binary prediction used to classify customers into predicted churn and non-churn groups.

---

# 13. Churn Probability Bands

The dashboard groups churn probabilities into:

| Band    | Range                         |
| ------- | ----------------------------- |
| 0–20%   | Low predicted risk            |
| 20–40%  | Relatively low predicted risk |
| 40–60%  | Moderate predicted risk       |
| 60–80%  | High predicted risk           |
| 80–100% | Very high predicted risk      |

These bands are dashboard categories and do not represent universal churn-risk thresholds.

---

# 14. Core Business Metrics

The project tracks:

### Sales Metrics

* Total Sales
* Total Quantity
* Total Orders
* Average Order Value

### Customer Metrics

* Total Customers
* Average Recency
* Average Customer Value

### Retention Metrics

* Churn Rate
* At-Risk Customers
* Average Churn Probability

---

# 15. Power BI Dashboard

The final Power BI report contains four pages.

---

## Page 1 — Executive Overview

### Purpose

Provide a high-level view of business performance and customer health.

### Components

* Total Sales
* Total Customers
* Total Orders
* Average Order Value
* Total Quantity
* Sales Trend Over Time
* Customer Segmentation
* Predicted Churn Rate

---

## Page 2 — Customer Intelligence

### Purpose

Analyze customer behavior and value using RFM analysis.

### Components

* Total Customers
* Average Recency
* Average Customer Value
* RFM Customer Distribution
* Customer Value by Segment
* Recency vs Frequency

---

## Page 3 — Churn & Retention

### Purpose

Analyze churn risk and customer retention opportunities.

### Components

* Churn Rate
* At-Risk Customers
* Average Churn Probability
* Churn by Customer Segment
* Churn Probability Distribution
* High-Risk Customer Analysis

---

## Page 4 — Sales & Product Analytics

### Purpose

Analyze sales performance and geographic contribution.

### Components

* Total Sales
* Total Quantity
* Monthly Sales Trend
* Sales by Country

---

# 16. Dashboard Design System

The dashboard follows a consistent visual design.

## Background

```text
#071A2F
```

## Visual Panels

```text
#123B3A
```

## Primary Accent

```text
#00D4FF
```

## Accent Colors

```text
#22C55E
#A855F7
#FFB000
#FF5C8A
```

## Text

```text
#FFFFFF
#D5E3E8
#7FD8E8
```

### Design Principles

* Strong contrast
* Consistent typography
* Consistent spacing
* Minimal unnecessary visuals
* Clear section hierarchy
* Business-focused visualizations
* Consistent color meaning across pages

---

# 17. Important DAX Measures

## Total Quantity

```DAX id="m2x8qa"
Total Quantity = SUM(Sales[Quantity])
```

## Total Sales

```DAX id="k5r1dz"
Total Sales = SUM(Sales[Total Amount])
```

## Total Orders

```DAX id="p9v3ht"
Total Orders = DISTINCTCOUNT(Sales[Invoice])
```

## Average Order Value

```DAX id="c6w4bn"
Average Order Value =
DIVIDE([Total Sales], [Total Orders])
```

## Average Recency

```DAX id="a8q2mf"
Average Recency =
AVERAGE(Customer_RFM[Recency])
```

## Average Customer Value

```DAX id="j4s7xp"
Average Customer Value =
AVERAGE(Customer_RFM[Monetary])
```

## At-Risk Customers

```DAX id="n1v6kc"
At-Risk Customers =
CALCULATE(
    COUNTROWS(Churn_Predictions),
    Churn_Predictions[Predicted_Churn] = 1
)
```

## Average Churn Probability

```DAX id="z3t8wy"
Average Churn Probability =
AVERAGE(Churn_Predictions[Churn_Probability])
```

## Churn Rate

```DAX id="r7m5hq"
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

# 18. Project Folder Structure

The project currently follows:

```text
Customer-IQ-Retention-Analytics/
│
├── data/
│
├── docs/
│   ├── DATASET_DOCUMENTATION.md
│   ├── ENGINEERING_DIARY.md
│   └── PROJECT_BIBLE.md
│
├── notebooks/
│
├── powerbi/
│
└── .gitignore
```

The structure may evolve as additional project artifacts are finalized.

---

# 19. Documentation System

The documentation folder has three main purposes.

## DATASET_DOCUMENTATION.md

Documents:

* Dataset source
* Dataset structure
* Columns
* Derived fields
* RFM data
* Churn data
* Data quality considerations

## ENGINEERING_DIARY.md

Records:

* Development stages
* Technical decisions
* Implementation work
* Lessons learned
* Project progress

## PROJECT_BIBLE.md

Acts as the project's single source of truth for:

* Project vision
* Architecture
* Technologies
* Analytical methodology
* Dashboard structure
* Metrics
* Design system
* Folder structure

---

# 20. Project Completion Criteria

The project is considered complete when the following are available:

* [x] Dataset documented
* [x] Data cleaned and validated
* [x] Customer-level RFM analysis
* [x] Customer segmentation
* [x] Churn prediction
* [x] Churn analysis
* [x] Business metrics
* [x] Power BI dashboard
* [x] Project documentation
* [ ] Final repository organization
* [ ] README documentation
* [ ] GitHub publication
* [ ] Final project validation

---

# 21. Future Improvements

Possible future improvements include:

* Automated data pipelines
* Scheduled model retraining
* Additional customer lifetime value analysis
* Advanced churn modeling
* Model performance monitoring
* Automated dashboard refresh
* Customer-level retention recommendations
* Deployment of the analytical workflow

These are future possibilities and are not considered part of the current completed scope.

---

# 22. Final Project Philosophy

The project follows a simple principle:

> **Turn raw transaction data into understandable customer and business intelligence.**

The project should remain:

* Reproducible
* Documented
* Explainable
* Business-focused
* Technically organized
* Honest about implemented functionality
