# tidy-ds

Tidy data-science workshop

## How to work with each lesson

Each lesson maps to a folder in this repo, and relates to a topic and an issue:

* Start each lesson on a new branch off master with `pr_init("#-topic")`, where `#` is the related issue and `topic` is the related topic -- e.g. `pr_init("01-rmarkdown")`.

* Copy the file `##-username.Rmd` as, for example, maurolepore.Rmd.

* Commit with a message like "Start #01" and submit a PR with `pr_push()`.

* Follow the instructions in `##-username.Rmd`.

* Commit after each section with an informative message and run `pr_sync()`.
