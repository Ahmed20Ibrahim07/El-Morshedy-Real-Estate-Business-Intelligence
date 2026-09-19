# 🏢 El-Morshedy Real Estate — Business-Intelligence

<p align="center">
  <b>Data Analysis & Business Intelligence Graduation Project</b>
</p>

<p align="center">
  This project presents an end-to-end Business Intelligence solution developed using Microsoft Power BI.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Power%20BI-Dashboard-yellow">
  <img src="https://img.shields.io/badge/Star%20Schema-Data%20Model-blue">
  <img src="https://img.shields.io/badge/DAX-13%2B%20Measures-orange">
  <img src="https://img.shields.io/badge/Deneb-Vega-purple">
  <img src="https://img.shields.io/badge/Projects-8-blue">
  <img src="https://img.shields.io/badge/Report%20Pages-35-blue">
  <img src="https://img.shields.io/badge/Status-Complete-brightgreen">
</p>

---

## 📌 Project Overview

El-Morshedy Real Estate sells residential units across multiple projects using multi-year installment plans.

Before this project, sales and collection data were maintained separately for each project in Excel workbooks. This made it difficult to compare projects, monitor overdue installments, analyze payment channels, and obtain a consolidated view of the company's financial position.

This project consolidates **8 residential projects** into a unified Power BI analytical solution.

The dashboard provides a guided, self-service environment to analyze:

- Sales performance
- Sold units
- Project completion
- Invoice amounts
- Collected amounts
- Outstanding balances
- Collection rates
- Installment states
- Cash collections
- Bank collections
- Bank-wise performance
- Customer-level collections

### Projects Covered

1. Degla Palms
2. Degla Landmark
3. Crystal Plaza Maadi
4. Lake
5. Skyline Katameya
6. Rihana
7. Zahra
8. One Katameya

---

# 🎯 Business Problem

The original reporting process faced several challenges:

### 1. Fragmented Data

Each project maintained its own installment and collection data, making cross-project analysis difficult.

### 2. Limited Visibility on Outstanding Amounts

Overdue installments were difficult to identify quickly, limiting the ability to monitor outstanding balances.

### 3. Cash vs. Bank Blind Spot

Cash and bank collections were not easily separated, making payment-channel analysis difficult.

### 4. Manual Reporting

Recurring collection reports had to be rebuilt manually in Excel, resulting in a time-consuming and difficult-to-maintain reporting process.

### Business Need

The project addresses these issues by creating:

> **One refreshable Power BI model that provides a consolidated and interactive view of sales, invoices, collections, and outstanding balances.**

---

# 🎯 Objectives

The main objectives of the project are:

- Provide management with one consolidated view across all eight projects.
- Monitor sold units and project completion.
- Track issued and collected invoices.
- Identify outstanding balances and overdue installments.
- Separate Cash and Bank collections.
- Analyze individual bank performance.
- Analyze customer-level collections.
- Replace recurring manual Excel reporting with a refreshable Power BI solution.
- Provide interactive filtering and guided navigation for business users.

---

# 🛠️ Tools & Technologies

| Tool / Technology | Role |
|---|---|
| **Microsoft Excel** | Source data containing customers, units, sales, installments, payments, and banks |
| **Power Query** | Data importing, cleaning, standardization, and transformation |
| **Power BI Desktop** | Data modeling, relationships, DAX, and dashboard development |
| **DAX** | Business logic and analytical measures |
| **Deneb** | Custom Vega-Lite visualizations |
| **Power BI Service** | Publishing and guided report navigation |

---

# 🏗️ Data Model

The solution uses a **Star Schema architecture**.

Each of the eight projects follows its own project-level star schema consisting of:

- One Installment Fact Table
- Customer Dimension
- Unit Dimension
- Payment Dimension
- Date Dimension

The fact table operates at the grain of:
### Core Model Structure

The solution follows a **Star Schema architecture**.

```mermaid
flowchart TD

C[Customer Dim] --> F[Project Fact]
U[Unit Dim] --> F
P[Payment Dim] --> F
D[Date Dim] --> F

style C fill:#E9E5FF,stroke:#9B7BFF,stroke-width:1px,color:#111
style U fill:#E9E5FF,stroke:#9B7BFF,stroke-width:1px,color:#111
style P fill:#E9E5FF,stroke:#9B7BFF,stroke-width:1px,color:#111
style D fill:#E9E5FF,stroke:#9B7BFF,stroke-width:1px,color:#111
style F fill:#E9E5FF,stroke:#9B7BFF,stroke-width:1px,color:#111
```

The **Project Fact** table acts as the central fact table and is connected to the Customer, Unit, Payment, and Date dimensions.

---

## 🔄 Data Preparation & Transformation

The data preparation process was implemented using Power Query.

The same transformation pipeline was applied across the eight projects to ensure consistency and comparability.

### Power Query Pipeline

1. Import Excel Data
2. Promote Headers
3. Remove Unnecessary Data
4. Change Data Types
5. Clean Text & Values
6. Unpivot Installments (P1–P7)
7. Split Payment Status / Amount
8. Correct Date / Locale
9. Final Cleaned Table

---

## 📐 Key DAX Measures

