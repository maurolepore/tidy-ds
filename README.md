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

1. Setup usethis on [rstudio.cloud](https://login.rstudio.cloud/) following [this 16' video](https://youtu.be/A_Q6nmUhcGA).

2. Fork and clone the tidy-ds repository into the home directory of the rstudio.cloud project you setup in (1):

```r
create_from_github("2DegreesInvesting/tidy-ds", destdir = "~", fork = TRUE)
```

3. Install the tidyverse packages and friends:

```r
install.packages(c("tidyverse", "here", "vroom"))
```

## Links

* Google doc: https://bit.ly/2020-08-26-tidy-ds
* tidy-ds repository: https://github.com/2DegreesInvesting/tidy-ds

## How to

Work with usethis:

* Use usethis with `library(usethis)` or `devtools::use_devtools()`.
* Use `pr_init()` to initialize work on a new pull-request branch.
* Use `pr_pause()` to pause work on a pull-request branch (to start a new one).
* Use RStudio's branch menu (Git pane) to switch between pull-request branches.
* Use `pr_sync()` to update a pull-request branch against `upstream`.

Work on a task:


1. Initialize a pull request with `pr_init("task_you")` (you is your name).
1. _Copy_ (don't rename) `task_you.Rmd` (a new file with your name).
1. Submit a draft pull request with `pr_push()`.
1. Open `task_you.Rmd` and collapse all chunks with Alt+o (or Alt+Shift+o).
1. Attempt each sub-task expanding only one of the three chunks:
  * `sub-task-1` is harder; type everything from scratch.
  * `sub-task-2` is easier; fill the blanks then set `eval = TRUE`.
  * `sub-task-3` is done; check it to debug or confirm.
1. Commit your sub-task with a meaningful message
1. Update the pull-request with `pr_sync()`.
