# Open Specy

Analyze, Process, Identify, and Share, Raman and (FT)IR Spectra

<!-- badges: start -->
[![Project Status](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![R-CMD-check](https://github.com/wincowgerDEV/OpenSpecy/workflows/R-CMD-check/badge.svg)](https://github.com/wincowgerDEV/OpenSpecy/actions)
[![License: CC BY 4.0](https://img.shields.io/badge/license-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Website](https://img.shields.io/badge/web-openspecy.org-white)](http://www.openspecy.org)
[![Twitter Follow](https://img.shields.io/twitter/follow/OpenSpecy)](https://twitter.com/OpenSpecy)
<!-- badges: end -->

![Graphical Abstract](https://github.com/wincowgerDEV/OpenSpecy/blob/main/inst/shiny/www/graphical_abstract.png?raw=true)

## :warning: This R package is currently under active development and not intended for productive use; visit [openspecy.org](https://wincowger.shinyapps.io/OpenSpecy/) for a stable version!


## Installation

<!-- **OpenSpecy** is available from CRAN and GitHub.

### Install from CRAN (stable version)

You can install the released version of **OpenSpecy** from
[CRAN](https://CRAN.R-project.org) with:

```r
install.packages("envalysis")
```
-->

### Install from GitHub (development version)

To install the development version of this package, paste the following code
into your R console (requires **devtools**):

```r
if (!require(devtools)) install.packages("devtools")
devtools::install_github("wincowgerDEV/OpenSpecy")
```

## Getting started
```r
library(OpenSpecy)
run_app()
```

## Workflow

```r
library(dplyr)

# Fetch current spectral library from https://osf.io/x7dpz/
get_lib()

# Load library into global environment
spec_lib <- load_lib()

# Sample spectrum
data("raman_hdpe")

# Share your spectrum with the Open Spey community
share_spectrum(raman_hdpe,
               metadata = c(user_name = "Win Cowger",
                            contact_info = "wincowger@gmail.com",
                            spectrum_type = "Raman",
                            spectrum_identity = "HDPE")
               )

# Adjust spectral intensity
raman_adj <- raman_hdpe %>%
  adjust_intensity()

# Smooth and background-correct spectrum
raman_proc <- raman_adj %>% 
  smooth_intensity() %>% 
  subtract_background()

# Match spectrum with library and retrieve meta data
match_spectrum(raman_proc, library = spec_lib, which = "raman")

find_spectrum(sample_name == 5381, library = spec_lib, which = "raman")
```

