# Enterprise Financial & Profitability Dashboard

## Overview
This **Power BI Dashboard** provides a comprehensive analysis of enterprise financial performance, tracking total revenue, operational expenses, net profit, and budget variance across different business regions, departments, and timeframes. Designed with a clean, professional, and accessible UI, this interactive dashboard helps stakeholders identify revenue trends, monitor departmental spending, and make data-driven financial decisions.

---

## Key Performance Indicators (KPIs)
- **Total Revenue:** Displays the aggregated gross revenue generated across all transactions ($3.1M+).
- **Total Expenses:** Highlights total operational and departmental expenditures ($1.8M+).
- **Net Profit:** Evaluates bottom-line profitability calculated as `Total Revenue - Total Expenses` ($1.3M+).
- **Budget Variance:** Tracks financial adherence against planned budget allocations.

---

## Interactive Features & Visualizations
1. **Monthly Revenue Trends (Column Chart):**
   - Displays month-by-month revenue breakdowns from January to December.
   - Built-in **Drill-Down Capabilities** (Year > Quarter > Month) for deep-dive granular analysis.
2. **Regional Profitability (Bar Chart):**
   - Comparative view of Net Profit across distinct geographic operating regions (e.g., APAC, Europe, North America).
3. **Departmental Expense Breakdown (Donut Chart):**
   - Visual distribution showing how operating expenses are allocated across company departments (e.g., Human Resources, IT, Sales).
4. **Dynamic Slicers & Filters:**
   - Interactive filtering by **Region Name**, **Department Name**, and **Date Hierarchy** (Year/Quarter/Month) for instant report recalculation.

---

## Data Model & DAX Formulas
The data structure follows a **Star Schema** linking fact tables (`Fact_Transactions`, `Fact_Budget`) with core dimension tables (`Dim_ChartOfAccounts`, `Dim_Department`, `Dim_Region`, `Dim_Date`).

### Core Measures:
```dax
// Total Revenue Measure
Total Revenue = CALCULATE(
    SUM(Fact_Transactions[Amount]),
    Dim_ChartOfAccounts[Account_Type] = "Revenue"
)

// Total Expenses Measure
Total Expenses = CALCULATE(
    SUM(Fact_Transactions[Amount]),
    Dim_ChartOfAccounts[Account_Type] = "Expenses"
)

// Net Profit Calculation
Net Profit = [Total Revenue] - [Total Expenses]

// Budget Variance Calculation
Budget Variance = SUM(Fact_Budget[Budget_Amount]) - [Total Expenses]
