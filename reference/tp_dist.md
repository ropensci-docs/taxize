# Return all distribution records for for a taxon name with a given id.

Return all distribution records for for a taxon name with a given id.

## Usage

``` r
tp_dist(id, key = NULL, ...)
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

List of two data.frame's, one named "location", and one "reference".

## References

http://services.tropicos.org/help?method=GetNameDistributionsXml

## Examples

``` r
if (FALSE) { # \dontrun{
# Query using a taxon name Id
out <- tp_dist(id = 25509881)
## just location data
head(out[['location']])
## just reference data
head(out[['reference']])
} # }
```
