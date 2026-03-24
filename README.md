# Australia's Housing Supply Crisis — Will We Hit 1.2 Million by 2029?

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow)
![Data](https://img.shields.io/badge/Data-ABS%20%7C%20RBA-blue)
![Status](https://img.shields.io/badge/Status-Complete-green)

## 🔗 Live Dashboard
[Click here to view the interactive dashboard](https://shorturl.at/sVYgh)

---

## Overview
A 5-page Power BI dashboard analysing Australia's housing supply crisis 
using real government data from the Australian Bureau of Statistics (ABS) 
and Reserve Bank of Australia (RBA).

**Core question:** At current approval rates, will Australia deliver the 
1.2 million homes promised under the National Housing Accord by 2029?

**Answer: No. Australia will fall short by 342,210 homes.**

---

## Key Findings

- 🔴 Australia will miss its 2029 Housing Accord target by **342,210 homes**
- 🔴 NSW needs **42% more approvals** annually just to meet its commitment
- 🔴 WA is building at only **46% of required pace** despite fastest population growth
- ✅ Victoria leads all states on the federal Housing Accord target
- 📈 Rate hikes had **zero effect on rents** — only slower migration helped
- 🏘️ Rent inflation peaked at **8.1%** in 2023 — highest in 40 years

---

## Dashboard Pages

| Page | Title | Story |
|------|-------|-------|
| 1 | National Overview | The big picture — 342K shortfall, state gaps |
| 2 | State Scorecard | State by state progress vs Housing Accord targets |
| 3 | Supply vs Demand | Population growth vs homes approved 2019-2025 |
| 4 | Rent Crisis | Rent inflation journey — from normal to crisis to easing |
| 5 | Recommendations | Strategic actions by state with supporting data |

---

## Data Model

Star schema with 7 tables and 4 relationships:
```
H2_housing_accord_scorecard (central fact table)
├── H1_building_approvals_monthly (via state)
├── H3_population_by_state (via state)
├── H4_supply_demand_gap (via state)
H5_rent_inflation ── H6_rba_cash_rate (via date)
Migration_Data (standalone)
Era_Rent_Data (standalone)
```

---

## DAX Measures

12 measures created including:
- `National Shortfall = -342210`
- `Total Approvals 2025 = CALCULATE(SUM approvals, year = 2025)`
- `Target Progress % = DIVIDE(projected_5yr, accord_target) * 100`
- `Latest Rent YoY = LASTNONBLANK(yoy_change_pct)`
- `Required Pace = SWITCH(state, "NSW", 62800, "VIC", 48000 ...)`

---

## Data Sources

All data publicly available from official Australian government sources:

| Dataset | Description | Coverage | Source |
|---------|-------------|----------|--------|
| ABS 8731.0 | Monthly dwelling approvals by state | Jan 2019 - Jan 2026 | abs.gov.au |
| ABS 3101.0 | National and state population quarterly | 2019 - Sep 2025 | abs.gov.au |
| ABS 6401.0 | CPI Table 7 — Rents seasonally adjusted | 2017 - Jan 2026 | abs.gov.au |
| RBA Table A2 | Cash rate target — all decisions | To Mar 2026 | rba.gov.au |
| NHSAC Targets | Housing Accord state-level targets | 2024-2029 | treasury.gov.au |

---

## Tools Used

- **Power BI Desktop** — dashboard design and DAX
- **Power Query** — data cleaning and transformation
- **Star schema** data modelling
- **Conditional formatting** — red/green status indicators

---

## Repository Structure
```
australia-housing-supply-crisis/
├── README.md
├── Australia_Housing_Crisis.pbix
├── Australia_Housing_Supply_Crisis.pdf
├── raw_data/
│   ├── README.md
│   └── [Original ABS and RBA files]
└── clean_data/
    ├── README.md
    └── [H1-H8 processed CSV files]
```

---

## Key Limitation

This analysis uses **approvals** as a proxy for supply.
15-25% of approved dwellings are never built — meaning
the real shortfall likely exceeds 342,210 homes.

---

## Author

**Nikhil Chhetri** | Aspiring Data Analyst | Melbourne, Australia

[LinkedIn](https://www.linkedin.com/in/nikhilchhetrianalytics/) · [Live Dashboard](https://shorturl.at/sVYgh)

---

*Data current as of March 2026. All sources publicly available.*
