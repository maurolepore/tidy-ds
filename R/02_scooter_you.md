Scooter
================

**Collapse all chunks with Alt+O / Cmd+Option+O**

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

# Your turn

  - Explore.

<!-- end list -->

``` r
gapminder %>% 
  glimpse()
#> Rows: 1,704
#> Columns: 6
#> $ country   <chr> "Afghanistan", "Afghanistan", "Afghanistan", "Afghanistan",…
#> $ continent <chr> "Asia", "Asia", "Asia", "Asia", "Asia", "Asia", "Asia", "As…
#> $ year      <dbl> 1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992, 1997,…
#> $ lifeExp   <dbl> 28.801, 30.332, 31.997, 34.020, 36.088, 38.438, 39.854, 40.…
#> $ pop       <dbl> 8425333, 9240934, 10267083, 11537966, 13079460, 14880372, 1…
#> $ gdpPercap <dbl> 779.4453, 820.8530, 853.1007, 836.1971, 739.9811, 786.1134,…
```

  - Find `distinct()` values of `continent`.

<!-- end list -->

``` r
gapminder %>% distinct(continent)
#> # A tibble: 5 x 1
#>   continent
#>   <chr>    
#> 1 Asia     
#> 2 Europe   
#> 3 Africa   
#> 4 Americas 
#> 5 Oceania
```

  - Subset rows where `continent` is “Americas” or “Europe”.

<!-- end list -->

``` r
continents <- c("Americas", "Europe")
gapminder %>% filter(continent %in% continents)
#> # A tibble: 660 x 6
#>    country continent  year lifeExp     pop gdpPercap
#>    <chr>   <chr>     <dbl>   <dbl>   <dbl>     <dbl>
#>  1 Albania Europe     1952    55.2 1282697     1601.
#>  2 Albania Europe     1957    59.3 1476505     1942.
#>  3 Albania Europe     1962    64.8 1728137     2313.
#>  4 Albania Europe     1967    66.2 1984060     2760.
#>  5 Albania Europe     1972    67.7 2263554     3313.
#>  6 Albania Europe     1977    68.9 2509048     3533.
#>  7 Albania Europe     1982    70.4 2780097     3631.
#>  8 Albania Europe     1987    72   3075321     3739.
#>  9 Albania Europe     1992    71.6 3326498     2497.
#> 10 Albania Europe     1997    73.0 3428038     3193.
#> # … with 650 more rows
```

  - Subset rows where `continent` is one of .

<!-- end list -->

``` r
continents <- c("Americas", "Europe")
gapminder %>% filter(continent %in% continents)
#> # A tibble: 660 x 6
#>    country continent  year lifeExp     pop gdpPercap
#>    <chr>   <chr>     <dbl>   <dbl>   <dbl>     <dbl>
#>  1 Albania Europe     1952    55.2 1282697     1601.
#>  2 Albania Europe     1957    59.3 1476505     1942.
#>  3 Albania Europe     1962    64.8 1728137     2313.
#>  4 Albania Europe     1967    66.2 1984060     2760.
#>  5 Albania Europe     1972    67.7 2263554     3313.
#>  6 Albania Europe     1977    68.9 2509048     3533.
#>  7 Albania Europe     1982    70.4 2780097     3631.
#>  8 Albania Europe     1987    72   3075321     3739.
#>  9 Albania Europe     1992    71.6 3326498     2497.
#> 10 Albania Europe     1997    73.0 3428038     3193.
#> # … with 650 more rows
```

  - Subset rows where `continent` is in `params$continents`.

<!-- end list -->

``` r
gapminder %>% filter(continent %in% params$continents)
#> # A tibble: 0 x 6
#> # … with 6 variables: country <chr>, continent <chr>, year <dbl>,
#> #   lifeExp <dbl>, pop <dbl>, gdpPercap <dbl>
```

Subset columns using their names and types:

  - Select all columns except `country` and `continent`.

<!-- end list -->

``` r
gapminder %>% select()
#> # A tibble: 1,704 x 0
```

``` r
subset_cols <- gapminder %>% 
  select(continent, lifeExp, year) %>% 
  # Returns invisible.
  glimpse() %>% 
  filter(year >= 1980)
#> Rows: 1,704
#> Columns: 3
#> $ continent <chr> "Asia", "Asia", "Asia", "Asia", "Asia", "Asia", "Asia", "As…
#> $ lifeExp   <dbl> 28.801, 30.332, 31.997, 34.020, 36.088, 38.438, 39.854, 40.…
#> $ year      <dbl> 1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992, 1997,…

subset_cols
#> # A tibble: 852 x 3
#>    continent lifeExp  year
#>    <chr>       <dbl> <dbl>
#>  1 Asia         39.9  1982
#>  2 Asia         40.8  1987
#>  3 Asia         41.7  1992
#>  4 Asia         41.8  1997
#>  5 Asia         42.1  2002
#>  6 Asia         43.8  2007
#>  7 Europe       70.4  1982
#>  8 Europe       72    1987
#>  9 Europe       71.6  1992
#> 10 Europe       73.0  1997
#> # … with 842 more rows
```

  - Boxplot `lifeExp` for each continent `continent` (see
    `?geom_boxplot()`).

<!-- end list -->

``` r
ggplot(data = gapminder, aes(x = continent, y = lifeExp)) +
  geom_boxplot()
```

![](02_scooter_you_files/figure-gfm/boxplot-1.png)<!-- -->
