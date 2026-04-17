# nurse-wage-crisis-analysis
Analyzing the nurse wage crisis in America using BLS government data | SQL · BigQuery · Tableau
# 🏥 Burned Out & Underpaid: The Nurse Wage Crisis in America

## Overview
This project analyzes 3 years of real Bureau of Labor Statistics (BLS) data to investigate 
whether nurse wages are keeping up with the demands placed on them — and whether the states 
nurses are moving TO for higher pay are actually better after accounting for cost of living 
and state income tax.

> **Central Question:** Are hospitals hiring more nurses without paying them more — and are 
> high-wage states actually better for nurses after adjusting for real cost of living?

**Tools:** SQL · Google BigQuery · Tableau Public · Python · GitHub

---

## Dataset Sources
| Dataset | Source | Records |
|---|---|---|
| Nurse Wage Data | BLS Occupational Employment & Wage Statistics (OEWS) | 597 rows, 3 years |
| Cost of Living Index | MERIC (Missouri Economic Research & Information Center) 2024 | 51 states + DC |
| State Income Tax Rates | Tax Foundation 2024 | 51 states + DC |

---

## Advanced SQL Techniques Used
- **CTEs (Common Table Expressions)** — multi-step wage growth calculations
- **Window Functions: RANK()** — ranking all 50 states by RN wage
- **Window Functions: LAG()** — year-over-year wage change by state
- **CASE WHEN** — classifying hiring vs wage growth trends
- **Double JOIN** — combining nurse wages + cost of living
- **Triple JOIN** — combining nurse wages + cost of living + state income tax
- **Derived calculations** — after-tax wage and true purchasing power formulas

---

## Key Questions & Findings

### 1. Are nurse wages actually growing? (CTE + JOIN)
Yes — but unevenly. LPN/LVNs got the biggest % raise (14.6%) but still earn just 
$63,900 — the lowest of all nurse roles. Nurse Practitioners got the smallest raise 
(7.6%) despite requiring the highest level of education.

| Nurse Role | 2022 Avg Wage | 2024 Avg Wage | % Increase |
|---|---|---|---|
| LPN/LVN | $55,740 | $63,900 | +14.6% |
| Registered Nurses | $83,852 | $93,431 | +11.4% |
| Nurse Anesthetists | $207,246 | $227,450 | +9.7% |
| Nurse Practitioners | $120,835 | $130,028 | +7.6% |

### 2. Does your state determine your salary? (Window Function: RANK)
Dramatically yes — nearly a $50,000 gap between the highest and lowest paying states 
on raw wages alone.

| Rank | State | Annual Mean Wage |
|---|---|---|
| #1 | California | $148,330 |
| #3 | Oregon | $120,470 |
| #50 | Alabama | $74,970 |
| #51 | South Dakota | $72,210 |

### 3. Are hospitals hiring faster than they're paying? (Window Function: LAG + CASE WHEN)
Yes — in every single top-growth state. Louisiana hired 27% more nurses in 2024 
but only raised wages 4.1%. This pattern repeated across all 15 fastest-growing 
states — a formula for burnout and turnover.

### 4. After cost of living adjustment, which states are actually best? (Double JOIN)
The rankings shift dramatically. New Mexico jumps from #19 to #3. Mississippi 
gains 28 spots. California stays #1 but the gap narrows significantly.

### 5. After tax AND cost of living — what is a nurse's TRUE purchasing power? (Triple JOIN)
This is the most important finding. Once state income tax is factored in alongside 
cost of living, the rankings flip entirely:

| True Rank | State | Raw Wage | True Purchasing Power | Raw Rank |
|---|---|---|---|---|
| #1 | Washington | $115,740 | $99,262 | #4 |
| #2 | Nevada | $102,280 | $99,013 | #11 |
| #3 | Texas | $91,690 | $98,064 | #22 |
| #4 | California | $148,330 | $97,137 | #1 |
| #49 | Vermont | $92,710 | $71,150 | #20 |
| #50 | DC | $109,240 | $64,821 | #8 |
| #51 | Hawaii | $123,720 | $63,203 | #2 |

**A nurse in Hawaii earning $123,720 has less true purchasing power ($63,203) 
than a nurse in Indiana earning $85,850 ($91,063).** The states nurses are 
moving TO are not always actually better.

---

## Why This Analysis Is More Honest Than Most
Most nurse wage comparisons use raw salary data only. This project goes further by:
1. Adjusting for **cost of living** using the MERIC index (where 100 = national average)
2. Adjusting for **state income tax** — 9 states have zero income tax, creating a 
   significant real-wage advantage
3. Calculating **true purchasing power** — what a nurse can actually afford to buy 
   with their paycheck in that state

---

## Dashboard
📊 [View Interactive Tableau Dashboard](https://public.tableau.com/views/BurnedOutUnderpaidTheNurseWageCrisisinAmerica/NurseWageDashboard)

---

## Conclusion
The nurse wage crisis is more complex than headline salaries suggest. Hospitals are 
expanding their nursing workforce without proportionally increasing compensation — 
a pattern visible in every high-growth state. And when nurses chase higher wages 
to expensive coastal states, they may be trading a modest salary for a lower 
standard of living.

The data points to a clear recommendation: **policymakers and hospital administrators 
should evaluate nurse compensation using purchasing power metrics, not raw wages.** 
A nurse in Texas earning $91,690 with zero state income tax in a below-average cost 
of living state may be better compensated in real terms than a nurse in Massachusetts 
earning $112,610 with a 5% income tax and 149.9 cost of living index.
