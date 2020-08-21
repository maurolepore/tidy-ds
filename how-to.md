Work with usethis:

* Use usethis with `library(usethis)` or `devtools::use_devtools()`.
* Use `pr_init()` to initialize work on a new pull-request branch.
* Use `pr_pause()` to pause work on a pull-request branch (to start a new one).
* Use RStudio's branch menu (Git pane) to switch between pull-request branches.
* Use `pr_sync()` to update a pull-request branch against `upstream`.

Work on a task:

1. Initialize a pull request with `pr_init()`.
2. Copy (don't rename) `task_your-name.Rmd` as a new file with your name.
3. Submit a draft pull request with `pr_push()`.
4. Do each sub-task in `task_your-name.Rmd` in only one of the three chunks:
  * `some-label-1` is harder; type everything from scratch.
  * `some-label-2` is easier; fill the blanks then set `eval = TRUE`.
  * `some-label-3` is done; check it to debug or confirm.
5. Commit your sub-task with a meaningful message
6. Update the pull-request with `pr_sync()`.
