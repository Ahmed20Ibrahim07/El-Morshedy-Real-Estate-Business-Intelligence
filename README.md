# El-Morshedy Real Estate — BI Dashboard

A Power BI Business Intelligence solution for tracking installment sales and collections across **8 residential real estate projects**, replacing fragmented Excel reporting with a single, governed, refreshable data model.

> Graduation Project — Data Analysis & Business Intelligence
> September 2026

---

## 📌 Overview

El-Morshedy Real Estate sells residential units across eight independent projects on multi-year installment plans. Before this project, each project's sales and collections were tracked in separate Excel workbooks — making it impossible to compare portfolios, spot overdue installments early, or separate cash from bank performance.

This project consolidates all eight project portfolios into **one Power BI model** and a guided, self-service dashboard showing what has been sold, invoiced, collected, and what remains outstanding — company-wide and per project.

**Projects covered:** Degla Palms · Degla Landmark · Crystal Plaza Maadi · Lake · Skyline Katameya · Rihana · Zahra · One Katameya

---

## 🎯 Objectives

- Give management one consolidated view of collections across all eight projects
- Surface overdue installments early for the collections team to act on
- Separate cash from bank collections, and rank individual banks by performance
- Replace manual, recurring Excel reporting with a refreshable Power BI model
- Track sold units, project completion %, and outstanding balances at a glance

---

## 🧰 Tools & Technologies

| Tool | Role |
|---|---|
| Microsoft Excel | Source system (customers, units, sales, installments, payments, banks) |
| Power Query | Importing, cleaning, standardizing, and reshaping 8 source workbooks |
| Power BI Desktop | Star-schema data modeling, relationships, DAX layer |
| DAX | All business logic — sales, collection, and outstanding measures |
| Deneb (custom visual) | Vega-Lite powered collection-rate curves by installment number |
| Power BI Service | Publishing and guided navigation |

---

## 🏗️ Data Model

Each of the 8 projects is modeled as its own **star schema**: one installment fact table (grain: one row per customer per installment) joined to four dimension tables — Customer, Unit, Payment, and Date.

**Power Query pipeline (9 stages, applied per project):**
1. Import Excel Data
2. Promote Headers
3. Remove Unnecessary Data
4. Change Data Types
5. Clean Text & Values
6. Unpivot Installments (P1–P7 → Installment Number / Value)
7. Split Payment Status / Amount
8. Correct Date / Locale
9. Final Cleaned Table

The 8 independent project stars roll up into a **company-wide Global Summary** using `TREATAS` to simulate cross-model filtering, since the project fact tables have no physical relationship to each other.

---

## 📐 Key DAX Measures

| Measure | Logic |
|---|---|
| `Sold Count` | `DISTINCTCOUNT` of customers who own a unit |
| `Sold %` | Sold Count ÷ total adopted units |
| `Project Completion %` | `AVERAGE` of unit-level POC (construction progress) |
| `Collection Rate` | Collected Invoices ÷ Issued Invoices |
| `Outstanding Amount` | Total Invoice Amount − Collected Amount |
| `Outstanding %` | Outstanding Invoices ÷ Issued Invoices |

Also handled: duplicate-row prevention after unpivoting, `REMOVEFILTERS` for fixed-denominator ratios, and project-name standardization across inconsistently labeled source files.

---

## 📊 Dashboard Structure (35 pages)

- **Landing Page** — 11 navigation buttons to every part of the model
- **Global Summary** — cross-project pivot: Units, Sold %, Unit Price, Collected, Outstanding, per project
- **Collection by Date Summary** — collection trend across NEW/OLD periods, with a Date slicer
- **8 × Project pages** (Overall / Cash / Bank / Bank-wise), each with:
  - KPI cards (Sold Count, Project Completion %, Adopted Units)
  - Donut chart of Installment State by Payment Method
  - Deneb collection-rate curves by installment number
  - Bank-wise ranking of collected vs. outstanding value

---

## 💡 Key Insights

- **Collection rate is the real health signal** — a project can be nearly fully sold while collections lag behind
- **Outstanding balance concentrates in later installments** — arrears build up over the payment schedule
- **Channel mix changes the risk profile** — cash vs. bank performance differs, and some banks settle more reliably than others
- **A small set of customers drives the outstanding balance** — a short priority list covers most of it

---

## 📁 Repository Contents
