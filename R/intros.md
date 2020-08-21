Create files in data/ from files in data-raw/
================

This document creates the data in data/ from files in data-raw. It also
introduces rmarkdown, R, the tidyverse, iteration with purrr, and some
packages that play well with the tidyverse.

## Basics

This section shows the basics of most data-science tasks.

rmarkdown:

  - Share reports online with rmarkdown’s `output: github_document`.
  - Write prose with Markdown and insert chunks of R code.
  - Setup chunk.
  - Set global chunk options.
  - Set chunk-specific options.

R:

  - Assign a value to an object.
  - Call a function with 0, 1, 2, and 3 arguments.
  - Passing arguments to `...`
  - Compose functions by nesting.
  - Compose functions with the pipe.

tidyverse:

  - Use multiple packages at once.
  - Notice conflicts.

Friends of the tidyverse:

  - rmarkdown for communication.
  - here to write safe paths (crucial in rmarkdown documents).
  - fs to interact with the file system.
  - vroom to read multiple files at once and fast.
  - glue to paste strings in a readable way.

–

  - Use tidyverse packages and friends.

<!-- end list -->

``` r
library(tidyverse)
#> ── Attaching packages ───────────────────────────────────────────── tidyverse 1.3.0 ──
#> ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
#> ✓ tibble  3.0.3     ✓ dplyr   1.0.1
#> ✓ tidyr   1.1.1     ✓ stringr 1.4.0
#> ✓ readr   1.3.1     ✓ forcats 0.5.0
#> ── Conflicts ──────────────────────────────────────────────── tidyverse_conflicts() ──
#> x dplyr::filter() masks stats::filter()
#> x dplyr::lag()    masks stats::lag()
library(here)
#> here() starts at /home/rstudio/tidy-ds
library(vroom)

library(fs)
library(glue)
#> 
#> Attaching package: 'glue'
#> The following object is masked from 'package:dplyr':
#> 
#>     collapse
```

Explore the root of this repository.

``` r
# Call a function with no argument
here()
#> [1] "/home/rstudio/tidy-ds"

# Call a function with 1 argument
dir_ls(here())
#> /home/rstudio/tidy-ds/R
#> /home/rstudio/tidy-ds/README.md
#> /home/rstudio/tidy-ds/data
#> /home/rstudio/tidy-ds/data-raw
#> /home/rstudio/tidy-ds/open-science-with-r
#> /home/rstudio/tidy-ds/tidy-ds.Rproj

# Same output, different syntax: nest
out1 <- dir_ls(here())

# Same output, different syntax: pipe
out2 <- here() %>% dir_ls()

# Call a function with 2 arguments
identical(out1, out2)
#> [1] TRUE

# Same
out1 %>% identical(out2)
#> [1] TRUE
```

Explore datasets.

``` r
# Call a function with three arguments (one passed to ...) -- see `?dir_ls()`
here() %>% dir_ls(regex = "data", recurse = TRUE)
#> /home/rstudio/tidy-ds/data
#> /home/rstudio/tidy-ds/data/by-continent
#> /home/rstudio/tidy-ds/data/by-continent/africa.csv
#> /home/rstudio/tidy-ds/data/by-continent/americas.csv
#> /home/rstudio/tidy-ds/data/by-continent/asia.csv
#> /home/rstudio/tidy-ds/data/by-continent/europe.csv
#> /home/rstudio/tidy-ds/data/by-continent/oceania.csv
#> /home/rstudio/tidy-ds/data-raw
#> /home/rstudio/tidy-ds/data-raw/gap_wide.csv
#> /home/rstudio/tidy-ds/data-raw/gapminder.csv
#> /home/rstudio/tidy-ds/open-science-with-r/data
#> /home/rstudio/tidy-ds/open-science-with-r/data/gap_wide.csv
#> /home/rstudio/tidy-ds/open-science-with-r/data/gapminder.csv
```

Import `wide` data from data-raw/.

``` r
wide <- vroom(here("data-raw", "gap_wide.csv"))

wide
#> # A tibble: 142 x 38
#>    continent country gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 gdpPercap_1967
#>    <chr>     <chr>            <dbl>          <dbl>          <dbl>          <dbl>
#>  1 Africa    Algeria          2449.          3014.          2551.          3247.
#>  2 Africa    Angola           3521.          3828.          4269.          5523.
#>  3 Africa    Benin            1063.           960.           949.          1036.
#>  4 Africa    Botswa…           851.           918.           984.          1215.
#>  5 Africa    Burkin…           543.           617.           723.           795.
#>  6 Africa    Burundi           339.           380.           355.           413.
#>  7 Africa    Camero…          1173.          1313.          1400.          1508.
#>  8 Africa    Centra…          1071.          1191.          1193.          1136.
#>  9 Africa    Chad             1179.          1308.          1390.          1197.
#> 10 Africa    Comoros          1103.          1211.          1407.          1876.
#> # … with 132 more rows, and 32 more variables: gdpPercap_1972 <dbl>,
#> #   gdpPercap_1977 <dbl>, gdpPercap_1982 <dbl>, gdpPercap_1987 <dbl>,
#> #   gdpPercap_1992 <dbl>, gdpPercap_1997 <dbl>, gdpPercap_2002 <dbl>,
#> #   gdpPercap_2007 <dbl>, lifeExp_1952 <dbl>, lifeExp_1957 <dbl>,
#> #   lifeExp_1962 <dbl>, lifeExp_1967 <dbl>, lifeExp_1972 <dbl>,
#> #   lifeExp_1977 <dbl>, lifeExp_1982 <dbl>, lifeExp_1987 <dbl>,
#> #   lifeExp_1992 <dbl>, lifeExp_1997 <dbl>, lifeExp_2002 <dbl>,
#> #   lifeExp_2007 <dbl>, pop_1952 <dbl>, pop_1957 <dbl>, pop_1962 <dbl>,
#> #   pop_1967 <dbl>, pop_1972 <dbl>, pop_1977 <dbl>, pop_1982 <dbl>,
#> #   pop_1987 <dbl>, pop_1992 <dbl>, pop_1997 <dbl>, pop_2002 <dbl>,
#> #   pop_2007 <dbl>
```

