# El-Morshedy Real Estate Business Intelligence

> End-to-end real estate analytics project built with Power BI, Power Query, DAX, and interactive data visualizations.
---

## 📊 Project Overview

This project presents an end-to-end Business Intelligence solution developed using Microsoft Power BI.

The solution consolidates data from 8 residential real estate projects into a unified analytical environment, transforming scattered sales and installment records into interactive dashboards.

The dashboard provides insights into:

- Sales performance
- Invoice amounts
- Collected amounts
- Outstanding balances
- Installment status
- Cash collections
- Bank collections
- Bank-wise performance
- Customer-level collections
- Project completion

The main objective is to provide a single refreshable analytical view that supports data-driven business analysis and reduces reliance on manual reporting.

---

## 🏢 Projects Covered

The solution covers the following residential projects:

- Degla Palms
- Degla Landmark
- Crystal Plaza Maadi
- Lake Front 6
- Skyline Katameya
- Rihana
- Zahra North Coast
- One Katameya

---

## 📈 Key Project Metrics

| Metric | Value |
|---|---:|
| Residential Projects | 8 |
| Report Pages | 35 |
| Model Tables | 51 |
| Sold Contracts | 3,088 |
| Units | 73,943 |
| Invoice Amount | EGP 13.88B |

---

## 🎯 Business Problem

Before the dashboard, collection reporting was fragmented across individual project files and required recurring manual reporting.

### 1. Fragmented Data

Each project maintained its own installment data, making it difficult to obtain a unified company-wide view.

### 2. Limited Arrears Visibility

Overdue installments were difficult to identify quickly, limiting visibility into outstanding balances and collection follow-up.

### 3. Cash vs. Bank Blind Spot

Cash and bank collections were mixed together, making payment-channel analysis difficult.

### 4. Manual Reporting

Reports had to be repeatedly prepared and consolidated, making the process slower and harder to maintain.

---

## 💡 Solution

A centralized Power BI analytical solution was developed with three analytical levels:

```mermaid
flowchart TD

A[Raw Project Data] --> B[Power Query]
B --> C[Data Cleaning & Transformation]
C --> D[Data Modeling]
D --> E[DAX Measures]
E --> F[Power BI Semantic Model]

F --> G[Company Level]
F --> H[Project Level]
F --> I[Payment Channel Level]

G --> G1[Global Summary]
G --> G2[Collection by Date]

H --> H1[Project Overall]
H --> H2[Sales Performance]
H --> H3[Collection Analysis]

I --> I1[Cash]
I --> I2[Bank]
I --> I3[Bank-wise Analysis]
flowchart LR

A[Source Files] --> B[Import]
B --> C[Data Cleaning]
C --> D[Data Transformation]
D --> E[Data Modeling]
E --> F[DAX Measures]
F --> G[Power BI Dashboard]
