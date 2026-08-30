# Retrieve all taxa names downstream in hierarchy for BOLD

Retrieve all taxa names downstream in hierarchy for BOLD

## Usage

``` r
bold_downstream(id, downto, intermediate = FALSE, ...)
```

## Arguments

- id:

  (integer) One or more BOLD taxonomic identifiers

- downto:

  (character) The taxonomic level you want to go down to. See examples
  below. The taxonomic level IS case sensitive, and you do have to spell
  it correctly. See `data(rank_ref)` for spelling.

- intermediate:

  (logical) If `TRUE`, return a list of length two with target taxon
  rank names, with additional list of data.frame's of intermediate
  taxonomic groups. Default: `FALSE`

- ...:

  crul options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

data.frame of taxonomic information downstream to family from e.g.,
Order, Class, etc., or if `intermediated=TRUE`, list of length two, with
target taxon rank names, and intermediate names.

## Details

BEWARE: This function scrapes the BOLD website, so may be unstable. That
is, one day it may work, and the next it may fail. Open an issue if you
encounter an error: https://github.com/ropensci/taxize/issues

## Examples

``` r
if (FALSE) { # \dontrun{
## the genus Gadus
bold_downstream(id = 3451, downto="species")

bold_downstream(id = 443, downto="genus")
bold_downstream(id = 443, downto="genus", intermediate=TRUE)
} # }
```
