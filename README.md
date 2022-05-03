
<!-- README.md is generated from README.Rmd. Please edit that file -->

<img src="man/figures/logo.png" align="right" height="139" />

# ggblanket

<!-- badges: start -->

[![CRAN
status](https://www.r-pkg.org/badges/version/ggblanket)](https://CRAN.R-project.org/package=ggblanket)
<!-- badges: end -->

## Overview

ggblanket is a package of wrapper functions around the amazing ggplot2
package.

Hence the blanket metaphor.

The primary objective of the package is to help users make beautiful
ggplot2 visualisation with less code and less cognitive load.

A secondary objective is to help users build intuition for ggplot2, such
that they can move between ggplot2 and ggblanket as needed.

With these objectives in mind, the ggblanket package:

-   uses quick functions that wrap around a single geom
-   merges col and fill aesthetics into a single col aesthetic
-   provides colour customisation via a pal argument
-   treats faceting as an aesthetic
-   pushes x and y limits to the max of the x and y breaks by default
-   arranges horizontal geom y and col labels etc to be in correct order
-   converts titles and labels to sentence case and comma format by
    default
-   provides arguments for scale adjustment and legend placement
-   changes default colours, alphas, widths and themes
-   allows users to access all other non-aesthetic geom functionality
-   keeps all stat and position arguments consistent with the applicable
    geom’s

## Installation

You can install the development version of ggblanket from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("davidhodge931/ggblanket")
```

## Examples

``` r
library(dplyr)
library(ggplot2)
library(ggblanket)
library(palmerpenguins)
```

``` r
penguins %>% 
  tidyr::drop_na() %>% 
  mutate(body_mass_kg = body_mass_g / 1000) %>%
  ggplot() +
  geom_histogram(aes(x = body_mass_kg)) 
```

<img src="man/figures/README-unnamed-chunk-3-1.png" width="100%" />

``` r
penguins %>% 
  tidyr::drop_na() %>% 
  mutate(body_mass_kg = body_mass_g / 1000) %>% 
  gg_histogram(x = body_mass_kg) 
```

<img src="man/figures/README-unnamed-chunk-4-1.png" width="100%" />

``` r
penguins %>%
  tidyr::drop_na(sex) %>%
  group_by(species, sex, island) %>%
  summarise(body_mass_kg = mean(body_mass_g) / 1000) %>%
  ggplot() +
  geom_col(
    aes(x = body_mass_kg, y = species, fill = sex), 
    position = "dodge"
    ) +
  facet_wrap( ~ island) +
  theme(legend.position = "bottom")
```

<img src="man/figures/README-unnamed-chunk-5-1.png" width="100%" />

``` r
penguins %>%
  tidyr::drop_na(sex) %>%
  group_by(species, sex, island) %>%
  summarise(body_mass_kg = mean(body_mass_g) / 1000) %>%
  gg_col(
    x = body_mass_kg,
    y = species,
    col = sex,
    facet = island,
    position = "dodge",
    col_legend_place = "b"
  )
```

<img src="man/figures/README-unnamed-chunk-6-1.png" width="100%" />

Other nice graphs

``` r
penguins %>%
  tidyr::drop_na(sex) %>% 
  mutate(body_mass_kg = body_mass_g / 1000) %>% 
  gg_histogram(
    x = body_mass_kg,
    col = species, 
    facet = sex, 
    col_legend_place = "b", 
    pal = pals::brewer.dark2(3))
```

<img src="man/figures/README-unnamed-chunk-7-1.png" width="100%" />

``` r
storms %>% 
  group_by(year) %>% 
  summarise(wind = mean(wind, na.rm = TRUE)) %>% 
  gg_line(x = year, 
          y = wind, 
          y_zero = TRUE,
          x_labels = ~.x, 
          title = "USA average storm wind speed, 1975-2020",
          subtitle = "Storms are stormy", 
          y_title = "Wind speed (knots)") +
  geom_point()
```

<img src="man/figures/README-unnamed-chunk-8-1.png" width="100%" />

``` r
penguins %>% 
  tidyr::drop_na() %>% 
  mutate(body_mass_kg = body_mass_g / 1000) %>% 
  gg_density(
    y = body_mass_kg, 
    col = sex, 
    facet = species)
```

<img src="man/figures/README-unnamed-chunk-9-1.png" width="100%" />

``` r
simplevis::example_polygon %>% 
  gg_sf(density)
```

<img src="man/figures/README-unnamed-chunk-10-1.png" width="100%" />
