# MT5763 Group Project - Data Analysis (Python)

<a href="https://www.thecommononline.org/return-of-the-puffin/">
  <img src="Assets/Puffin_Photo.jpg" alt="Puffin bird photo. Photo by Tianne Stormbeck" width="400">
</a>

## Bird Biodiversity Analysis Toolkit

A complete, end-to-end workflow for collecting, visualising and
analysing UK bird observation data.

This project integrates a real-time Shiny application with Python-based
statistical analysis, including jackknife estimation, bootstrap
regression and simulation-based hypothesis testing.

This repository accompanies the Shiny application (repo can be found
[here](https://github.com/mt5763standrews/shiny-app-puffin)) and
reproducible code for the MT5763 Software for Data Analysis module.

## Highlights

Here’s what our project offers:

-   Real-time data collection from GBIF’s Occurrence API
-   Interactive Shiny app with maps, filters and data downloads
-   [Link to the GitHub repo](https://github.com/mt5763standrews/shiny-app-puffin)
-   [Link to the Published Shiny App](https://atucker.shinyapps.io/just_final_shiny_app/)
-   Jackknife analysis with perfect match to analytical SE
-   Bootstrap regression with robust uncertainty estimates
-   Randomisation tests (slow + fast versions with 3x speedup)
-   Reproducible Python/Quarto pipeline
-   Real biological insight into Bluetits and Robins in the UK
-   Clean repository organisation with all data and results included

## Overview

This project was developed as part of the MT5763 Software for Data
Analysis module at the University of St Andrews.

We built a full analysis pipeline using both R (for the Shiny App) and
Python (for data analysis).

All results shown in the report come from our reproducible .qmd file.

What the project does:
* Fetches bird occurrence data via [GBIF API](https://techdocs.gbif.org/en/openapi/)
* Displays observations on a live, interactive map
* Exports data for analysis
* Applies jackknife, bootstrap, and randomisation-based methods
* Tests for species differences in geographic location
* Produces polished figures and clear interpretations

Why this matters:
* Biodiversity monitoring relies on high-quality tools
* The pipeline demonstrates correct application of resampling methods
* The analysis helps understand whether species prefer different regions

## Authors

This project was created by MT5763 Group Puffins

All group members contributed to Tasks 1–4 as required by the module
specification.

## Usage instructions

Here is how to run each component of the toolkit.

### Run the Shiny App

Can be found in the following
[repository](https://github.com/mt5763standrews/shiny-app-puffin) and
run it with

```{r}
shiny::runApp("app/")
```

or you can access the published version [here](https://atucker.shinyapps.io/just_final_shiny_app/).

Both open: 
* An interactive map of bird sightings
* A data summary tab
* A table of occurrences
* Buttons to load and download filtered data

### Data for analysis

All data used in this project was downloaded through our Shiny App using
the GBIF API.

The dataset includes two bird species: 
* Blue Tit (Cyanistes caeruleus)
* European Robin (Erithacus rubecula)

The downloaded dataset is saved in the repository under:

```{bash}
Data/GBIF_Erithacus_rubecula_2025.csv
```

and

```{bash}
Data/GBIF_Cyanistes_caeruleus_2025.csv
```

This file contains the exact data used for Tasks 2–4 in our statistical
analysis.

#### Download date

The dataset was retrieved on: 
* 25 November 2025

#### What the data contains

-   300 Blue Tit observations
-   300 European Robin observations
-   
    -   Geographic coordinates (latitude, longitude)
-   
    -   Measurement uncertainty
-   
    -   Metadata from GBIF’s occurrence records

### Run the Quarto Report

``` bash
quarto render analysis/MT5763_Puffins.qmd
```

This will generate the full .html report containing: 
* Jackknife SE results
* Regression outputs
* Randomisation test null distributions
* Bootstrap distributions and confidence intervals
* All figures used in the final submission

### Example Python snippet

``` py
from analysis.randomisation import randomisation_test_fast

T_obs, p_fast = randomisation_test_fast(data, n_permutations=1000)
print("Observed T:", T_obs)
print("Fast p-value:", p_fast)
```

## Installation instructions

### Requirements

-   Python 3.10+
-   Quarto
-   R 4.0+ (for running the Shiny APP)

### Python packages:

You can install the required Python libraries using either **pip** or **conda**, depending on your setup:

**Using pip:**

``` bash
pip install numpy pandas matplotlib statsmodels
```

**Using conda:**

``` bash
conda install numpy pandas matplotlib statsmodels
```

Both options will give you all the dependencies needed to run the analysis and render the Quarto report.

### Install R dependencies (for running the Shiny APP)

``` r
install.packages(c("shiny", "leaflet", "httr", "jsonlite"))
```

That’s it!
