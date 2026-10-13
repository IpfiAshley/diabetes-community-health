# Early findings: diabetes and community health

## Question
How does county-level diagnosed diabetes prevalence relate to inactivity, obesity, insurance coverage, and food insecurity across the United States?

## Snapshot
- **2,956 counties** have estimates for diabetes, obesity, inactivity, and lack of insurance in the selected extract.
- County diabetes prevalence ranges from **6.0% to 23.8%**; the unweighted county median is **10.7%** (mean **11.2%**).
- The strongest association among the four measures available in all counties is with **no leisure-time physical activity**: Pearson *r* = **0.873**. The county-level linear slope is about **3.78 percentage points higher diabetes prevalence per 10-point higher inactivity prevalence**; this is descriptive, not causal.
- Food insecurity has a high positive correlation with diabetes, *r* = **0.937**, among **2,299 counties** with both estimates. That subset is smaller than the main sample.
- The inactivity association remains strong after removing each state's mean levels (within-state *r* = **0.912**), so the national pattern is not explained only by differences between states. This is still an ecological comparison between modeled county estimates.

## State-level pattern
The table ranks states by the unweighted mean of their available county diabetes estimates. Each county has equal influence in this summary; it is not a population-weighted state prevalence estimate.

### Highest county means

| State | Mean county diabetes | Counties |
|---|---:|---:|
| Mississippi | 14.76% | 82 |
| Louisiana | 14.18% | 64 |
| Alabama | 13.91% | 67 |
| South Carolina | 13.46% | 46 |
| Georgia | 13.32% | 159 |
| West Virginia | 13.20% | 55 |
| Texas | 12.59% | 253 |
| Arkansas | 12.41% | 75 |

### Lowest county means

| State | Mean county diabetes | Counties |
|---|---:|---:|
| Vermont | 7.29% | 14 |
| New Hampshire | 7.77% | 10 |
| Massachusetts | 8.34% | 14 |
| Connecticut | 8.42% | 9 |
| District of Columbia | 8.50% | 1 |
| Colorado | 8.57% | 64 |
| Rhode Island | 8.60% | 5 |
| Montana | 8.98% | 56 |

## Interpretation limits
- CDC PLACES reports model-based small-area estimates. These are not direct county survey counts or individual medical records.
- The data are cross-sectional. Correlations do not show that inactivity, obesity, insurance status, or food insecurity caused diabetes.
- Measures are county aggregates; county-level relationships cannot be applied to individuals (ecological fallacy).
- Estimates are age-adjusted prevalence measures. They should not be combined with county population counts to infer case counts.
- Food insecurity estimates are available for fewer counties, so comparisons involving that measure use a separate 2,299-county subset.
- Pearson correlations describe linear association and may be affected by outliers, measurement error, shared model inputs, and spatial dependence.

## Next analysis steps
1. Add state and Census-region geography to an interactive county map.
2. Compare Pearson and rank-based (Spearman) associations and inspect outliers.
3. Use confidence limits to distinguish stable patterns from estimates with wide uncertainty.
4. Explore a multivariable model as a descriptive association analysis, with spatial and ecological limitations made explicit.
