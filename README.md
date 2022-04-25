
<!-- README.md is generated from README.Rmd. Please edit that file -->

<img src="man/figures/logo.png" align="right" height="139" />

# ggblanket

<!-- badges: start -->

[![CRAN
status](https://www.r-pkg.org/badges/version/ggblanket)](https://CRAN.R-project.org/package=ggblanket)
<!-- badges: end -->

The goal of ggblanket is to assist users make beautiful ggplots faster
and with less brainpower - while building intuition for how ggplot2
works.

## Installation

You can install the development version of ggblanket from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("davidhodge931/ggblanket")
```

## Example

This is a basic example which shows you how to solve a common problem:

``` r
library(ggblanket)
## basic example code
```

``` r
summary(cars)
#>      speed           dist       
#>  Min.   : 4.0   Min.   :  2.00  
#>  1st Qu.:12.0   1st Qu.: 26.00  
#>  Median :15.0   Median : 36.00  
#>  Mean   :15.4   Mean   : 42.98  
#>  3rd Qu.:19.0   3rd Qu.: 56.00  
#>  Max.   :25.0   Max.   :120.00
```

## Wrapper functions available

-   `gg_area`
-   `gg_bar`  
-   `gg_blank`  
-   `gg_boxplot`  
-   `gg_col`  
-   `gg_crossbar`
-   `gg_density`
-   `gg_errorbar`
-   `gg_freqpoly`
-   `gg_function`
-   `gg_histogram`  
-   `gg_jitter`  
-   `gg_label`
-   `gg_line`
-   `gg_linerange`
-   `gg_path`
-   `gg_point`  
-   `gg_pointrange`  
-   `gg_polygon`
-   `gg_qq`
-   `gg_raster`  
-   `gg_rect`
-   `gg_ribbon`
-   `gg_rug`
-   `gg_segment`  
-   `gg_sf`  
-   `gg_smooth`  
-   `gg_step`
-   `gg_text`
-   `gg_theme`
-   `gg_tile`
-   `gg_violin`

Default changes: - gg_sf defaults coord_sf and gg_theme(void = TRUE) -
gg_qq defaults oob_squish - width default = 0.75 for categorical vars -
size defaults 0.75 - alpha for fill defaults to 0.9 generally - alpha on
boxplot and smooth is 0.25

# library(palmerpenguins)

# 

# penguins \|\>

# gg_point(x = flipper_length_mm,

# y = body_mass_g)

# 

# penguins \|\>

# gg_point(x = flipper_length_mm,

# y = body_mass_g,

# col = sex)

# 

# penguins \|\>

# gg_point(x = flipper_length_mm,

# y = body_mass_g,

# col = species)

# 

# penguins \|\>

# gg_point(x = body_mass_g,

# y = species,

# col = sex)

# 

# penguins \|\>

# gg_point(x = body_mass_g,

# y = species,

# col = flipper_length_mm)

# 

# penguins \|\>

# gg_point(x = flipper_length_mm,

# y = body_mass_g,

# col = sex,

# facet = species)

# 

# penguins \|\>

# gg_point(x = body_mass_g,

# y = species,

# col = sex)
