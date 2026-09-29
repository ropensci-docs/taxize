# Search UK National Biodiversity Network database for taxonomic classification

Search UK National Biodiversity Network database for taxonomic
classification

## Usage

``` r
nbn_classification(id, ...)
```

## Arguments

- id:

  (character) An NBN identifier.

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
[`nbn_search()`](https://docs.ropensci.org/taxize/reference/nbn_search.md),
[`nbn_synonyms()`](https://docs.ropensci.org/taxize/reference/nbn_synonyms.md)

## Author

Scott Chamberlain,

## Examples

``` r
if (FALSE) { # \dontrun{
nbn_classification(id="NHMSYS0000376773")

# get id first, then pass to this fxn
id <- get_nbnid("Zootoca vivipara", rec_only = TRUE, rank = "Species")
nbn_classification(id)

nbn_classification(id="NHMSYS0000502940", verbose = TRUE)
} # }
```
