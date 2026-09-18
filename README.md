# 🏢 El-Morshedy Real Estate — Business-Intelligence

<p align="center">
  <img src="screenshots/dashboard-overview.png" alt="El-Morshedy Real Estate Dashboard" width="900"/>
</p>

<p align="center">
  <b>Data Analysis & Business Intelligence Graduation Project</b>
</p>

<p align="center">
 This project presents an end-to-end Business Intelligence solution developed using Microsoft Power BI.
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

> **One row per customer per installment**

### Core Model Structure

```text
                    ┌──────────────────┐
                    │   Customer Dim   │
                    └────────┬─────────┘
                             │
                             │
┌──────────────────┐         ▼         ┌──────────────────┐
│    Unit Dim      │────► Project Fact ◄──── Payment Dim │
└──────────────────┘         ▲         └──────────────────┘
                             │
                             │
                    ┌────────┴─────────┐
                    │    Date Dim      │
                    └──────────────────┘
