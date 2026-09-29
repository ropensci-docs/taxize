# Return all accepted names for a taxon name with a given id.

Return all accepted names for a taxon name with a given id.

## Usage

``` r
tp_accnames(id, key = NULL, ...)
```

## Arguments

- id:

  the taxon identifier code

- key:

  Your Tropicos API key; See
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
  for help on authentication

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

List or dataframe.

## Examples

``` r
if (FALSE) { # \dontrun{
tp_accnames(id = 25503923)
tp_accnames(id = 25538750)

# No accepted names found
tp_accnames(id = 25509881)
} # }
```
