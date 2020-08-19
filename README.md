# tidy-ds

Tidy data-science workshop

## How to work

Each folder relates to a topic and an issue.

* Initialize a pull request like `pr_init("#-topic")`, where `#` is the related issue and `topic` is the related topic -- e.g. `pr_init("01-rmarkdown")`.

* Copy this file as (GitHub) username.Rmd, e.g. maurolepore.Rmd.

* Submit a pull request with `pr_push()` and mark it as a draft.

* Commit after each section with an informative message and run `pr_sync()`, e.g.:

```
Copy .Rmd to mauro.Rmd

Relates to #01
```
