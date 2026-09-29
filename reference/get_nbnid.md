# Get the UK National Biodiversity Network ID from taxonomic names.

Get the UK National Biodiversity Network ID from taxonomic names.

## Usage

``` r
get_nbnid(
  sci_com,
  ask = TRUE,
  messages = TRUE,
  rec_only = FALSE,
  rank = NULL,
  rows = NA,
  name = NULL,
  ...
)

as.nbnid(x, check = TRUE)

# S3 method for class 'nbnid'
as.nbnid(x, check = TRUE)

# S3 method for class 'character'
as.nbnid(x, check = TRUE)

# S3 method for class 'list'
as.nbnid(x, check = TRUE)

# S3 method for class 'data.frame'
as.nbnid(x, check = TRUE)

# S3 method for class 'nbnid'
as.data.frame(x, ...)

get_nbnid_(
  sci_com,
  messages = TRUE,
  rec_only = FALSE,
  rank = NULL,
  rows = NA,
  name = NULL,
  ...
)
```

## Arguments

- sci_com:

  character; a vector of common or scientific names. Or, a `taxon_state`
  object (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- ask:

  logical; should get_nbnid be run in interactive mode? If TRUE and more
  than one ID is found for the species, the user is asked for input. If
  FALSE NA is returned for multiple matches.

- messages:

  logical; If TRUE the actual taxon queried is printed on the console.

- rec_only:

  (logical) If `TRUE` ids of recommended names are returned (i.e.
  synonyms are removed). Defaults to `FALSE`. Remember, the id of a
  synonym is a taxa with 'recommended' name status.

- rank:

  (character) If given, we attempt to limit the results to those taxa
  with the matching rank.

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a nbnid
  class object with one to many identifiers. See `get_nbnid_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- name:

  Deprecated, see `sci_com`

- ...:

  Further args passed on to `nbn_search`

- x:

  Input to `as.nbnid()`

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.nbnid()`

## Value

A vector of taxonomic identifiers as an S3 class. If a taxon is not
found an `NA` is given. If more than one identifier is found the
function asks for user input if `ask = TRUE`, otherwise returns `NA`. If
`ask=FALSE` and `rows` does not equal `NA`, then a data.frame is given
back, but not of the uid class, which you can't pass on to other
functions as you normally can.

See
[`get_id_details`](https://docs.ropensci.org/taxize/reference/get_id_details.md)
for further details including attributes and exceptions

an object of class nbnid, a light wrapper around a character string that
is the taxonomic ID - includes attributes with relavant metadata

## References

https://api.nbnatlas.org/

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

Other taxonomic-ids:
[`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md),
[`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
[`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
[`get_ids()`](https://docs.ropensci.org/taxize/reference/get_ids.md),
[`get_iucn()`](https://docs.ropensci.org/taxize/reference/get_iucn.md),
[`get_natservid()`](https://docs.ropensci.org/taxize/reference/get_natservid.md),
[`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md),
[`get_tolid()`](https://docs.ropensci.org/taxize/reference/get_tolid.md),
[`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
[`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
[`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

Other nbn:
[`nbn_classification()`](https://docs.ropensci.org/taxize/reference/nbn_classification.md),
[`nbn_search()`](https://docs.ropensci.org/taxize/reference/nbn_search.md),
[`nbn_synonyms()`](https://docs.ropensci.org/taxize/reference/nbn_synonyms.md)

## Author

Scott Chamberlain,

## Examples

``` r
if (FALSE) { # \dontrun{
get_nbnid(sci_com='Poa annua')
get_nbnid(sci_com='Poa annua', rec_only=TRUE)
get_nbnid(sci_com='Poa annua', rank='Species')
get_nbnid(sci_com='Poa annua', rec_only=TRUE, rank='Species')
get_nbnid(sci_com='Pinus contorta')

# The NBN service handles common names too
get_nbnid(sci_com='red-winged blackbird')

# specify rows to limit choices available
get_nbnid('Poa ann')
get_nbnid('Poa ann', rows=1)
get_nbnid('Poa ann', rows=25)
get_nbnid('Poa ann', rows=1:2)

# When not found
get_nbnid(sci_com="uaudnadndj")
get_nbnid(c("Zootoca vivipara", "uaudnadndj"))
get_nbnid(c("Zootoca vivipara","Chironomus riparius", "uaudnadndj"))

# Convert an nbnid without class information to a nbnid class
as.nbnid(get_nbnid("Zootoca vivipara")) # already a nbnid, returns the same
as.nbnid(get_nbnid(c("Zootoca vivipara","Pinus contorta"))) # same
as.nbnid('NHMSYS0001706186') # character
# character vector, length > 1
as.nbnid(c("NHMSYS0001706186","NHMSYS0000494848","NBNSYS0000010867"))
# list
as.nbnid(list("NHMSYS0001706186","NHMSYS0000494848","NBNSYS0000010867"))
## dont check, much faster
as.nbnid('NHMSYS0001706186', check=FALSE)
as.nbnid(list("NHMSYS0001706186","NHMSYS0000494848","NBNSYS0000010867"),
  check=FALSE)

(out <- as.nbnid(c("NHMSYS0001706186","NHMSYS0000494848",
  "NBNSYS0000010867")))
data.frame(out)
as.nbnid( data.frame(out) )

# Get all data back
get_nbnid_("Zootoca vivipara")
get_nbnid_("Poa annua", rows=2)
get_nbnid_("Poa annua", rows=1:2)
get_nbnid_(c("asdfadfasd","Pinus contorta"), rows=1:5)

# use curl options
invisible(get_nbnid("Quercus douglasii", verbose = TRUE))
} # }
```
