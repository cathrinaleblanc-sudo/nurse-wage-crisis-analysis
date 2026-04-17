# nurse-wage-crisis-analysis
Analyzing the nurse wage crisis in America using BLS government data | SQL · BigQuery · Tableau
# 🏥 Burned Out & Underpaid: The Nurse Wage Crisis in America

## Overview
This project analyzes 3 years of real Bureau of Labor Statistics (BLS) data to investigate 
whether nurse wages are keeping up with the demands placed on them — and whether wage 
stagnation is contributing to the nursing shortage crisis across America.

> **Central Question:** Are hospitals hiring more nurses without paying them more?

**Tools:** SQL · Google BigQuery · Tableau Public · Python (data prep) · GitHub

---

## Dataset
- **Source:** Bureau of Labor Statistics — Occupational Employment and Wage Statistics (OEWS)
- **Years:** May 2022, May 2023, May 2024
- **Records:** 597 rows across 4 nurse roles, all 50 states + DC
- **Roles analyzed:** Registered Nurses, LPN/LVN, Nurse Practitioners, Nurse Anesthetists

---

## Advanced SQL Techniques Used
- **CTEs (Common Table Expressions)** — multi-step wage growth calculations
- **Window Functions: RANK()** — ranking all 50 states by RN wage
- **Window Functions: LAG()** — year-over-year wage change by state
- **CASE WHEN** — classifying states as "Hiring faster than paying" vs inverse
- **JOINs** — combining 2022 and 2024 CTEs to calculate % growth

---

## Key Questions & Findings

### 1. Are nurse wages actually growing?
Yes — but unevenly. LPN/LVNs got the biggest % raise (14.6%) but still earn just 
$63,900 — the lowest of all nurse roles. Nurse Practitioners got the smallest raise 
(7.6%) despite being among the highest skilled.

| Nurse Role | 2022 Avg Wage | 2024 Avg Wage | % Increase |
|---|---|---|---|
| LPN/LVN | $55,740 | $63,900 | +14.6% |
| Registered Nurses | $83,852 | $93,431 | +11.4% |
| Nurse Anesthetists | $207,246 | $227,450 | +9.7% |
| Nurse Practitioners | $120,835 | $130,028 | +7.6% |

### 2. Does your state determine your nurse salary?
Dramatically yes — nearly a $50,000 gap between the highest and lowest paying states.

| Rank | State | Annual Mean Wage |
|---|---|---|
| #1 | California | $148,330 |
| #3 | Oregon | $120,470 |
| #50 | Alabama | $74,970 |
| #51 | South Dakota | $72,210 |

### 3. Are hospitals hiring faster than they're paying?
**Yes — in every single top-growth state.** Louisiana hired 27% more nurses in 2024 
but only raised wages 4.1%. This pattern repeated across all 15 fastest-growing states 
— more nurses hired, wages lagging far behind.

### 4. When did wage growth peak?
Most of the biggest wage jumps happened in **2023**, not 2024 — meaning wage growth 
is already slowing down after the post-pandemic spike, even as hiring continues to grow.

---

## Dashboard
📊 [View Interactive Tableau Dashboard](https://public.tableau.com/views/BurnedOutUnderpaidTheNurseWageCrisisinAmerica/NurseWageDashboard)

---

## Conclusion
The data tells a clear story: hospitals are expanding their nursing workforce without 
proportionally increasing compensation. As hiring outpaces wage growth, nurses face 
increasing workloads without matching financial recognition — a formula for burnout 
and turnover that ultimately harms patient care.

The nurse shortage crisis is not just a supply problem. It is a compensation problem.
