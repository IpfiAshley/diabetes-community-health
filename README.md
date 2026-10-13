# Diabetes and Community Health

A portfolio-ready exploratory data analysis of county-level diagnosed diabetes prevalence and related community health measures.

## Research question

How does diagnosed diabetes prevalence vary across U.S. counties, and how is it associated with inactivity, obesity, lack of health insurance, and food insecurity?

## Data

This project uses selected measures from the CDC **PLACES: Local Data for Better Health, County Data, 2025 release**. The dataset provides modeled small-area estimates using BRFSS and supporting population data. CDC describes PLACES as model-based estimates for counties and other geographies; values are not raw county survey counts or person-level records.

- [CDC PLACES county data, 2025 release](https://data.cdc.gov/500-Cities-Places/PLACES-Local-Data-for-Better-Health-County-Data-20/swc5-untb)
- [About PLACES and data sources](https://www.cdc.gov/places/about/)
- [CDC PLACES methodology](https://www.cdc.gov/places/methodology/index.html)
- API dataset identifier: `swc5-untb`
- Data retrieved: 12 October 2026
- All selected estimates use age-adjusted prevalence. The downloaded extract retains confidence limits and population fields from CDC.

Included measures:

| Measure | CDC id | Counties available |
|---|---|---:|
| Diagnosed diabetes among adults | `DIABETES` | 2,956 counties after excluding the U.S. total |
| Obesity among adults | `OBESITY` | 2,956 |
| No leisure-time physical activity among adults | `LPA` | 2,956 |
| Lack of health insurance, ages 18–64 | `ACCESS2` | 2,956 |
| Food insecurity in the past 12 months | `FOODINSECU` | 2,299 |

The CDC file has additional records outside the county geography (including a U.S. aggregate) and some rows with no estimate. The county analysis excludes the aggregate and keeps available estimates. Leading zeros are restored in county FIPS identifiers when reshaping the data.

## Key early findings

- In the 2,956-county complete sample, diabetes prevalence ranges from 6.0% to 23.8%; the unweighted county median is 10.7%.
- The pooled county-level Pearson correlation is 0.873 between diabetes and inactivity, 0.683 with obesity, and 0.631 with lack of insurance.
- The inactivity association remains strong after subtracting state means (within-state correlation 0.912).
- Food insecurity and diabetes have a Pearson correlation of 0.937 in the 2,299 counties where both estimates are available.

These are ecological, cross-sectional associations among model-based estimates. They do not establish causation or describe individual risk. State averages are unweighted averages of county estimates, not population-weighted state prevalence.

## Project files

- `index.html` — visual summary dashboard; open in a browser.
- `analysis.ipynb` — reproducible notebook for cleaning, coverage checks, and correlations.
- `findings.md` — written findings, state comparison, and interpretation limits.
- `data/cdc_places_county_selected_2025.csv` — selected CDC source rows, including confidence limits.
- `data/county_health_wide.csv` — analysis-ready county table.
- `charts/` — standalone SVG charts used by the dashboard.

## Reproduce the analysis

Use Python 3 with `pandas` and `numpy`, plus Jupyter to open the notebook. From this project folder, run the notebook cells in order. The provided source extract means a live CDC connection is not required to reproduce the current analysis.

## Interpretation and next steps

The measures are county aggregates, so relationships at this level cannot be assumed to hold for individuals (ecological fallacy). The estimates are cross-sectional and model-based; the correlations can reflect shared social, economic, geographic, or modeling factors. Confidence limits should be incorporated before identifying statistically meaningful differences. A next iteration could compare rank correlations, add mapped geography, and study uncertainty explicitly.
