# Retrieve all taxonomic names downstream in hierarchy for GBIF

Retrieve all taxonomic names downstream in hierarchy for GBIF

## Usage

``` r
gbif_downstream(
  id,
  downto,
  intermediate = FALSE,
  limit = 100,
  start = NULL,
  key = NULL,
  ...
)
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

- limit:

  Number of records to return. default: 100. max: 1000. use in
  combination with the `start` parameter

- start:

  Record number to start at. default: 0. use in combination with the
  `limit` parameter

- key:

  Deprecated, see `id`

- ...:

  Further args passed on to
  [`gbif_name_usage()`](https://docs.ropensci.org/taxize/reference/gbif_name_usage.md)

## Value

data.frame of taxonomic information downstream to family from e.g.,
Order, Class, etc., or if `intermediated=TRUE`, list of length two, with
target taxon rank names, and intermediate names.

## Details

Sometimes records don't have a `canonicalName` entry which is what we
look for. In that case we grab the `scientificName` entry. You can see
the type of name colleceted in the column `name_type`

## Author

Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
## the plant class Bangiophyceae
gbif_downstream(id = 198, downto="genus")
gbif_downstream(id = 198, downto="genus", intermediate=TRUE)

# families downstream from the family Strepsiptera (twisted wing parasites)
gbif_downstream(id = 1227, "family")
## here, intermediate leads to the same result as the target
gbif_downstream(id = 1227, "family", intermediate=TRUE)

if (interactive()) {
# Lepidoptera
gbif_downstream(id = 797, "family")

# get species downstream from the genus Ursus
gbif_downstream(id = 2433406, "species")

# get tribes down from the family Apidae
gbif_downstream(id = 7799978, downto="species")
gbif_downstream(id = 7799978, downto="species", intermediate=TRUE)

# names that don't have canonicalname entries for some results
# Myosotis: key 2925668
key <- 2925668
res <- gbif_downstream(key, downto = "species")
res2 <- downstream(key, db = "gbif", downto = "species")

# Pagination
# GBIF limits queries to a maximum of 1000 records per request, so if
# there's more than 1000, use the start parameter
# Piper, taxonKey = 3075433
x1 <- gbif_downstream(id = 3075433, downto = "species", limit=1000)
x2 <- gbif_downstream(id = 3075433, downto = "species", limit=1000,
  start=1000)
x3 <- gbif_downstream(id = 3075433, downto = "species", limit=1000,
  start=2000)
x4 <- gbif_downstream(id = 3075433, downto = "species", limit=1000,
  start=3000)
rbind(x1, x2, x3, x4)
}
} # }
```
