# Retrieve the downstream taxa for a given taxon name or ID.

This function uses a while loop to continually collect children taxa
down to the taxonomic rank that you specify in the `downto` parameter.
You can get data from ITIS (itis), GBIF (gbif), NCBI (ncbi), WORMS
(worms), or BOLD (bold). There is no method exposed by these four
services for getting taxa at a specific taxonomic rank, so we do it
ourselves here.

## Usage

``` r
downstream(...)

# Default S3 method
downstream(
  sci_id,
  db = NULL,
  downto = NULL,
  intermediate = FALSE,
  rows = NA,
  x = NULL,
  ...
)

# S3 method for class 'tsn'
downstream(sci_id, db = NULL, downto = NULL, intermediate = FALSE, ...)

# S3 method for class 'gbifid'
downstream(
  sci_id,
  db = NULL,
  downto = NULL,
  intermediate = FALSE,
  limit = 100,
  start = NULL,
  ...
)

# S3 method for class 'uid'
downstream(sci_id, db = NULL, downto = NULL, intermediate = FALSE, ...)

# S3 method for class 'wormsid'
downstream(sci_id, db = NULL, downto = NULL, intermediate = FALSE, ...)

# S3 method for class 'boldid'
downstream(sci_id, db = NULL, downto = NULL, intermediate = FALSE, ...)

# S3 method for class 'ids'
downstream(sci_id, db = NULL, downto = NULL, intermediate = FALSE, ...)
```

## Arguments

- ...:

  Further args passed on to
  [`itis_downstream()`](https://docs.ropensci.org/taxize/reference/itis_downstream.md),
  [`gbif_downstream()`](https://docs.ropensci.org/taxize/reference/gbif_downstream.md),
  [`ncbi_downstream()`](https://docs.ropensci.org/taxize/reference/ncbi_downstream.md),
  [`worms_downstream()`](https://docs.ropensci.org/taxize/reference/worms_downstream.md),
  or
  [`bold_downstream()`](https://docs.ropensci.org/taxize/reference/bold_downstream.md)

- sci_id:

  Vector of taxa names (character) or IDs (character or numeric) to
  query.

- db:

  character; database to query. One or more of `itis`, `gbif`, `ncbi`,
  `worms`, or `bold`. Note that each taxonomic data source has their own
  identifiers, so that if you provide the wrong `db` value for the
  identifier you could get a result, but it will likely be wrong (not
  what you were expecting). If using ncbi, we recommend getting an API
  key; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- downto:

  What taxonomic rank to go down to. One of: 'superkingdom', 'kingdom',
  'subkingdom','infrakingdom','phylum','division','subphylum',
  'subdivision','infradivision',
  'superclass','class','subclass','infraclass',
  'superorder','order','suborder','infraorder','superfamily','family',
  'subfamily','tribe','subtribe','genus','subgenus','section','subsection',
  'species
  group','species','subspecies','variety','form','subvariety','race',
  'stirp', 'morph','aberration','subform', 'unspecified', 'no rank'

- intermediate:

  (logical) If `TRUE`, return a list of length two with target taxon
  rank names, with additional list of data.frame's of intermediate
  taxonomic groups. Default: `FALSE`

- rows:

  (numeric) Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this parameter is ignored if you pass in a
  taxonomic id of any of the acceptable classes: tsn.

- x:

  Deprecated, see `sci_id`

- limit:

  Number of records to return. Applies to gbif only. default: 100.
  max: 1000. use in combination with the `start` parameter

- start:

  Record number to start at. Applies to gbif only. default: 0. use in
  combination with the `limit` parameter

## Value

A named list of data.frames with the downstream names of every supplied
taxa. You get an NA if there was no match in the database.

## Authentication

See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication

## bold

BEWARE: `db="bold"` scrapes the BOLD website, so may be unstable. That
is, one day it may work, and the next it may fail. Open an issue if you
encounter an error: https://github.com/ropensci/taxize/issues

## Examples

``` r
if (FALSE) { # \dontrun{
# Plug in taxon IDs
downstream(125732, db = 'worms', downto = 'species')
downstream(3451, db = 'bold', downto = 'species')

if (interactive()) {

# Plug in taxon names
downstream("Apis", db = 'ncbi', downto = 'species')
downstream("Apis", db = 'itis', downto = 'species')
downstream("Apis", db = 'bold', downto = 'species')
downstream("Gadus", db = 'worms', downto = 'species')
downstream(c("Apis","Epeoloides"), db = 'itis', downto = 'species')
downstream("Ursus", db = 'gbif', downto = 'species')
downstream(get_gbifid("Ursus"), db = 'gbif', downto = 'species')

# Many taxa
sp <- names_list("genus", 3)
downstream(sp, db = 'itis', downto = 'species')
downstream(sp, db = 'gbif', downto = 'species')

# Both data sources
ids <- get_ids("Apis", db = c('gbif','itis'))
downstream(ids, downto = 'species')
## same result
downstream(get_ids("Apis", db = c('gbif','itis')), downto = 'species')

# Collect intermediate names
## itis
downstream('Bangiophyceae', db="itis", downto="genus")
downstream('Bangiophyceae', db="itis", downto="genus", intermediate=TRUE)
downstream(get_tsn('Bangiophyceae'), downto="genus")
downstream(get_tsn('Bangiophyceae'), downto="genus", intermediate=TRUE)

# Use the rows parameter
## note how in the second function call you don't get the prompt
downstream("Poa", db = 'gbif', downto="species")
downstream("Poa", db = 'gbif', downto="species", rows=1)

# use curl options
res <- downstream("Apis", db = 'gbif', downto = 'species', verbose = TRUE)

# Pagination
# GBIF limits queries to a maximum of 1000 records per request, so if
# there's more than 1000, use the start parameter
# Piper, taxonKey = 3075433
z1 <- downstream(3075433, db = 'gbif', downto = "species", limit=1000)
z2 <- downstream(3075433, db = 'gbif', downto = "species", limit=1000,
  start=1000)
z3 <- downstream(3075433, db = 'gbif', downto = "species", limit=1000,
  start=2000)
z4 <- downstream(3075433, db = 'gbif', downto = "species", limit=1000,
  start=3000)
NROW(rbind(z1[[1]], z2[[1]], z3[[1]], z4[[1]]))
}} # }
```
