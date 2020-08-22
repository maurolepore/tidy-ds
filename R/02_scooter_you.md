Scooter
================

**Collapse all chunks with Alt+O / Cmd+Option+O**

## Setup

  - Packages.

<!-- end list -->

``` r
library(tidyverse)
#> ── Attaching packages ──────────────────────────────── tidyverse 1.3.0 ──
#> ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
#> ✓ tibble  3.0.3     ✓ dplyr   1.0.1
#> ✓ tidyr   1.1.1     ✓ stringr 1.4.0
#> ✓ readr   1.3.1     ✓ forcats 0.5.0
#> ── Conflicts ─────────────────────────────────── tidyverse_conflicts() ──
#> x dplyr::filter() masks stats::filter()
#> x dplyr::lag()    masks stats::lag()
library(here)
#> here() starts at /home/rstudio/tidy-ds
```

  - Import – [practice safe paths](https://rstats.wtf/safe-paths.html).

<!-- end list -->

``` r
gapminder <- read_csv(here("data", "gapminder.csv"))
#> Parsed with column specification:
#> cols(
#>   country = col_character(),
#>   continent = col_character(),
#>   year = col_double(),
#>   lifeExp = col_double(),
#>   pop = col_double(),
#>   gdpPercap = col_double()
#> )
```

  - Explore.

<!-- end list -->

``` r
glimpse(gapminder)
#> Rows: 1,704
#> Columns: 6
#> $ country   <chr> "Afghanistan", "Afghanistan", "Afghanistan", "Afghanistan",…
#> $ continent <chr> "Asia", "Asia", "Asia", "Asia", "Asia", "Asia", "Asia", "As…
#> $ year      <dbl> 1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992, 1997,…
#> $ lifeExp   <dbl> 28.801, 30.332, 31.997, 34.020, 36.088, 38.438, 39.854, 40.…
#> $ pop       <dbl> 8425333, 9240934, 10267083, 11537966, 13079460, 14880372, 1…
#> $ gdpPercap <dbl> 779.4453, 820.8530, 853.1007, 836.1971, 739.9811, 786.1134,…
```

  - Boxplot `lifeExp` for each continent `continent` (see
    `?geom_boxplot()`).

<!-- end list -->

``` r
ggplot(data = _________, aes(x = _________, y = _______)) +
  geom________()
```

![](02_scooter_you_files/figure-gfm/boxplot-3-1.png)<!-- -->
