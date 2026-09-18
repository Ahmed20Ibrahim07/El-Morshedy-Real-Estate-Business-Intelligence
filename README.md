# El-Morshedy Real Estate — Installment Sales & Collections Analytics

**A Power BI collection intelligence solution covering 8 residential real estate projects — from 8 fragmented Excel workbooks to a governed multi-star-schema model and a 35-page guided report.**

![Power BI](https://img.shields.io/badge/Power%20BI-Star%20Schema-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-13%2B%20Measures-005A9C?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-2E7D32?style=flat-square)

---

## 🎯 The Business Problem

El-Morshedy Real Estate sells units across 8 concurrent projects using multi-year installment plans. Before this project, each project kept its own Excel workbook, and management had no single, reliable way to answer:

- What has become **due**, what has actually been **collected**, and what remains **outstanding**?
- Where are overdue installments concentrated — before it's too late to act on them?
- How does **cash** collection compare to **bank** collection — and how do individual banks perform against each other?
- How does each project's **sales progress** compare to its actual **collection health**?

This solution answers all four — with drill-down from a company-wide view down to a single bank's performance on a single project.

---

## 📊 Results at a Glance

| Metric | Value |
|---|---|
| Projects unified into one model | **8** |
| Report pages | **35** |
| Tables across the combined star schemas | **~51** |
| Core DAX measures (per-project, replicated 8×) | **13** |
| Payment channels tracked | **Cash / Bank / Bank-wise** |
| Installment states classified | **Paid / Due – Not Paid / Not Due** |

---

A user opens the **Landing Page**, checks the portfolio-wide numbers on **Global Summary**, compares collection trends over time on **Collection by Date Summary**, then drills into any of the 8 projects. Every project exposes the same four views — **Overall → Cash → Bank → Bank-wise** — so the reading experience is identical across all 8 portfolios.

---

## 🖼️ Walkthrough

*(Add screenshots to a `/screenshots` folder and update the paths below.)*

### 1. Landing Page — 11 navigation buttons to every part of the model
`screenshots/01-landing.png`

### 2. Global Summary — One row per project, company-wide KPIs
`screenshots/02-global-summary.png`

### 3. Collection by Date Summary — Old vs. New period comparison
`screenshots/03-collection-by-date.png`

### 4. Project — Overall — KPI cards, installment matrix, donut chart
`screenshots/04-project-overall.png`

### 5. Project — Cash — Collection rate & collected vs. outstanding curves by installment number
`screenshots/05-project-cash.png`

### 6. Project — Bank — Same view, filterable by individual bank
`screenshots/06-project-bank.png`

### 7. Project — Bank-wise — Collected vs. outstanding ranked by bank
`screenshots/07-project-bankwise.png`

### 8. Data Model — Star schema (Degla Palms example)
`screenshots/08-data-model.png`

---

## 🏗️ Data Model (Star Schema)

Each of the 8 projects is modeled as its **own independent star schema**:

**Key modeling decisions:**
- Installments were exported **wide** (P1–P7 columns) and **unpivoted** into a long `Installment Number` / `Value` structure, so one DAX measure works across any installment number, for any project
- `TREATAS` simulates a relationship between the Projects table and each independent project fact table, since no physical relationship exists between the 8 stars
- `REMOVEFILTERS` keeps fixed-denominator ratios (like `Sold %`) stable as the user applies slicers
- `DISTINCTCOUNT` (not `COUNTROWS`) is used for all customer-level counts, to avoid duplicate-row inflation after the unpivot
- Project names were standardized in Power Query to resolve Arabic/English and spelling inconsistencies across the 8 source files

---

## 📐 Report Architecture

---

## 🛠️ Tech Stack

- **Power BI Desktop** — star-schema data modeling, DAX, report design
- **Power Query (M)** — 9-stage cleaning pipeline: header promotion, type correction, text cleaning, installment unpivot, payment-status split, date/locale correction
- **DAX** — 13 core measures (Sold Count, Sold %, Project Completion %, Collection Rate, Outstanding Amount/%, etc.), replicated per project and rolled up to Global
- **Deneb (Vega-Lite custom visual)** — collection-rate curves and collected-vs-outstanding curves by installment number, not achievable with native Power BI visuals

---

## 💡 Key Insights

- **Collection rate is the real health signal** — a project can be nearly fully sold while its collection rate lags behind
- **Outstanding balance concentrates in later installments** — arrears build up as the payment schedule progresses
- **Channel mix changes the risk profile** — cash and bank collections behave differently, and bank-wise ranking exposes which partners settle reliably
- **A small set of customers drives the outstanding balance** — a short priority list covers a large share of it

---

## 📁 Repo Contents

- `El-Morshedy_Real_State.pbix` — full interactive Power BI report
- `El-Morshedy-Real_Estate-Presentation.pptx` — project presentation deck
- `El-Morshedy_Project_Documentation.pdf` — full written project documentation
- `/screenshots` — dashboard walkthrough (add after export)

---

## 🚀 Future Scope

- Automated refresh with overdue-balance alerts
- Ageing buckets & customer risk scoring
- Forecasting expected monthly collections from the remaining schedule
- Row-level security per project + a mobile layout for the field team

---

## 👥 About This Project

This graduation project applies a real-world real estate business case — a company selling units across 8 concurrent projects on multi-year installment plans — to build a governed BI solution. It consolidates 8 independently maintained Excel workbooks into one comparable model spanning ~51 tables and 35 report pages.

**Team:** Ahmed Ibrahim · Abdelazzim Ramy · Amina Elsayed · Nada Mohamed

**Acknowledgment:** Special thanks to our instructor, **[Instructor's Name]**, for the guidance and support throughout this project.
## 🧭 How to Navigate This Report

The report is built around one idea: **start company-wide, then zoom into a project and a channel.**
