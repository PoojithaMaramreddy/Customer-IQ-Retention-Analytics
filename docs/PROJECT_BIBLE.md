# Customer IQ & Retention Analytics Platform

## Project Information

Project Name:
Customer IQ & Retention Analytics Platform

Status:
Sprint 2 - Data Understanding (In Progress)

Selected Dataset:
Online Retail II

Started On:
25 July 2026

Version:
0.8

Last Updated:
26 July 2026

Project Owner:
Poojitha Maramreddy

---

## Project Goal

Develop an end-to-end Customer Intelligence and Retention Analytics Platform that helps businesses understand customer behavior, segment customers using RFM analysis, predict customer churn, and provide actionable business insights through analytics, machine learning, and interactive dashboards.

---

## Problem Statement

Businesses often lose valuable customers without understanding why they leave. This project aims to analyze customer behavior, identify customer segments, predict customers who are likely to churn, and help businesses make better retention decisions using data-driven insights.

---

## Dataset

Name: Online Retail II

Source: Kaggle

Original Source: UCI Machine Learning Repository

Status:
Downloaded

---

## Tech Stack

(To be decided)

---

## Project Workflow

Business Understanding
        ↓
Dataset Selection
        ↓
Data Cleaning
        ↓
Exploratory Data Analysis (EDA)
        ↓
Customer Segmentation (RFM)
        ↓
Churn Prediction
        ↓
Business Insights
        ↓
Power BI Dashboard
        ↓
Deployment

---

## Version History

### v0.1 - Project Initialization
- Project initialized
- Folder structure created
- Documentation setup

### v0.2 - Dataset Fundamentals
- Learned dataset fundamentals
- Understood rows, columns, features, and target variables
- Started the Engineering Diary

### v0.3 - Business Understanding (Part 1)
- Started Sprint 1 - Business Understanding
- Learned where customer data comes from
- Understood public datasets and why they are used
- Learned the difference between identifier columns and behavioural features
- Defined dataset selection criteria

### v0.4 - Data Sources
- Learned different types of data sources
- Understood the differences between CSV, Excel, Databases, and Data Warehouses
- Learned the complete data flow from customer transactions to business insights
- Improved project documentation

### v0.5 - Dataset Evaluation
- Compared different types of customer datasets
- Evaluated datasets based on business requirements
- Decided that a transaction-based retail dataset best fits the project goals
- Prepared evaluation criteria for selecting the final Kaggle dataset

### v0.6 - Introduction to Kaggle
- Learned about Kaggle and its role in Data Science projects
- Understood Kaggle datasets, notebooks, competitions, and learning resources
- Established the process for evaluating datasets before selection

### v0.7
- Explored the Kaggle platform and understood its purpose
- Learned how to evaluate a dataset before downloading it
- Understood the importance of Dataset Description, License, and Usability Score
- Studied the business context of the Online Retail II dataset
- Learned business metadata such as business type, store type, customer type, country, products sold, and time period
- Understood the concept of Attribute Information
- Learned the difference between Programming Data Types and Statistical Data Types
- Understood Nominal and Numeric data types

### v0.8

- Downloaded the Online Retail II dataset
- Organized the project data directory
- Started Sprint 2 – Data Understanding

---

## Candidate Dataset

| Dataset | Status | Reason |
|----------|--------|--------|
| Telecom Customer Churn | Rejected | Does not support RFM analysis and lacks transaction history. |
| Bank Customer Churn | Rejected | Focused on banking attributes rather than customer purchase behaviour. |
| E-commerce Customer Behavior | Rejected | Contains behavioural data but does not fully support the business objectives of this project. |
| Online Retail II | **Selected** | Supports RFM analysis, customer segmentation, feature engineering, business analytics, and churn analysis. Selected as the final dataset for the project. |


---
## Milestones

- [x] Project Name
- [x] Project Folder Created
- [x] Initial Folder Structure
- [x] Sprint 0 - Project Foundation
- [x] Sprint 1 - Business Understanding
- [x] Dataset Selected (Online Retail II)
- [ ] Data Understanding
- [ ] Data Cleaning & Preprocessing
- [ ] Exploratory Data Analysis (EDA)
- [ ] Feature Engineering
- [ ] RFM Analysis
- [ ] Customer Segmentation
- [ ] Churn Prediction
- [ ] Business Insights
- [ ] Power BI Dashboard
- [ ] Deployment

---

## Overall Progress

Sprint 0 - ✅ Completed

Sprint 1 - 🟡 In Progress

Sprint 2 - ⬜ Pending

Sprint 3 - ⬜ Pending

Sprint 4 - ⬜ Pending

Sprint 5 - ⬜ Pending

---

## Decisions Log

25 July 2026

Decision 1:
Project documentation will be maintained using Markdown files.

Reason:
Easy to maintain, GitHub-friendly, and widely used in software development.

---

Decision 2:
Identifier columns will not be considered useful predictive features for machine learning models.

Reason:
They uniquely identify records but do not describe customer behaviour.

---

Decision 3:
The project will use a publicly available Kaggle dataset.

Reason:
Real company production databases contain sensitive customer information and cannot be accessed publicly. Kaggle provides realistic datasets suitable for learning and portfolio projects.

---

Decision 4:
The project dataset will initially be downloaded in CSV format.

Reason:
CSV files are lightweight, easy to use with Python, SQL, and Power BI, and are the most common format for Kaggle datasets.

---

Decision 5:
Engineering documentation will be updated after every completed lesson.

Reason:
Keeping documentation updated throughout the project improves maintainability, tracks project progress, and reflects professional software engineering practices.

---

26 July 2026

Decision 6:
The project will use a transaction-based retail dataset instead of a dataset with a pre-defined churn label.

Reason:
A transaction dataset supports RFM analysis, customer segmentation, feature engineering, business analytics, and allows churn to be defined using business rules. This aligns better with the objectives of the Customer IQ & Retention Analytics Platform.

---

Decision 7:
The project dataset will be selected only after evaluating multiple Kaggle datasets.

Reason:
Choosing the right dataset is critical for achieving the project's business goals. The selected dataset must support RFM analysis, customer segmentation, churn analysis, and business insights instead of being chosen simply because it is popular.

---

26 July 2026

Decision 8:
Before downloading any dataset, the dataset page will be thoroughly explored and evaluated.

Reason:
Understanding the dataset's description, columns, source, and suitability helps ensure that the selected data aligns with the project's business objectives and avoids unnecessary rework later.

---

Decision 9:
The Online Retail II dataset is selected as the primary candidate dataset for the project because it aligns with the business objectives.

Reason:
The dataset contains approximately two years of customer transaction history, making it suitable for customer behaviour analysis, RFM analysis, customer segmentation, and churn prediction. It is publicly available, legally usable for learning, and contains the required business information for the project.
---

Decision 10:

The original dataset will always be preserved inside the
data/raw folder.

Reason:
Raw data should never be modified. All cleaning and
transformations will be performed on copies stored in the
processed folder.
---