## Beyond basics

This section shows `if()`, the not `!` operator, and the pattern
`glue("{variable} string")`.

–

Find `continents`.

``` r
continents <- wide %>% 
  distinct(continent) %>% 
  pull() %>% 
  tolower()

continents
#> [1] "africa"   "americas" "asia"     "europe"   "oceania"
```

Ensure data/by-continent/.

``` r
by_continent_path <- here("data", "by-continent")

by_continent_path
#> [1] "/home/rstudio/tidy-ds/data/by-continent"

if (!dir_exists(by_continent_path)) {
  dir_create(by_continent_path)
}
```

Create paths where to later save the data of each continent.

``` r
paths <- path(by_continent_path, glue("{continents}.csv"))

paths
#> /home/rstudio/tidy-ds/data/by-continent/africa.csv
#> /home/rstudio/tidy-ds/data/by-continent/americas.csv
#> /home/rstudio/tidy-ds/data/by-continent/asia.csv
#> /home/rstudio/tidy-ds/data/by-continent/europe.csv
#> /home/rstudio/tidy-ds/data/by-continent/oceania.csv
```

## Iteration purrr

This section shows how to iterate with purrr:

  - Apply a function to each element of a list.
  - Iterate over multiple inputs simultaneously.
  - Apply a function called primarily for its side effect.
  - Specify the expected output with specialized, `map_*()` functions.
  - Inline a function with the formula shortcut `~`.

–

Split data by continent and save it in data/ (side effect with no
output).

``` r
wide %>% 
  group_split(continent) %>% 
  walk2(paths, write_csv)
```

Confirm.

``` r
# See files
dir_ls(by_continent_path)
#> /home/rstudio/tidy-ds/data/by-continent/africa.csv
#> /home/rstudio/tidy-ds/data/by-continent/americas.csv
#> /home/rstudio/tidy-ds/data/by-continent/asia.csv
#> /home/rstudio/tidy-ds/data/by-continent/europe.csv
#> /home/rstudio/tidy-ds/data/by-continent/oceania.csv

# Read them back as a single data frame
df <- dir_ls(by_continent_path) %>% vroom()

df
#> # A tibble: 142 x 38
#>    continent country gdpPercap_1952 gdpPercap_1957 gdpPercap_1962 gdpPercap_1967
#>    <chr>     <chr>            <dbl>          <dbl>          <dbl>          <dbl>
#>  1 Africa    Algeria          2449.          3014.          2551.          3247.
#>  2 Africa    Angola           3521.          3828.          4269.          5523.
#>  3 Africa    Benin            1063.           960.           949.          1036.
#>  4 Africa    Botswa…           851.           918.           984.          1215.
#>  5 Africa    Burkin…           543.           617.           723.           795.
#>  6 Africa    Burundi           339.           380.           355.           413.
#>  7 Africa    Camero…          1173.          1313.          1400.          1508.
#>  8 Africa    Centra…          1071.          1191.          1193.          1136.
#>  9 Africa    Chad             1179.          1308.          1390.          1197.
#> 10 Africa    Comoros          1103.          1211.          1407.          1876.
#> # … with 132 more rows, and 32 more variables: gdpPercap_1972 <dbl>,
#> #   gdpPercap_1977 <dbl>, gdpPercap_1982 <dbl>, gdpPercap_1987 <dbl>,
#> #   gdpPercap_1992 <dbl>, gdpPercap_1997 <dbl>, gdpPercap_2002 <dbl>,
#> #   gdpPercap_2007 <dbl>, lifeExp_1952 <dbl>, lifeExp_1957 <dbl>,
#> #   lifeExp_1962 <dbl>, lifeExp_1967 <dbl>, lifeExp_1972 <dbl>,
#> #   lifeExp_1977 <dbl>, lifeExp_1982 <dbl>, lifeExp_1987 <dbl>,
#> #   lifeExp_1992 <dbl>, lifeExp_1997 <dbl>, lifeExp_2002 <dbl>,
#> #   lifeExp_2007 <dbl>, pop_1952 <dbl>, pop_1957 <dbl>, pop_1962 <dbl>,
#> #   pop_1967 <dbl>, pop_1972 <dbl>, pop_1977 <dbl>, pop_1982 <dbl>,
#> #   pop_1987 <dbl>, pop_1992 <dbl>, pop_1997 <dbl>, pop_2002 <dbl>,
#> #   pop_2007 <dbl>
```

Other purrr ways to do the same.

``` r
# Same
df1 <- dir_ls(by_continent_path) %>% 
  map(read_csv) %>% 
  reduce(bind_rows)

# Same
df2 <- dir_ls(by_continent_path) %>% 
  map_df(read_csv)

# Same
df3 <- dir_ls(by_continent_path) %>% 
  map_df(~read_csv(.x))

all_equal(df, df1)
#> [1] TRUE
all_equal(df, df2)
#> [1] TRUE
all_equal(df, df3)
#> [1] TRUE
```
