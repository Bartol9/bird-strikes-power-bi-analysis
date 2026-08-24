# Data quality and scope

## Scope reconciliation

| Stage | Records | Explanation |
| --- | ---: | --- |
| Raw Excel source | 99,404 | All rows in the historical source snapshot |
| Dashboard model | 62,484 | Rows with a populated `When: Time of day` value |

The analysed period runs from 1 January 2000 to 31 December 2011. The raw workbook contains 37 columns covering aircraft, event timing, weather, wildlife, location, damage and cost.

## Observed quality issues

| Issue | Example | Analytical impact |
| --- | --- | --- |
| Missing categorical data | empty time of day, aircraft or location fields | Reduces the usable population for some visuals |
| Inconsistent labels | `No Cloud` versus `No Clouds` | Splits one logical category into multiple values |
| Placeholder geography | `N/A` in origin state | Can distort rankings if interpreted as a real location |
| Sparse cost reporting | many zero or empty cost records | Average cost does not describe every strike equally well |
| Extreme cost outliers | rare aircraft with very high reported cost | Can strongly affect averages and rankings |
| Reporting bias | events are reported observations | Results may not represent every wildlife strike |

## Recommended improvements

- Create explicit category-mapping tables in Power Query.
- Report missingness for every field used in a visual.
- Add median and percentile-based cost measures.
- Separate zero reported cost from missing cost.
- Add a severity classification combining damage, injuries, fatalities and cost.
- Preserve both the raw record count and the filtered analytical population in report KPIs.
