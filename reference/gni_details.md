# Search for taxonomic name details using the Global Names Index

Uses the Global Names Index, see http://gni.globalnames.org/

## Usage

``` r
gni_details(id, all_records = 1, ...)
```

## Arguments

- id:

  Name id. Required.

- all_records:

  If all_records is 1, GNI returns all records from all repositories for
  the name string (takes 0, or 1 \[default\]).

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

Data.frame of results.

## See also

[`gnr_datasources()`](https://docs.ropensci.org/taxize/reference/gnr_datasources.md),
[`gna_search()`](https://docs.ropensci.org/taxize/reference/gna_search.md).

## Author

Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
gni_details(id = 17802847)

# pass on curl options
gni_details(id = 17802847, verbose = TRUE)
} # }
```
