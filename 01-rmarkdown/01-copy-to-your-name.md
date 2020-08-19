
## Initialize

  - Initialize a pull request with `pr_init("01-your-name")`.

  - Copy this file as your-name.Rmd, e.g. mauro.Rmd.

## Global chunk-options

  - The first chunk of an .Rmd file is usually called `setup` and
    includes options that modify the output. These are my favourite
    options. What do they do? Experiment.

## Setup packages

  - It’s good practice to include all calls to `library()` at the top of
    your script. Why not include do this in the `setup` chunk? What does
    `include=FALSE` do in the `setup` chunk?

<!-- end list -->

``` r
library(praise)
```

## Chunk-specific options

  - Make this chunk output comments of the form “x\>”. Why should chunk
    comments always start with `#`?

<!-- end list -->

``` r
praise()
#> [1] "You are hunky-dory!"
```

  - Commit with a meaningful message, e.g. “Tweak chunk options”.

## Outputs

  - Change `output:` to `pdf_document` and knit.

  - Remove the .pdf output and revert the change to your-name.Rmd.

## Params

  - Click on *Knit \> Knit with Parameters …* and add your name so the
    code below prises you. How could you use `params` in real life?

<!-- end list -->

``` r
paste(params$name, praise())
#> [1] "Mauro Lepore You are impressive!"
```

## Submit

  - Use `pr_push()` to submit a pull request with your changes to the
    .Rmd source and the .md output.
