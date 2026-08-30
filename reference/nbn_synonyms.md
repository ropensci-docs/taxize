# Return all synonyms for a taxon name with a given id from NBN

Return all synonyms for a taxon name with a given id from NBN

## Usage

``` r
nbn_synonyms(id, ...)
```

## Arguments

- id:

  the taxon identifier code

- ...:

  Further args passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

A data.frame

## References

https://api.nbnatlas.org/

## See also

Other nbn:
[`get_nbnid()`](https://docs.ropensci.org/taxize/reference/get_nbnid.md),
[`nbn_classification()`](https://docs.ropensci.org/taxize/reference/nbn_classification.md),
[`nbn_search()`](https://docs.ropensci.org/taxize/reference/nbn_search.md)

## Examples

``` r
if (FALSE) { # \dontrun{
nbn_synonyms(id = 'NHMSYS0001501147')
nbn_synonyms(id = 'NHMSYS0000456036')

# none
nbn_synonyms(id = 'NHMSYS0000502940')
} # }
```
