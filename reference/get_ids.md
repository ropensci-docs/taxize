# Retrieve taxonomic identifiers for a given taxon name.

This is a convenience function to get identifiers across all data
sources. You can use other `get_*` functions to get identifiers from
specific sources if you like.

## Usage

``` r
get_ids(
  sci_com,
  db = c("itis", "ncbi", "eol", "tropicos", "gbif", "nbn", "pow"),
  suppress = FALSE,
  names = NULL,
  ...
)

get_ids_(
  sci_com,
  db = get_ids_dbs,
  rows = NA,
  suppress = FALSE,
  names = NULL,
  ...
)
```

## Arguments

- sci_com:

  (character) Taxonomic name to query.

- db:

  (character) database to query. One or more of `ncbi`, `itis`, `eol`,
  `tropicos`, `gbif`, `nbn`, or `pow`. By default db is set to search
  all data sources. Note that each taxonomic data source has their own
  identifiers, so that if you give the wrong `db` value for the
  identifier you could get a result, it will likely be wrong (not what
  you were expecting). If using ncbi and/or tropicos we recommend
  getting API keys; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- suppress:

  (logical) suppress cli separators with the database name being
  queried. default: `FALSE`

- names:

  Deprecated, see `sci_com`

- ...:

  Other arguments passed to
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
  [`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
  [`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
  [`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
  [`get_nbnid()`](https://docs.ropensci.org/taxize/reference/get_nbnid.md).

- rows:

  (numeric) Any number from 1 to infinity. If the default NA, all rows
  are returned. When used in `get_ids` this function still only gives
  back a ids class object with one to many identifiers. See `get_ids_`
  to get back all, or a subset, of the raw data that you are presented
  during the ask process.

## Value

A vector of taxonomic identifiers, each retaining their respective S3
classes so that each element can be passed on to another function (see
e.g.'s).

## Note

There is a timeout of 1/3 seconds between queries to NCBI.

## Authentication

See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

Other taxonomic-ids:
[`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md),
[`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
[`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
[`get_iucn()`](https://docs.ropensci.org/taxize/reference/get_iucn.md),
[`get_natservid()`](https://docs.ropensci.org/taxize/reference/get_natservid.md),
[`get_nbnid()`](https://docs.ropensci.org/taxize/reference/get_nbnid.md),
[`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md),
[`get_tolid()`](https://docs.ropensci.org/taxize/reference/get_tolid.md),
[`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
[`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
[`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Plug in taxon names directly
# specify rows to limit choices available
get_ids("Poa annua", db="eol", rows=1)
get_ids("Poa annua", db="eol", rows=1:2)

## Or you can specify which source you want via the db parameter
get_ids("Chironomus riparius", db = 'ncbi')
get_ids("Salvelinus fontinalis", db = 'nbn')

get_ids(c("Chironomus riparius", "Pinus contorta"), db = 'ncbi')
get_ids("Pinus contorta", db = c('ncbi','eol','tropicos'))
get_ids("ava avvva", db = c('ncbi','eol','tropicos'))

# Pass on to other functions
out <- get_ids("Pinus contorta", db = c('ncbi','eol','tropicos'))
classification(out$ncbi)

# Get all data back
get_ids_(c("Chironomus riparius", "Pinus contorta"), db = 'nbn',
  rows=1:10)
get_ids_(c("Chironomus riparius", "Pinus contorta"), db = c('nbn','gbif'),
  rows=1:10)

# use curl options
get_ids("Agapostemon", db = "ncbi", verbose = TRUE)
} # }
```
