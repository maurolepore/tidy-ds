# tidy-ds

Tidy data-science: An online coding workshop for 2DII  
August 26-27, 1-5pm - Berlin time  

This workshop will cover the most useful bits of the [tidyverse](https://www.tidyverse.org/): The main features of [ggplot2](https://ggplot2.tidyverse.org/), [tidyr](https://tidyr.tidyverse.org/), [dplyr](https://dplyr.tidyverse.org/), and [purrr](https://purrr.tidyverse.org/). It will also help you practice other tools that are crucial for data science but won't be the focus of any specific lesson: Rmarkdown, RStudio, Git, and GitHub.

## General objectives

* Overview the main features of ggplot2, tidyr, dplyr, and purrr.
* Solve iteration problems with purrr and dplyr instead of `for()` loops.
* Practice working with Rmarkdown, RStudio, Git, and GitHub.

## Before the workshop setup usethis and the tidy-ds repo on rstudio.cloud

Please do this before the workshop to ensure we all have the same R environment; this avoids problems and saves time. You may ask for help on the #tidy-ds channel on Slack.

* Setup usethis on [rstudio.cloud](https://login.rstudio.cloud/) following [this 16' video](https://youtu.be/A_Q6nmUhcGA).

* Fork and clone the workshop materials into the home directory of rstudio.cloud:

```r
create_from_github("2DegreesInvesting/tidy-ds", destdir = "~", fork = TRUE)
```

* Install the packages tidyverse and here with:

```r
install.packages(c("tidyverse", "here"))
```

## Links

* Google doc: https://bit.ly/2020-08-26-tidy-ds
* tidy-ds repository: https://github.com/2DegreesInvesting/tidy-ds

