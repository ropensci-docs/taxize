# Return summary data a taxon name with a given id.

Return summary data a taxon name with a given id.

## Usage

``` r
tp_summary(id, key = NULL, ...)
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

A data.frame.

## Examples

``` r
if (FALSE) { # \dontrun{
tp_summary(id = 25509881)
tp_summary(id = 2700851)
tp_summary(id = 24900183)
} # }
```
