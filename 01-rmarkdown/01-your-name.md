
## Initialize pull request

  - Remember to initialize a pull request with `pr_init()`.

  - Rename this file with your name, e.g. from your-name.Rmd to
    mauro.Rmd.

  - Commit with a meaningful message, e.g. “Personalise your-name.Rmd”.

## Setup options and packages

  - The first chunk of an .Rmd file is usually called “setup” and
    includes options, such as `echo = TRUE`, that modify the output.
    Kint this document; then add the options `comment = "#>"` and
    `collapse = TRUE` to `knitr::opts_chunk$set()`, and knit again.
    Based on your results, explain what these options do?:
    
      - `echo = TRUE`: …
      - `collapse = TRUE`: …
      - `comment = #>`: …

  - It’s good practice to include all calls to `library()` at the top of
    your script. Why not include do this in the `setup` chunk?

<!-- end list -->

``` r
library(usethis)
library(praise)
```

  - You can also pass options to specific chunks. Change the chunk `{r
    greetings}` to `{r greetings, comment = ">"}`. Why should chunk
    comments start with `#` instead of any other symbol (e.g. `>`)?

<!-- end list -->

``` r
paste(params$name, praise())
#> [1] "your-name You are stunning!"
```

  - Commit with a meaningful message, e.g. “Tweak chunk options”.

## Outputs

  - Create a .pdf file: Change the `output:` to `pdf_document` and knit.

  - Create a .word file: Change the `output:` to `word_document` and
    knit.

  - Ignore all outputs except the .md file.

  - Commit with a meaningful message, e.g. “Ignore .pdf and .docx
    outputs”.

## Formatting

How is this chunk similar to the other chunks? How is it different?

``` r
git_sitrep()
```

## Params

  - In the YAML header, replace “your-name” with your name. See how this
    works, then add a new `params` and use it however you like:

<!-- end list -->

``` r
# Your code goes here; it should use the variable params$your-new-param
```

## Submit

  - Use `pr_push()` to submit a pull request with your changes to the
    .Rmd source and the .md output.
