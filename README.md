
<!-- README.md is generated from README.Rmd. Please edit that file -->

# disasters-collide

<!-- badges: start -->

Cite the code and data:
[![DOI](https://zenodo.org/badge/599836056.svg)](https://zenodo.org/badge/latestdoi/599836056)

<!-- badges: end -->

# Intersection of social vulnerability, hurricanes, and COVID-19 outcomes

This repository contains data and code needed to recreate Figure 2 from
the following publication:

Drake, John; Marty, Eric; Gandhi, Kamal; Welch-Devine, Meredeith;
Bledsoe, Brian; Shepherd, Marshall; Seymour, Lynne; Fortuin, Christine;
Montes, Cristian. “Disasters collide at the intersection of extreme
weather and infectious diseases.” *Ecology Letters,* accepted for
publication 05-Feb-2023.

Preprint DOI: <https://doi.org/10.22541/au.166999211.18330817/v1>

The preprint DOI will point to the published article when published.

Data and code prepared by Eric Marty.

## Data

### COVID-19 outcomes and social vulnerability scores by Hospital Service Area (HSA)

The file `data/master_dataset_hsa_2020.Rds` contains COVID-19 outcomes
and social vulnerability scores for Health and Human Services (HHS)
regions 4 and 6, by Hospital Service Area (HSA).

Data from COVID-19 outcomes (cases and deaths) and social vulnerability
(SoVI and BRIC) were originally at the county level. We aggregated the
county-level data to the Hospital Service Area (HSA) level by
population, using data from the 2020 US census.

**File format:** The file is an R data file containing an R dataframe of
class `sf`, or “simple features.” The columns of the dataset are
described in the file `data/master_dataset_hsa_2020_metadata.csv`.

#### COVID-19 Outcomes

COVID-19 cases and deaths were derived from county-level cases and
deaths reported by Johns Hopkins University:

cases:
<https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_US.csv>

deaths:
<https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_deaths_US.csv>

COVID-19 outcomes were aggregated to HSA by population.

### SoVI

The Social Vulnerability Index (SoVI) 2010-2014, developed by the
Hazards & Vulnerability Research Institute (HVRI) at the University of
South Carolina provides measures of social vulnerability to
environmental hazards for US counties.

General information on the SoVI is available at
<https://sc.edu/study/colleges_schools/artsandsciences/centers_and_institutes/hvri/data_and_resources/>

The SoVI data inputs consist of 29 census variables from the 2010 US
Census, normalized as percentages, per capita values, or density
functions.

Input variables were standardized using z‐scores, giving variables with
mean 0 and standard deviation 1. The overall SoVI score is an additive
model using PCA to determine weights of components in each of 8 factors,
which are summed to obtain the overall score.

We aggregate from county-level to HSA-level scores using the
population-weighted mean of county-level SoVI scores (mean 0, standard
deviation 1), using 2010 Census numbers.

Original SoVI 2010-2014 scores by county are available here:

<https://www.sc.edu/study/colleges_schools/artsandsciences/centers_and_institutes/hvri/documents/sovi/sovi_10_14_data.pdf>

#### BRIC

The Baseline Resilience Indicators for Communities (BRIC), developed by
the Hazards & Vulnerability Research Institute (HVRI) at the University
of South Carolina provides measures of resilience for US counties.

BRIC input variables are grouped into “capitals,” normalized 0-1 and
averaged to obtain a BRIC capital score for each capital. (1 indicates
high resilience.)

The overall resilience score is a sum of 6 capital scores, with
theoretical maximum of 6.

We aggregate from county-level to HSA/HRR-level scores by taking the
population-weighted mean of BRIC capital scores for each HSA, then
summing HSA-level BRIC capital scores to obtain the BRIC overall score
for each HSA.

Origical county-level data are available here:

<https://sc.edu/study/colleges_schools/artsandsciences/centers_and_institutes/hvri/data_and_resources/bric/bric_data/index.php>

References for SoVI and BRIC:

Cutter, S.L., Ash, K.D. & Emrich, C.T. (2014). “The geographies of
community disaster resilience.” *Glob. Environ. Change*, 29, 65–77.

Cutter, S.L., Boruff, B.J. & Shirley, W.L. (2003). “Social vulnerability
to environmental hazards.” *Soc. Sci. Q., 84, 242–261.*

### Hurricane tracks, 2010-2021

The file `data/hurr_tracks.sf.Rds` contains Atlantic hurricane tracks
for the 2010 through 2021 seasons.

Data from COVID-19 outcomes (cases and deaths) and social vulnerability
(SoVI and BRIC) were originally at the county level. We aggregated the
county-level data to the Hospital Service Area (HSA) level by
population, using data from the 2020 US census.

**File format:** The file is an R data file containing an R dataframe of
class `sf`, or “simple features.” The columns of the dataset are
described in the file `data/hurr_tracks_metadata.csv`.

The original hurricane track data were downloaded from the US National
Oceanic and Atmospheric Administration’s “Atlantic hurricane database”
(HURDAT2) 1851-2021, here:

<https://www.nhc.noaa.gov/data/hurdat/hurdat2-1851-2021-100522.txt>

See <https://www.nhc.noaa.gov/data/hurdat/> for the latest data.

## Code

The file `Map.Rmd` contains the R code needed to reproduce figure 2. The
file is in R Markdown format.

A PDF containing the same code and code outputs, including the figure,
is also available: `Map.pdf`

The file `R/visualization` contains functions needed to create the map.

## Outputs

The code produces the figure in jpeg and pdf formats:
`covid_sovi_hurr.jpg` and `covid_sovi_hurr.pdf`.
