# Extractor functions for `iucn`-class.

Extractor functions for `iucn`-class.

## Usage

``` r
iucn_status(x, ...)
```

## Arguments

- x:

  an `iucn`-object as returned b`iucn_summary`ry

- ...:

  Currently not used

## Value

A character vector with the status.

## See also

[`iucn_summary()`](https://docs.ropensci.org/taxize/reference/iucn_summary.md)

## Examples

``` r
if (FALSE) { # \dontrun{
ia <- iucn_summary(c("Panthera uncia", "Lynx lynx"))
iucn_status(ia)} # }
```
