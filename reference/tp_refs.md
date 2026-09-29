# Return all reference records for for a taxon name with a given id.

Return all reference records for for a taxon name with a given id.

## Usage

``` r
tp_refs(id, key = NULL, ...)
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
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

List or dataframe.

## Examples

``` r
if (FALSE) { # \dontrun{
tp_refs(id = 25509881)
} # }
```
