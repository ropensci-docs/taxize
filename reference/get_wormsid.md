# Get Worms ID for a taxon name

Retrieve Worms ID of a taxon from World Register of Marine Species
(WORMS).

## Usage

``` r
get_wormsid(
  sci_com,
  searchtype = "scientific",
  marine_only = TRUE,
  fuzzy = NULL,
  accepted = FALSE,
  ask = TRUE,
  messages = TRUE,
  rows = NA,
  query = NULL,
  ...
)

as.wormsid(x, check = TRUE)

# S3 method for class 'wormsid'
as.wormsid(x, check = TRUE)

# S3 method for class 'character'
as.wormsid(x, check = TRUE)

# S3 method for class 'list'
as.wormsid(x, check = TRUE)

# S3 method for class 'numeric'
as.wormsid(x, check = TRUE)

# S3 method for class 'data.frame'
as.wormsid(x, check = TRUE)

# S3 method for class 'wormsid'
as.data.frame(x, ...)

get_wormsid_(
  sci_com,
  messages = TRUE,
  searchtype = "scientific",
  marine_only = TRUE,
  fuzzy = NULL,
  accepted = TRUE,
  rows = NA,
  query = NULL,
  ...
)
```

## Arguments

- sci_com:

  character; A vector of common or scientific names. Or, a `taxon_state`
  object (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- searchtype:

  character; One of 'scientific' or 'common', or any unique abbreviation

- marine_only:

  logical; marine only? default: `TRUE` (only used when
  `searchtype="scientific"`); passed on to
  [`worrms::wm_records_name()`](https://docs.ropensci.org/worrms/reference/wm_records_name.html)

- fuzzy:

  logical; fuzzy search. default: `NULL` (`TRUE` for
  `searchtype="scientific"` and `FALSE` for `searchtype="common"` to
  match the default values for those parameters in worrms package);
  passed on to
  [`worrms::wm_records_name()`](https://docs.ropensci.org/worrms/reference/wm_records_name.html)
  or
  [`worrms::wm_records_common()`](https://docs.ropensci.org/worrms/reference/wm_records_common.html)

- accepted:

  logical; If TRUE, removes names that are not accepted valid names by
  WORMS. Set to `FALSE` (default) to give back both accepted and
  unaccepted names.

- ask:

  logical; should get_wormsid be run in interactive mode? If `TRUE` and
  more than one wormsid is found for the species, the user is asked for
  input. If `FALSE` NA is returned for multiple matches.

- messages:

  logical; should progress be printed?

- rows:

  numeric; Any number from 1 to infinity. If the default NaN, all rows
  are considered. Note that this function still only gives back a
  wormsid class object with one to many identifiers. See
  `get_wormsid_()` to get back all, or a subset, of the raw data that
  you are presented during the ask process.

- query:

  Deprecated, see `sci_com`

- ...:

  Ignored

- x:

  Input to `as.wormsid`

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.wormsid()`

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

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

Other taxonomic-ids:
[`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md),
[`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
[`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
[`get_ids()`](https://docs.ropensci.org/taxize/reference/get_ids.md),
[`get_iucn()`](https://docs.ropensci.org/taxize/reference/get_iucn.md),
[`get_natservid()`](https://docs.ropensci.org/taxize/reference/get_natservid.md),
[`get_nbnid()`](https://docs.ropensci.org/taxize/reference/get_nbnid.md),
[`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md),
[`get_tolid()`](https://docs.ropensci.org/taxize/reference/get_tolid.md),
[`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
[`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
[`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md)

## Examples

``` r
if (FALSE) { # \dontrun{
(x <- get_wormsid('Gadus morhua'))
attributes(x)
attr(x, "match")
attr(x, "multiple_matches")
attr(x, "pattern_match")
attr(x, "uri")

get_wormsid('Pomatomus saltatrix')
get_wormsid(c("Gadus morhua", "Lichenopora neapolitana"))

# marine_only
get_wormsid("Apedinella", marine_only=TRUE)
get_wormsid("Apedinella", marine_only=FALSE)

# fuzzy
## searchtype="scientific": fuzzy is TRUE by default
get_wormsid("Platypro", searchtype="scientific", fuzzy=TRUE)
get_wormsid("Platypro", searchtype="scientific", fuzzy=FALSE)
## searchtype="common": fuzzy is FALSE by default
get_wormsid("clam", searchtype="common", fuzzy=FALSE)
get_wormsid("clam", searchtype="common", fuzzy=TRUE)

# by common name
get_wormsid("dolphin", 'common')
get_wormsid("clam", 'common')

# specify rows to limit choices available
get_wormsid('Plat')
get_wormsid('Plat', rows=1)
get_wormsid('Plat', rows=1:2)

# When not found
get_wormsid("howdy")
get_wormsid(c('Gadus morhua', "howdy"))

# Convert a wormsid without class information to a wormsid class
# already a wormsid, returns the same
as.wormsid(get_wormsid('Gadus morhua'))
# same
as.wormsid(get_wormsid(c('Gadus morhua', 'Pomatomus saltatrix')))
# numeric
as.wormsid(126436)
# numeric vector, length > 1
as.wormsid(c(126436,151482))
# character
as.wormsid("126436")
# character vector, length > 1
as.wormsid(c("126436","151482"))
# list, either numeric or character
as.wormsid(list("126436","151482"))
## dont check, much faster
as.wormsid("126436", check=FALSE)
as.wormsid(126436, check=FALSE)
as.wormsid(c("126436","151482"), check=FALSE)
as.wormsid(list("126436","151482"), check=FALSE)

(out <- as.wormsid(c(126436,151482)))
data.frame(out)
as.wormsid( data.frame(out) )

# Get all data back
get_wormsid_("Plat")
get_wormsid_("Plat", rows=1)
get_wormsid_("Plat", rows=1:2)
get_wormsid_("Plat", rows=1:75)
} # }
```
