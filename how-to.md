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
