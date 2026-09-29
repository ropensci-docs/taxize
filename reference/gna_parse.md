# Parse scientific names using Global Names Parser

Parse scientific names using Global Names Parser

## Usage

``` r
gna_parse(names, ...)
```

## Arguments

- names:

  A vector of length 1 or more taxonomic names

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

A data.frame with results, the submitted names, and the parsed names
with additional information.

## References

http://gni.globalnames.org/

## See also

[`gbif_parse()`](https://docs.ropensci.org/taxize/reference/gbif_parse.md),
[`gni_parse()`](https://docs.ropensci.org/taxize/reference/gni_parse.md)

## Examples

``` r
if (FALSE) { # \dontrun{
gna_parse("Cyanistes caeruleus")
gna_parse("Plantago minor")
gna_parse("Plantago minor minor")
gna_parse(c("Plantago minor minor","Helianthus annuus texanus"))

# if > 20 names, uses an HTTP POST request
x <- names_list("species", size = 30)
gna_parse(x)

# pass on curl options
gna_parse("Cyanistes caeruleus", verbose = TRUE)
} # }
```
