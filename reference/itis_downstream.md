# Retrieve all taxa names or TSNs downstream in hierarchy from given TSN.

Retrieve all taxa names or TSNs downstream in hierarchy from given TSN.

## Usage

``` r
itis_downstream(id, downto, intermediate = FALSE, tsns = NULL, ...)
```

## Arguments

- id:

  A taxonomic serial number.

- downto:

  The taxonomic level you want to go down to. See examples below. The
  taxonomic level IS case sensitive, and you do have to spell it
  correctly. See `data(rank_ref)` for spelling.

- intermediate:

  (logical) If TRUE, return a list of length two with target taxon rank
  names, with additional list of data.frame's of intermediate taxonomic
  groups. Default: FALSE

- tsns:

  Deprecated, see `id`

- ...:

  Further args passed on to
  [`ritis::rank_name()`](https://docs.ropensci.org/ritis/reference/rank_name.html)
  and
  [`ritis::hierarchy_down()`](https://docs.ropensci.org/ritis/reference/hierarchy.html)

## Value

Data.frame of taxonomic information downstream to family from e.g.,
Order, Class, etc., or if `intermediated=TRUE`, list of length two, with
target taxon rank names, and intermediate names.

## Examples

``` r
if (FALSE) { # \dontrun{
## the plant class Bangiophyceae, tsn 846509
itis_downstream(id = 846509, downto="genus")
itis_downstream(id = 846509, downto="genus", intermediate=TRUE)

# get families downstream from Acridoidea
itis_downstream(id = 650497, "family")
## here, intermediate leads to the same result as the target
itis_downstream(id = 650497, "family", intermediate=TRUE)

# get species downstream from Ursus
itis_downstream(id = 180541, "species")

# get orders down from the Division Rhodophyta (red algae)
itis_downstream(id = 660046, "order")
itis_downstream(id = 660046, "order", intermediate=TRUE)

# get tribes down from the family Apidae
itis_downstream(id = 154394, downto="tribe")
itis_downstream(id = 154394, downto="tribe", intermediate=TRUE)
} # }
```
