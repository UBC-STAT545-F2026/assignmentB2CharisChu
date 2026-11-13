
<!-- README.md is generated from README.Rmd. Please edit that file -->

# assignmentB2CharisChu

<!-- badges: start -->

<!-- badges: end -->

The goal of assignmentB2CharisChu is to allow users to easily see
missing values in data to determine if datasets are suitable for
analysis.

## Installation

You can install the development version of assignmentB2CharisChu from
[GitHub](https://github.com/) with:

``` r
devtools::install_github("UBC-STAT545-F2026/assignmentB2CharisChu")
```

## Example

This is a basic example which shows you how to use the
`count_all_missing_by_group` function from the `assignmentB2CharisChu`
package.

``` r
library(tidyverse)
#> Warning: package 'tibble' was built under R version 4.4.3
#> Warning: package 'dplyr' was built under R version 4.4.3
#> ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
#> ✔ dplyr     1.2.1     ✔ readr     2.1.5
#> ✔ forcats   1.0.0     ✔ stringr   1.5.1
#> ✔ ggplot2   3.5.1     ✔ tibble    3.3.1
#> ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
#> ✔ purrr     1.0.2     
#> ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
#> ✖ dplyr::filter() masks stats::filter()
#> ✖ dplyr::lag()    masks stats::lag()
#> ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
library(palmerpenguins)
#> Warning: package 'palmerpenguins' was built under R version 4.4.3
library(assignmentB2CharisChu)
# Compute the number of missing values in the `airquality` dataset grouped by the `cyl` column.
count_all_missing_by_group(airquality, Month)
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0

# This example has the same output as the last example, but shows off an alternative way of invoking the `count_all_missing_by_group()`: piping the dataset into the function.
airquality |> count_all_missing_by_group(Month)
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0

# The optional `.groups` argument allows us to keep the output grouped by the grouping column. See example below; notice how the output is a grouped tibble, rather than the ungrouped tibble output of the earlier examples.
count_all_missing_by_group(airquality, Month, .groups = "keep")
#> # A tibble: 5 × 6
#> # Groups:   Month [5]
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```
