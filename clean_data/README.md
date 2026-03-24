
# Clean Data

CSV files processed and structured for Power BI.
Each file corresponds to one table in the data model.

## Files

| File | Contents | Source |
|------|----------|--------|
| H1_building_approvals_monthly.csv | Monthly approvals by state 2019-2026 | ABS 8731.0 |
| H2_housing_accord_scorecard.csv | State targets, projections and gaps | ABS + NHSAC |
| H3_population_by_state.csv | Quarterly population by state | ABS 3101.0 |
| H4_supply_demand_gap.csv | Annual supply vs demand by state | ABS 3101.0 + 8731.0 |
| H5_rent_inflation.csv | Monthly rent YoY% with era labels | ABS 6401.0 |
| H6_rba_cash_rate.csv | Monthly RBA cash rate with era labels | RBA Table A2 |
| Migration_Data.csv | Annual net overseas migration | ABS 3101.0 |
| Era_Rent_Data.csv | Average rent inflation by economic era | Calculated |

## Data cleaning steps applied

- Renamed columns to snake_case
- Converted date formats to YYYY-MM-DD
- Removed null and blank rows
- Filtered to relevant date ranges
- Added calculated columns (era labels, year, month)
- Standardised state codes (NSW, VIC, QLD etc)

## Data model

These 8 tables form a star schema in Power BI:
- H2 is the central fact table
- H1, H3, H4 connect to H2 via state column
- H6 connects to H5 via date column
- Migration_Data and Era_Rent_Data are standalone
