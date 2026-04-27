# Mental Health Trends in England: An Epidemiological Analysis

**Author:** Usman Adamu  
**Date:** April 2026  
**Tools:** R, R Markdown, fingertipsR, tidyverse, ggplot2, tmap, sf  
**Data source:** OHID Fingertips platform (NHS Digital)

---

## Overview

This project presents a reproducible epidemiological analysis of mental health trends in England using real NHS data from the Office for Health Inequalities and Disparities (OHID) Fingertips platform. The analysis is structured around five core research questions covering national trends, geographic variation, social determinants, and hospital admission patterns among under-18s.

All data were accessed programmatically via the `fingertipsR` package. The full analysis is written in R Markdown and is completely reproducible from source.

---

## Research Questions

1. How has depression prevalence changed in England between 2012 and 2024?
2. Which local authorities have the highest and lowest depression prevalence?
3. What is the geographic distribution of depression across English local authorities?
4. Is there an association between neighbourhood deprivation and depression prevalence?
5. How have mental health hospital admissions among under-18s changed over time, and do patterns differ by gender?

---

## Data

All indicators were extracted at **Counties and Unitary Authorities level (AreaTypeID 502)** from the OHID Fingertips platform using `fingertipsR` v1.1.0.

| Indicator | Fingertips ID |
|---|---|
| Depression QOF prevalence | 848 |
| Depression new diagnosis | 90646 |
| % reporting depression or anxiety | 93376 |
| Mental health hospital admissions (under-18s) | 90812 |
| IMD 2019 deprivation score | 93553 |

Data accessed: April 2026.

---

## Key Findings

**1. Sustained rise in depression prevalence**  
Depression QOF prevalence increased by **146%** between 2012/13 and 2024/25, rising from 5.8% to 14.3%. Linear regression confirmed this trend was highly significant (β = 0.77 percentage points per year, p < 0.001, R² = 0.995).

**2. Clear deprivation gradient**  
A statistically significant positive association was found between IMD deprivation score and depression prevalence across local authorities (β = 0.13, p < 0.001). Local authorities in the most deprived quintile recorded mean depression prevalence of ~16.8%, compared to ~13.0% in the least deprived — a gap of nearly four percentage points.

**3. Pronounced North-South geographic inequality**  
Choropleth mapping revealed a clear North-South gradient, with the North West and North East of England showing the highest depression prevalence. London and the South East showed the lowest — consistent with established evidence on regional health inequalities in England.

**4. Rising mental health admissions among under-18s**  
Hospital admissions for mental health concerns among under-18s increased substantially from 2010/11, with self-harm accounting for over half of all admissions by 2021/22.

**5. Persistent and widening gender disparity**  
Female under-18s had consistently higher admission rates than males. During 2020/21, the gap widened sharply — female admissions increased while male admissions declined — reflecting both the disproportionate mental health impact of COVID-19 lockdowns on young women and structural barriers to help-seeking among young men.

---

## Methodology

- **Trend analysis:** National England-level depression prevalence plotted with 95% confidence intervals; linear regression of prevalence against time index
- **Geographic analysis:** Choropleth mapping of local authority depression prevalence using `tmap` and `rnaturalearth` boundary data
- **Deprivation analysis:** Scatter plot with linear regression fit; deprivation quintile bar chart with standard error bars
- **Admissions analysis:** Time-series plots of overall admissions and sex-stratified trends
- **All citations:** Vancouver style, drawing on peer-reviewed UK public health literature

---

## Limitations

- QOF depression prevalence reflects **recorded diagnosis**, not true population prevalence. Areas with better GP access may record higher rates independently of underlying burden (ascertainment bias).
- Depression prevalence data are available for **"Persons" only** — sex-stratified prevalence analysis is not possible with this indicator.
- Hospital admissions data are **specific to under-18s** and do not capture adult trends.
- This is an **ecological analysis**. Area-level associations cannot be used to infer individual-level causal relationships.

---

## Repository Structure

```
mental-health-trends-england/
├── mental_health_trends.Rmd     # Full R Markdown source (reproducible)
├── mental_health_trends.html    # Rendered HTML report
└── README.md
```

---

## How to Reproduce

1. Clone this repository
2. Open `mental_health_trends.Rmd` in RStudio
3. Install required packages if not already installed:

```r
install.packages(c("fingertipsR", "tidyverse", "tmap", "sf",
                   "rnaturalearth", "rnaturalearthdata"))
```

4. Click **Knit** — data are fetched live from the OHID Fingertips API

> **Note:** Live API calls mean rendering requires an internet connection. Data values may differ slightly if accessed after April 2026 as Fingertips is updated regularly.

---

## References

Key references cited in the analysis include:

- Daras K et al. SSM Popul Health. 2024;26:101669. *(12-year longitudinal spatial analysis of depression in England)*
- Ward JL et al. Lancet Child Adolesc Health. 2025;9(2):112–20. *(national cohort study of mental health admissions among children and young people)*
- Solmi M et al. Lancet Child Adolesc Health. 2023;7(8):554–63. *(eating disorder and self-harm trends post-COVID)*
- Sheikh A et al. Eur Child Adolesc Psychiatry. 2025;34:565–83. *(barriers to help-seeking in young men)*

Full reference list available in the rendered report.

---

*This project is part of a public health data analytics portfolio developed using real NHS data. All analysis is conducted for educational and professional development purposes.*
