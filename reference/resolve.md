# Resolve names from different data sources

Resolve names from iPlant's name resolver, and the Global Names Resolver
(GNR)

## Usage

``` r
resolve(sci, db = "gnr", query = NULL, ...)
```

## Arguments

- sci:

  Vector of one or more taxonomic names (common names not supported)

- db:

  Source to check names against. One of iplant or gnr. Default: gnr.
  Note that each taxonomic data source has their own identifiers, so
  that if you provide the wrong `db` value for the identifier you could
  get a result, but it will likely be wrong (not what you were
  expecting).

- query:

  Deprecated, see `sci`

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  or
  [crul::verb-POST](https://docs.ropensci.org/crul/reference/verb-POST.html).
  In addition, further named args passed on to each respective function.
  See examples

## Value

A list with length equal to length of the db parameter (number of
sources requested), with each element being a data.frame or list with
results from that source.

## Examples

``` r
if (FALSE) { # \dontrun{
resolve(sci=c("Helianthus annuus", "Homo sapiens"))
resolve(sci="Quercus keloggii", db='gnr')
resolve(sci=c("Helianthus annuus", "Homo sapiens"), db=c('iplant', 'gnr'))
resolve(sci="Quercus keloggii", db=c('iplant', 'gnr'))

# pass in options specific to each source
resolve("Helianthus annuus", db = 'gnr', preferred_data_sources = c(3, 4))
resolve("Helianthus annuus", db = 'iplant', retrieve = 'best')
identical(
 resolve("Helianthus annuus", db = 'iplant', retrieve = 'best')$iplant,
 iplant_resolve("Helianthus annuus", retrieve = 'best')
)

# pass in curl options
resolve(sci="Qercuss", db = "iplant", verbose = TRUE)
} # }
```