| Measure | Logic |
|---|---|
| Sold Count | DISTINCTCOUNT of customers who own a unit |
| Sold % | Sold Count ÷ Total Adopted Units |
| Project Completion % | AVERAGE of unit-level POC |
| Total Invoice Amount | SUM of installment amounts |
| Issued Invoices | Paid + Due – Not Paid installments |
| Collected Invoices | Count of Paid installments |
| Collected Amount | SUM of Paid installment amounts |
| Collection Rate | Collected Invoices ÷ Issued Invoices |
| Outstanding Invoices | Issued Invoices − Collected Invoices |
| Outstanding Amount | Total Invoice Amount − Collected Amount |
| Outstanding % | Outstanding Invoices ÷ Issued Invoices |

---

## 📊 Key Project Metrics

| Metric | Value |
|---|---:|
| Report Pages | 35 |
| Projects Covered | 8 |
| Adopted Total Units | 73,943 |
| Sold Count | 3,088 |
| Total Unit Value | 18.64B EGP |
| Total Invoice Amount | 13.88B EGP |
| Collected Amount | 13.09B EGP |
| Outstanding Amount | 791M EGP |
### Sales Metrics

- Adopted Total Units
- Sold Count
- Sold %
- Project Completion %
- Unit Price
- Total Invoice Amount

### Collection Metrics

- Issued Invoices
- Collected Invoices
- Collected Amount
- Collection Rate
- Outstanding Invoices
- Outstanding Amount
- Outstanding %

### Payment Metrics

- Cash Collections
- Bank Collections
- Bank-wise Collections
- Bank-wise Outstanding Amount

### Customer Metrics

- Customer-level Collections
- Customer Concentration
- Customer Counts

---

## 📊 Dashboard Structure

The Power BI solution follows an end-to-end analytical workflow, starting from the raw project data and ending with interactive project-level analysis.

```mermaid
flowchart TD

A[Raw Project Data] --> B[Power Query]
B --> C[Data Cleaning & Transformation]
C --> D[Data Modeling]
D --> E[DAX Measures]
E --> F[Power BI Semantic Model]

F --> G[Project]
G --> H[Global Summary]
H --> I[Collection by Date Summary]

I --> J[Project Views]

J --> K[Overall]
J --> L[Cash]
J --> M[Bank]
J --> N[Bank-wise Analysis]
```

### Dashboard Navigation

The report is structured into the following analytical views:

- **Global Summary** — Consolidated view across all projects.
- **Collection by Date Summary** — Collection analysis over time.
- **Project Views** — Detailed project-level analysis.
- **Overall** — Complete project performance overview.
- **Cash** — Cash collection analysis.
- **Bank** — Bank collection analysis.
- **Bank-wise Analysis** — Detailed comparison across banks.
---

## 📸 Dashboard Preview

### Landing Page

![Landing Page](screenshots/Landing%20Page.png)

### Global Summary

![Global Summary](screenshots/Global%20Summary.png)

### Collection by Date Summary

![Collection by Date Summary](screenshots/Collection%20By%20Date%20Summary.png)

### Project Overall

![Project Overall](screenshots/Project%20Overall.png)

### Cash Analysis

![Cash Analysis](screenshots/Cash%20Analysis%20.png)

### Bank Analysis

![Bank Analysis](screenshots/Bank%20Analysis%20.png)

### Bank-wise Analysis

![Bank-wise Analysis](screenshots/Bank%20Wise%20Analysis%20.png)


---
## 📁 Repository Contents

The repository contains the complete Power BI solution, project documentation, presentation, and dashboard screenshots.

### 📊 Power BI Report

**El-Morshedy Real State.pbix**  
Full interactive Power BI report containing the complete analytical model, DAX measures, and dashboard pages.

### 📑 Project Presentation

**El-Morshedy-Real_Estate-Presentation.pptx**  
Project presentation covering the business problem, methodology, analysis, and key insights.

### 📄 Project Documentation

**El-Morshedy_Project_Documentation.pdf**  
Full project documentation covering the technical implementation, data preparation, data model, DAX measures, and analytical approach.

### 🖼️ Dashboard Screenshots

The `screenshots/` folder contains selected dashboard views:

- Landing Page
- Global Summary
- Collection By Date Summary
- Project Overall
- Cash Analysis
- Bank Analysis
- Bank Wise Analysis

### 📊 Data Source

The project is based on the original Excel data source containing sales, unit, customer, and installment information across the eight residential projects.

The dataset was cleaned and transformed using Power Query before being integrated into the Power BI data model.

**Source file:** `data/El_Morshedy Real Estate Data Source.xlsm`


### 📘 README

**README.md**  
Project documentation and technical overview.

---

## 🚀 Future Scope

The solution can be further extended with:

- Automated refresh with overdue-balance alerts
- Ageing buckets and customer risk scoring
- Forecasting expected monthly collections
- Row-level security per project
- Mobile dashboard layout

---

## 👥 Team Members

This project was developed by:

- **Ahmed Ibrahim**
- **Abdelazzim Ramy**
- **Amina Elsayed**
- **Nada Mohamed**

---

> **One row per customer per installment**
