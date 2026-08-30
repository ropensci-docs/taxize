# iPlant name resolution

iPlant name resolution

## Usage

``` r
iplant_resolve(sci, retrieve = "all", query = NULL, ...)
```

## Arguments

- sci:

  Vector of one or more taxonomic names (no common names)

- retrieve:

  Specifies whether to retrieve all matches for the names submitted. One
  of 'best' (retrieves only the single best match for each name
  submitted) or 'all' (retrieves all matches)

- query:

  Deprecated, see `sci`

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

A data.frame

## Examples

``` r
if (FALSE) { # \dontrun{
iplant_resolve(sci=c("Helianthus annuus", "Homo sapiens"))
iplant_resolve("Helianthusss")
iplant_resolve("Pooa")
iplant_resolve("Helianthusss", verbose = TRUE)
} # }
```
