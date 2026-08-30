# Retrieve all taxa names downstream in hierarchy for NCBI

Retrieve all taxa names downstream in hierarchy for NCBI

## Usage

``` r
ncbi_downstream(id, downto, intermediate = FALSE, ...)
```

## Arguments

- id:

  (numeric/integer) An NCBI taxonomic identifier

- downto:

  The taxonomic level you want to go down to. See examples below. The
  taxonomic level IS case sensitive, and you do have to spell it
  correctly. See `data(rank_ref)` for spelling.

- intermediate:

  (logical) If `TRUE`, return a list of length two with target taxon
  rank names, with additional list of data.frame's of intermediate
  taxonomic groups. Default: `FALSE`

- ...:

  Further args passed on to
  [`ncbi_children()`](https://docs.ropensci.org/taxize/reference/ncbi_children.md)

## Value

Data.frame of taxonomic information downstream to family from e.g.,
Order, Class, etc., or if `intermediate=TRUE`, list of length two, with
target taxon rank names, and intermediate names.

## No Rank

A sticky point with NCBI is that they can have designation for taxonomic
rank of "No Rank". So we have no way of programatically knowing what to
do with that taxon. Of course one can manually look at a name and
perhaps know what it is, or look it up on the web - but we can't do
anything programatically. So, no rank things will sometimes be missing.

## Authentication

See
[`taxize-authentication()`](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication. We strongly recommend getting an API key

## Author

Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
## genus Apis
ncbi_downstream(id = 7459, downto="species")

## get intermediate taxa as a separate object
ncbi_downstream(id = 7459, downto="species", intermediate = TRUE)

## Lepidoptera
ncbi_downstream(id = 7088, downto="superfamily")

## families in the ferns (Moniliformopses)
(id <- get_uid("Moniliformopses"))
ncbi_downstream(id = id, downto = "order")
} # }
```
