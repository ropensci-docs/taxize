# Lookup taxa in Kew's Plants of the World

Lookup taxa in Kew's Plants of the World

## Usage

``` r
pow_lookup(id, include = NULL, ...)
```

## Arguments

- id:

  (character) taxon id. required

- include:

  (character) vector of additional fields to include in results. options
  include 'distribution' and 'descriptions'. optional

- ...:

  Further args passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html).

## See also

Other pow:
[`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md),
[`pow_search()`](https://docs.ropensci.org/taxize/reference/pow_search.md),
[`pow_synonyms()`](https://docs.ropensci.org/taxize/reference/pow_synonyms.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pow_lookup(id = 'urn:lsid:ipni.org:names:320035-2')
pow_lookup(id = 'urn:lsid:ipni.org:names:320035-2',
  include = "distribution")
pow_lookup(id = 'urn:lsid:ipni.org:names:320035-2',
  include = c("distribution", "descriptions"))
} # }
```
