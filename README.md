# HydroState

**Understanding how Victorian catchments are responding to a drier climate.**

🌐 **Live site: [hydrostate.github.io](https://hydrostate.github.io)**

HydroState is a free dashboard and statistics tool for identifying where catchment runoff behaviour has shifted, how persistent that shift is, and what it means for water resource planning. It brings the research of Peterson et al. (2021) and Zahedi et al. (2026) together with the open-source [hydroState](https://github.com/peterson-tim-j/HydroState) R package. Anyone can use it in a web browser, with no software to install and no R code to learn.

---

## Why it matters

Many Victorian catchments still produce less runoff than they did before the Millennium Drought (1997–2009), even though rainfall has returned. Peer-reviewed research on Victoria's gauged, unregulated catchments found that:

- **57%** of catchments shifted to a low-runoff state, many of them very early in the drought;
- **37%** had not returned to their pre-drought rainfall–runoff behaviour seven years after the drought ended; and
- **80%** of those showed no sign of imminent recovery.

Planning that assumes rainfall will deliver pre-drought runoff may therefore overestimate the water available. HydroState helps planners see where that assumption may no longer hold.

## What the site offers

| Section | What it provides |
|---|---|
| **Overview** | A summary of hydrological state shifts across Victoria, with example catchments that stayed unchanged, recovered, or did not recover. |
| **Background & Theory** | Catchment states, hydrological resilience and tipping points, recovery and non-recovery, and how a Hidden Markov Model detects a shift. |
| **Catchment Map** | The current runoff state of 161 Victorian streamflow gauges: a quick screen of where pre-drought assumptions may no longer hold. |
| **Method & Calculations** | The model structure, the mathematics behind it, and how to interpret the results. |
| **Analyse your Data** | Run the hydroState model on your own annual streamflow and rainfall record and get the state history, the evidence for a shift, and the size of that shift. |
| **About** | The team, references, data sources and acknowledgements. |

## Analysing your own catchment

The **Analyse your Data** tab embeds an interactive R Shiny app ([open it on its own](https://weatherburn10.shinyapps.io/R-HydroState_App_v1/)). Upload or paste an annual record with three columns:

| Column | Description |
|---|---|
| `year` | Water year, one row per year |
| `flow` | Annual streamflow, in mm/year or GL/year. Gaps are allowed: leave the cell blank. |
| `precipitation` | Annual rainfall, in the same units as flow. Gaps are **not** allowed. |

The record must be between 20 and 200 years long, and should ideally include years before, during and after the Millennium Drought. The app then:

1. fits a two-state model (or three states, under Advanced settings), alongside a one-state, no-shift model for comparison;
2. reports the **evidence ratio**: how many times better the data support the state-shift model than the no-shift model;
3. shows the most likely state in each year, with the reference year of your choice (1990 by default) defining the **Baseline** state; and
4. estimates the **size of the shift**: the flow in the identified state compared with the flow expected had the catchment stayed in its Baseline state.

Victorian streamflow records can be downloaded from the DEECA Water Measurement Information System (WMIS) at [data.water.vic.gov.au](https://data.water.vic.gov.au).

> [!NOTE]
> The app is hosted on the shinyapps.io free plan, which allows a limited number of active hours each month. If it shows as unavailable, please try again later.

## Data sources

- **Streamflow:** 161 Victorian streamflow gauges, DEECA Water Measurement Information System (WMIS), [data.water.vic.gov.au](https://data.water.vic.gov.au). These were selected from 602 candidate gauges using criteria covering data availability, upstream regulation and licensed extraction, record length around the Millennium Drought, and local review by catchment management authorities.
- **Rainfall:** Australian Bureau of Meteorology gridded AWAP datasets.
- **Basin boundaries:** AWRC Major River Basins of Victoria (BASIN100), Department of Energy, Environment and Climate Action, via DataVic, CC BY 4.0.
- **Catchment Map states:** annual hydroState model outputs for each gauge, supplied by A/Prof Tim Peterson.
- **Land cover:** [Victorian land cover time series 1985–2019](https://discover.data.vic.gov.au/dataset/victorian-land-cover-time-series).

## Key references

- Peterson, T.J., Saft, M., Peel, M.C. & John, A. (2021). Watersheds may not recover from drought. *Science*, 372(6543), 745–749. [doi:10.1126/science.abd5085](https://doi.org/10.1126/science.abd5085)
- Peterson, T.J. & Westfall, T. hydroState: Hidden Markov Modelling of Hydrological State Change. *R package*. [github.com/peterson-tim-j/HydroState](https://github.com/peterson-tim-j/HydroState)
- Zahedi, S. et al. (2026). [FULL REFERENCE: title, journal, DOI]
- Zahedi, S. (2025). Rainfall–runoff regime shifts and thresholds induced by multi-year droughts across Victoria. *PhD thesis*, Monash University. [Monash Bridges](https://bridges.monash.edu/articles/thesis/Rainfall-Runoff_regime_shifts_and_thresholds_induced_by_multi-year_droughts_across_Victoria/30334264/1)
- Saft, M., Western, A.W., Zhang, L., Peel, M.C. & Potter, N.J. (2015). The influence of multiyear drought on the annual rainfall–runoff relationship: An Australian perspective. *Water Resources Research*, 51, 2444–2463. [doi:10.1002/2014WR015348](https://doi.org/10.1002/2014WR015348)
- Fowler, K. et al. (2020). Many commonly used rainfall–runoff models lack long, slow dynamics: Implications for runoff projections. *Water Resources Research*, 56, e2019WR025286. [doi:10.1029/2019WR025286](https://doi.org/10.1029/2019WR025286)
- Pamminger, L.W., Peterson, T.J. & Peel, M.C. (2025). Climate change may alter rainfall-partitioning in ways unlikely to be detected in the coming decades. *Water Resources Research*, 61, e2024WR039102. [doi:10.1029/2024WR039102](https://doi.org/10.1029/2024WR039102)
- Peterson, T.J., Western, A.W. & Argent, R.M. (2014). Multiple hydrological attractors under stochastic daily forcing: 2. Can multiple attractors emerge? *Water Resources Research*, 50. [doi:10.1002/2012WR013004](https://doi.org/10.1002/2012WR013004)

The full reference list is on the site's [About](https://hydrostate.github.io) page.

## The team

HydroState was developed as a final-year Environmental Engineering (Honours) project at Monash University.

- **Chelsea Morgan**, Environmental Engineering (Honours), Monash University
- **Caitlin Weatherburn**, Environmental Engineering (Honours), Monash University
- **A/Prof Tim Peterson** (supervisor), Department of Civil & Environmental Engineering, Monash University. Lead author of Peterson et al. (2021) and developer of the hydroState R package.

The platform was co-designed with Victorian water industry professionals through interviews and feedback sessions.

## How to cite

> Morgan, C., Weatherburn, C. & Peterson, T.J. (2026). *HydroState*. Monash University. https://hydrostate.github.io

## Acknowledgements

Development of the hydroState package was funded by the Victorian Government Department of Energy, Environment and Climate Action (DEECA). The research underpinning the platform (Peterson et al., 2021) was funded mainly by the Victorian Government under the Victorian Water and Climate Initiative (VicWaCI), with supplemental support from the Australian Research Council.

We thank the water industry professionals who gave their time and feedback during project interviews, the Victorian catchment management authorities whose local review shaped the gauge set, and Monash University for supporting the project.

## Contact

For questions, feedback or collaboration enquiries, please email
**hydro.research.mu@gmail.com**.

- **Found a problem or have a suggestion?** [Open an issue](https://github.com/hydrostate/hydrostate.github.io/issues).
- **Questions about the hydroState method or R package:** A/Prof Tim Peterson,
  Department of Civil & Environmental Engineering, Monash University
  ([staff profile](https://www.monash.edu/engineering/timpeterson)).
- **Project team:** [Chelsea Morgan](www.linkedin.com/in/chelsea-morgan-105b97237) · [Caitlin Weatherburn](https://www.linkedin.com/in/caitlin-weatherburn-36b943210/)

---

## Repository contents

| File | Purpose |
|---|---|
| `index.html` | The website: all pages, styling and figures in a single file |
| `basins_vic.js` | Victorian river basin boundaries for the Catchment Map |
| `gauges_vic.js` | Gauge locations and yearly runoff states for the Catchment Map |

The site is published with GitHub Pages directly from the `main` branch. To update it, replace `index.html` (or the data files) and commit; the live site refreshes within a few minutes.

---

> [!IMPORTANT]
> **Disclaimer.** HydroState is a research tool developed at Monash University. It is not an official Victorian Government product. Results should be considered alongside local knowledge and other evidence before informing planning decisions.
