# Capitalize the first letter of a character string.

Capitalize the first letter of a character string.

## Usage

``` r
taxize_capwords(s, strict = FALSE, onlyfirst = FALSE)
```

## Arguments

- s:

  A character string

- strict:

  Should the algorithm be strict about capitalizing. Defaults to FALSE.

- onlyfirst:

  Capitalize only first word, lowercase all others. Useful for taxonomic
  names.

## Examples

``` r
taxize_capwords(c("using AIC for model selection"))
#> [1] "Using AIC For Model Selection"
taxize_capwords(c("using AIC for model selection"), strict=TRUE)
#> [1] "Using aic for model selection"
```
