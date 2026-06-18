# Telco Customer Churn Analysis — Power BI Dashboard

An interactive Power BI dashboard that analyses customer churn for a telecom company, built to answer a question every subscription business faces: **who is leaving, and why?**

![Dashboard preview](dashboard.png)

---

## Overview

Customer churn — the rate at which customers stop doing business with a company — is one of the most important metrics in any subscription industry. Acquiring a new customer typically costs far more than retaining an existing one, so understanding *which* customers are at risk (and what they have in common) directly affects revenue.

This dashboard explores the churn behaviour of **7,032 telecom customers**, surfacing the contract types, services, and payment methods most strongly associated with customers leaving.

## Dataset

- **Source:** IBM Telco Customer Churn — a widely used public sample dataset describing a fictional telecom provider's customers in California.
- **Size:** 7,043 customer records across 21 fields (demographics, account details, services subscribed, and churn status).
- **Cleaning:** 11 records with missing `TotalCharges` values (brand-new customers with zero tenure) were removed during data prep, leaving 7,032 records.

## Tools & Skills

- **Power BI Desktop** — report design and interactivity
- **Power Query** — data import, type correction, and cleaning
- **DAX** — calculated measures for KPIs and churn rate
- **Data visualisation** — KPI cards, donut, bar/column charts, slicers, and a custom theme

## Key Insights

- **~26.6% of customers churned overall** — roughly 1 in 4.
- **Contract type is the strongest signal.** Month-to-month customers churned around **43%**, compared with about **11%** on one-year contracts and just **3%** on two-year contracts.
- **Fiber-optic internet customers** were the most likely to leave (~42%), well above DSL (~19%) and customers with no internet service (~7%).
- **Electronic-check payers** churned the most (~45%) among all payment methods.

**Takeaway:** Contract length and payment method act as powerful early-warning signals. Encouraging month-to-month customers onto longer contracts and reviewing the fiber-optic / electronic-check experience are clear levers for retention.

## Dashboard Features

- Four KPI cards: total customers, churn rate, average tenure, and average monthly charge
- A donut chart showing the overall churned-vs-retained split
- Churn-rate breakdowns by contract type, internet service, and payment method
- Interactive slicers for contract, internet service, and gender — every visual cross-filters on selection

## How It Was Built

1. **Import & clean** the CSV in Power Query; corrected the `TotalCharges` column to a numeric type and removed incomplete records.
2. **Create measures** in DAX for the KPIs and churn rate.
3. **Build visuals** matching a planned layout, then apply a custom theme and formatting for a presentation-ready look.

### Core DAX measures

```DAX
Total Customers = COUNTROWS('Telco-Customer-Churn')

Churned Customers =
CALCULATE([Total Customers], 'Telco-Customer-Churn'[Churn] = "Yes")

Churn Rate = DIVIDE([Churned Customers], [Total Customers])

Avg Monthly Charge = AVERAGE('Telco-Customer-Churn'[MonthlyCharges])

Avg Tenure (Months) = AVERAGE('Telco-Customer-Churn'[tenure])
```

## How to Use

1. Download `Telco-Customer-Churn-Dashboard.pbix` from this repository.
2. Open it in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free).
3. Use the slicers to filter the report and explore churn patterns across segments.

## Repository Contents

| File | Description |
|------|-------------|
| `Telco-Customer-Churn-Dashboard.pbix` | The Power BI report file |
| `dashboard.png` | Preview image of the dashboard |
| `Telco-Customer-Churn.csv` | The source dataset |
| `README.md` | This file |

---

*Built as a portfolio project to demonstrate end-to-end Power BI skills — data cleaning, modelling, DAX, and dashboard design. Dataset credit: IBM sample data.*
