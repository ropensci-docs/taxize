# Lookup synonyms in Kew's Plants of the World

Lookup synonyms in Kew's Plants of the World

## Usage

``` r
pow_synonyms(id, ...)
```

## Arguments

- id:

  (character) taxon id. required

- ...:

  Further args passed on to
  [`pow_lookup()`](https://docs.ropensci.org/taxize/reference/pow_lookup.md)

## See also

Other pow:
[`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md),
[`pow_lookup()`](https://docs.ropensci.org/taxize/reference/pow_lookup.md),
[`pow_search()`](https://docs.ropensci.org/taxize/reference/pow_search.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pow_synonyms(id = 'urn:lsid:ipni.org:names:320035-2')
pow_synonyms(id = 'urn:lsid:ipni.org:names:358881-1')
pow_synonyms(id = 'urn:lsid:ipni.org:names:359855-1')
} # }
```
