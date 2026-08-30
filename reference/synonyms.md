# Retrieve synonyms from various sources given input taxonomic names or identifiers

Retrieve synonyms from various sources given input taxonomic names or
identifiers

## Usage

``` r
synonyms(...)

# Default S3 method
synonyms(sci_id, db = NULL, rows = NA, x = NULL, ...)

# S3 method for class 'tsn'
synonyms(id, ...)

# S3 method for class 'tpsid'
synonyms(id, ...)

# S3 method for class 'nbnid'
synonyms(id, ...)

# S3 method for class 'wormsid'
synonyms(id, ...)

# S3 method for class 'iucn'
synonyms(id, ...)

# S3 method for class 'pow'
synonyms(id, ...)

# S3 method for class 'ids'
synonyms(id, ...)

synonyms_df(x)
```

## Arguments

- ...:

  Other passed arguments to internal functions `get_*()` and functions
  to gather synonyms.

- sci_id:

  Vector of taxa names (character) or IDs (character or numeric)

- db:

  character; database to query. either `itis`, `tropicos`, `nbn`,
  `worms`, or `pow`. Note that each taxonomic data source has their own
  identifiers, so that if you provide the wrong `db` value for the
  identifier you could get a result, but it will likely be wrong (not
  what you were expecting). If using tropicos, we recommend getting an
  API key; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- rows:

  (numeric) Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this parameter is ignored if you pass in a
  taxonomic id of any of the acceptable classes: tsn, tpsid, nbnid, ids.

- x:

  For `synonyms()`: deprecated, see `sci_id`. For `synonyms_df()`, the
  output of `synonyms()`

- id:

  character; identifiers, returned by
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
  [`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
  [`get_nbnid()`](https://docs.ropensci.org/taxize/reference/get_nbnid.md),
  [`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md),
  [`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md)

## Value

A named list of results with three types of output in each slot:

- if the name was not found: `NA_character_`

- if the name was found but no synonyms found, an empty data.frame (0
  rows)

- if the name was found, and synonyms found, a data.frames with the
  synonyms - the column names vary by data source

## Details

If IDs are supplied directly (not from the `get_*()` functions) you must
specify the type of ID.

For `db = "itis"` you can pass in a parameter `accepted` to toggle
whether only accepted names are used `accepted = TRUE`, or if all are
used `accepted = FALSE`. The default is `accepted = FALSE`

Note that IUCN requires an API key. See
[rredlist::rredlist-package](https://docs.ropensci.org/rredlist/reference/rredlist-package.html)
for help on authentiating with IUCN Redlist

## See also

[`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md)
[`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md)
[`get_nbnid()`](https://docs.ropensci.org/taxize/reference/get_nbnid.md)
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)
[`get_iucn()`](https://docs.ropensci.org/taxize/reference/get_iucn.md)
[`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Plug in taxon IDs
synonyms(526852, db="itis")
synonyms(183327, db="itis") # ID with no synonyms
synonyms("25509881", db="tropicos")
synonyms("NBNSYS0000004629", db='nbn')
synonyms(105706, db='worms')
synonyms(12392, db='iucn')
synonyms('urn:lsid:ipni.org:names:358881-1', db='pow')

# Plug in taxon names directly
synonyms("Pinus contorta", db="itis")
synonyms("Puma concolor", db="itis")
synonyms(c("Poa annua",'Pinus contorta','Puma concolor'), db="itis")
synonyms("Poa annua", db="tropicos")
synonyms("Pinus contorta", db="tropicos")
synonyms(c("Poa annua",'Pinus contorta'), db="tropicos")
synonyms("Pinus sylvestris", db='nbn')
synonyms('Pomatomus', db='worms')
synonyms('Pomatomus saltatrix', db='worms')
synonyms('Lithocarpus mindanaensis', db='pow')
synonyms('Poa annua', db='pow')
synonyms(c('Poa annua', 'Pinus contorta', 'foo bar'), db='pow')

# not accepted names, with ITIS
## looks for whether the name given is an accepted name,
## and if not, uses the accepted name to look for synonyms
synonyms("Acer drummondii", db="itis")
synonyms("Spinus pinus", db="itis")

# Use get_* methods
synonyms(get_tsn("Poa annua"))
synonyms(get_tpsid("Poa annua"))
synonyms(get_nbnid("Carcharodon carcharias"))
synonyms(get_iucn('Loxodonta africana'))
synonyms(get_pow('Lithocarpus mindanaensis'))

# Pass many ids from class "ids"
out <- get_ids(names="Poa annua", db = c('itis','tropicos'))
synonyms(out)

# Use the rows parameter to select certain rows
synonyms("Poa annua", db='tropicos', rows=1)
synonyms("Poa annua", db='tropicos', rows=1:3)
synonyms("Pinus sylvestris", db='nbn', rows=1:3)

# Use curl options
synonyms("Poa annua", db='tropicos', rows=1, verbose = TRUE)
synonyms("Poa annua", db='itis', rows=1, verbose = TRUE)


# combine many outputs together
x <- synonyms(c("Osmia bicornis", "Osmia rufa", "Osmia"), db = "itis")
synonyms_df(x)

## note here how Pinus contorta is dropped due to no synonyms found
synonyms_df(x)

## note here that ids are taxon identifiers b/c you start with them
x <- synonyms(c(25509881, 13100094), db="tropicos")
synonyms_df(x)

## NBN
x <- synonyms(c('Aglais io', 'Usnea hirta', 'Arctostaphylos uva-ursi'),
  db="nbn")
synonyms_df(x)
} # }
```
