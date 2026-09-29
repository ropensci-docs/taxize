# Parse taxon names using the GBIF name parser.

Parse taxon names using the GBIF name parser.

## Usage

``` r
gbif_parse(scientificname, ...)
```

## Arguments

- scientificname:

  (character) scientific names

- ...:

  Further args passed on to
  [crul::verb-POST](https://docs.ropensci.org/crul/reference/verb-POST.html)

## Value

A `data.frame` containing fields extracted from parsed taxon names.
Fields returned are the union of fields extracted from all species names
in `scientificname`.

## References

https://www.gbif.org/tools/name-parser/about

## See also

[`gni_parse()`](https://docs.ropensci.org/taxize/reference/gni_parse.md),
[`gna_parse()`](https://docs.ropensci.org/taxize/reference/gna_parse.md)

## Author

John Baumgartner <johnbb@student.unimelb.edu.au>

## Examples

``` r
if (FALSE) { # \dontrun{
gbif_parse(scientificname='x Agropogon littoralis')
gbif_parse(c('Arrhenatherum elatius var. elatius',
             'Secale cereale subsp. cereale', 'Secale cereale ssp. cereale',
             'Vanessa atalanta (Linnaeus, 1758)'))
} # }
```
