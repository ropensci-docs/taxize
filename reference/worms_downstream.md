# Retrieve all taxa names downstream in hierarchy for WORMS

Retrieve all taxa names downstream in hierarchy for WORMS

## Usage

``` r
worms_downstream(id, downto, intermediate = FALSE, start = 1, ...)
```

## Arguments

- id:

  (integer) One or more AphiaID's

- downto:

  (character) The taxonomic level you want to go down to. See examples
  below. The taxonomic level IS case sensitive, and you do have to spell
  it correctly. See
  [rank_ref_zoo](https://docs.ropensci.org/taxize/reference/rank_ref_zoo.md)
  for spelling.

- intermediate:

  (logical) If `TRUE`, return a list of length two with target taxon
  rank names, with additional list of data.frame's of intermediate
  taxonomic groups. Default: `FALSE`

- start:

  (integer) Record number to start at

- ...:

  crul options passed on to
  [`worrms::wm_children()`](https://docs.ropensci.org/worrms/reference/wm_children.html),
  including the parameters `marine_only` and `offset`, see
  [`?worrms::wm_children`](https://docs.ropensci.org/worrms/reference/wm_children.html)
  for details

## Value

data.frame of taxonomic information downstream to family from e.g.,
Order, Class, etc., or if `intermediated=TRUE`, list of length two, with
target taxon rank names, and intermediate names.

## Examples

``` r
if (FALSE) { # \dontrun{
## the genus Gadus
worms_downstream(id = 125732, downto="species")
worms_downstream(id = 125732, downto="species", intermediate=TRUE)

worms_downstream(id = 51, downto="class")
worms_downstream(id = 51, downto="subclass", intermediate=TRUE)

worms_downstream(id = 105, downto="subclass")

# marine_only parameter
worms_downstream(545470, downto = "species")
worms_downstream(545470, downto = "species", marine_only = FALSE)
} # }
```
