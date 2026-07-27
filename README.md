# Diabetes and Mortality in Denmark: A GLM Approach

Modelling the effect of diabetes on population-level mortality in Denmark
(1996–2015) using Poisson and negative binomial regression, with a focus
on rigorous model diagnostics and interpretation.

## Summary

Using two decades of aggregated Danish population mortality data, this
project models death rates as a function of age, sex, calendar period,
and diabetes status. Starting from a Poisson regression baseline,
diagnostic checks reveal overdispersion and a misspecified mean
structure. Both are resolved by moving to a negative binomial model with
a `diabetes × age group` interaction, capturing the finding that
diabetes' relative impact on mortality is largest in younger age groups
and diminishes with age.

**Key finding:** diabetes is estimated to be responsible for
approximately **74,000 deaths** in Denmark over the study period, around
**6.4% of all deaths**.

## Project structure
glm-danish-mortality-analysis/
├── notebooks/
│ └── glm_danish_mortality.ipynb ← full analysis
├── data/
│ └── dmdk.csv ← Danish mortality data (1996–2015)
├── outputs/
│ └── glm_danish_mortality.pdf ← rendered report
├── requirements.txt
└── README.md
## Methodology

1. **Exploratory analysis** - empirical death rates by age, sex, period,
   and diabetes status.
2. **Poisson regression** - baseline model with `agegrp`, `period`,
   `sex`; likelihood ratio test comparing linear `age` vs. factor
   `agegrp`.
3. **Diagnostics** - Cook's distance, residuals-vs-fitted (structural
   fit), scale-location plots (random/variance fit).
4. **Negative binomial regression** - addressing overdispersion
   identified in Poisson diagnostics.
5. **Interaction model** - adding `diabetes × agegrp` to resolve
   remaining structural misspecification, motivated by the empirical
   finding that the diabetes mortality gap narrows with age.
6. **Attributable risk** - counterfactual population without diabetes,
   used to estimate deaths and the fraction of all deaths attributable
   to diabetes.

## Tools

Python, pandas, statsmodels, matplotlib, scipy.

## Running this project

```bash
pip install -r requirements.txt
jupyter notebook notebooks/glm_danish_mortality.ipynb
```

## Data

The dataset (`dmdk.csv`) contains counts of deaths and person-years at
risk in Denmark from 1996-2015, stratified by 5-year age group,
calendar period, sex, and diabetes status.
