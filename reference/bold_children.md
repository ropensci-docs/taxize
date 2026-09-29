# Barcode of Life taxonomic children

BEWARE: this function scrapes data from the BOLD website, so may be
unstable. That is, one day it may work, and the next it may fail. Open
an issue if you encounter an error:
https://github.com/ropensci/taxize/issues

## Usage

``` r
bold_children(id, ...)
```

## Arguments

- id:

  (integer) A BOLD taxonomic identifier. length=1. required

- ...:

  named curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  debugging

## Value

list of data.frame's

## Examples

``` r
if (FALSE) { # \dontrun{
# Osmia (genus): 253 children
bold_children(id = 4940)
# Momotus (genus): 3 children
bold_children(id = 88899)
# Momotus aequatorialis (species): no children
bold_children(id = 115130)
# Osmia sp1 (species): no children
bold_children(id = 293378)
# Arthropoda (phylum): 27 children
bold_children(id = 82)
# Psocodea (order): 51 children
bold_children(id = 737139)
# Megachilinae (subfamily): 2 groups (tribes: 3, genera: 60)
bold_children(id = 4962)
# Stelis (species): 78 taxa
bold_children(id = 4952)
} # }
```
