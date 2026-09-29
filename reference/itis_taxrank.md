# Retrieve taxonomic rank name from given TSN.

Retrieve taxonomic rank name from given TSN.

## Usage

``` r
itis_taxrank(query = NULL, ...)
```

## Arguments

- query:

  TSN for a taxonomic group (numeric). If query is left as default
  (NULL), you get all possible rank names, and their TSN's (using
  function
  [`ritis::rank_names()`](https://docs.ropensci.org/ritis/reference/rank_names.html).
  There is slightly different terminology for Monera vs. Plantae vs.
  Fungi vs. Animalia vs. Chromista, so there are separate terminologies
  for each group.

- ...:

  Further arguments passed on to
  [`ritis::rank_name()`](https://docs.ropensci.org/ritis/reference/rank_name.html)

## Value

Taxonomic rank names or data.frame of all ranks.

## Details

You can print messages by setting `verbose=FALSE`.

## Examples

``` r
if (FALSE) { # \dontrun{
# All ranks
itis_taxrank()

# A single TSN
itis_taxrank(query=202385)

# Many TSN's
itis_taxrank(query=c(202385,183833,180543))
} # }
```
