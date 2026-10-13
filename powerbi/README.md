# Power BI dashboard starter

This folder contains the build guide and DAX measures for an interactive Power BI report based on the county analysis. The source is `data/county_health_wide.csv` in the project root.

## Build the report

1. Open Power BI Desktop and choose **Get data → Text/CSV**.
2. Select `data/county_health_wide.csv` from the project folder, then choose **Transform data**.
3. Confirm `diabetes_pct`, `inactive_pct`, `obesity_pct`, `uninsured_pct`, and `food_insecurity_pct` are decimal number columns. Keep `county_fips` as text so leading zeroes remain intact. Rename the query to `CountyHealth`, then choose **Close & Apply**.
4. In Model view, add a calculated column named `County Label`:

   ```DAX
   County Label = CountyHealth[county] & ", " & CountyHealth[state_abbr]
   ```

5. Add the measures from [measures.dax](measures.dax). Format each prevalence measure with the custom display format `0.0"%"`: the CSV stores percentage points (for example, `11.4` means 11.4%), not decimal fractions.
6. Build the report using the page plan below. Save the result as a `.pbix` file in this folder.

## Page plan: County overview

- **Slicers:** `state`, `County Label`
- **Cards:** Average diabetes prevalence, Median diabetes prevalence, Counties in selection, Counties with food insecurity estimate
- **Scatter chart:** X = `inactive_pct`, Y = `diabetes_pct`, Details = `County Label`, Tooltips = `state`, `obesity_pct`, `uninsured_pct`
- **Bar chart:** Axis = `state`, Values = Average diabetes prevalence; sort descending and show the top 10 states
- **Table:** `County Label`, `diabetes_pct`, `inactive_pct`, `obesity_pct`, `uninsured_pct`, `food_insecurity_pct`; sort by diabetes prevalence descending
- **Optional scatter chart:** X = `food_insecurity_pct`, Y = `diabetes_pct`, Details = `County Label`. Counties without food insecurity estimates are excluded automatically.

Use the title **Diabetes and Community Health by County**. Add a visible note that these are age-adjusted, model-based county estimates and that county-level associations are descriptive, cross-sectional, and not evidence of causation or individual risk.

## Interpretation notes

- The main four-measure comparison includes 2,956 counties. Food insecurity is available in 2,299 counties; its chart and card use only rows with an estimate.
- County values are not population-weighted state estimates. The state bar chart averages county estimates equally.
- Avoid using these percentages with county population counts to estimate case counts; they are age-adjusted prevalence estimates.

Power BI Desktop is required to assemble, save, and publish the interactive report. This starter folder does not contain a `.pbix` file yet.
