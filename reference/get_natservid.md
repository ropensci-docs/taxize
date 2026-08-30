# Get NatureServe taxonomic ID for a taxon name

Get NatureServe taxonomic ID for a taxon name

## Usage

``` r
get_natservid(
  sci_com,
  searchtype = "scientific",
  ask = TRUE,
  messages = TRUE,
  rows = NA,
  query = NULL,
  ...
)

as.natservid(x, check = TRUE)

# S3 method for class 'natservid'
as.natservid(x, check = TRUE)

# S3 method for class 'character'
as.natservid(x, check = TRUE)

# S3 method for class 'list'
as.natservid(x, check = TRUE)

# S3 method for class 'numeric'
as.natservid(x, check = TRUE)

# S3 method for class 'data.frame'
as.natservid(x, check = TRUE)

# S3 method for class 'natservid'
as.data.frame(x, ...)

get_natservid_(
  sci_com,
  searchtype = "scientific",
  messages = TRUE,
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

  character; One of 'scientific' (default) or 'common'. This doesn't
  affect the query to NatureServe - but rather affects what column of
  data is targeted in name filtering post data request.

- ask:

  logical; should get_natservid be run in interactive mode? If `TRUE`
  and more than one wormsid is found for the species, the user is asked
  for input. If `FALSE` NA is returned for multiple matches. default:
  `TRUE`

- messages:

  logical; should progress be printed? default: `TRUE`

- rows:

  numeric; Any number from 1 to infinity. If the default NaN, all rows
  are considered. Note that this function still only gives back a
  natservid class object with one to many identifiers. See
  `get_natservid_()` to get back all, or a subset, of the raw data that
  you are presented during the ask process.

- query:

  Deprecated, see `sci_com`

- ...:

  curl options passed on to
  [crul::verb-POST](https://docs.ropensci.org/crul/reference/verb-POST.html)

- x:

  Input to `as.natservid`

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.natservid()`

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

## Note

Authentication no longer required

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

Other taxonomic-ids:
[`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md),
[`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
[`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
[`get_ids()`](https://docs.ropensci.org/taxize/reference/get_ids.md),
[`get_iucn()`](https://docs.ropensci.org/taxize/reference/get_iucn.md),
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
(x <- get_natservid("Helianthus annuus", verbose = TRUE))
attributes(x)
attr(x, "match")
attr(x, "multiple_matches")
attr(x, "pattern_match")
attr(x, "uri")

get_natservid('Gadus morhua')
get_natservid(c("Helianthus annuus", 'Gadus morhua'))

# specify rows to limit choices available
get_natservid('Ruby Quaker Moth', 'common')
get_natservid('Ruby*', 'common')
get_natservid('Ruby*', 'common', rows=1)
get_natservid('Ruby*', 'common', rows=1:2)

# When not found
get_natservid("howdy")
get_natservid(c('Gadus morhua', "howdy"))

# Convert a natservid without class information to a natservid class
# already a natservid, returns the same
as.natservid(get_natservid('Pomatomus saltatrix'))
# same
as.natservid(get_natservid(c('Gadus morhua', 'Pomatomus saltatrix')))
# character
as.natservid(101905)
# character vector, length > 1
as.natservid(c(101905, 101998))
# list, either numeric or character
as.natservid(list(101905, 101998))
## dont check, much faster
as.natservid(101905, check = FALSE)
as.natservid(c(101905, 101998), check = FALSE)
as.natservid(list(101905, 101998), check = FALSE)

(out <- as.natservid(c(101905, 101998), check = FALSE))
data.frame(out)
as.natservid( data.frame(out) )

# Get all data back
get_natservid_("Helianthus")
get_natservid_("Ruby*", searchtype = "common")
get_natservid_("Ruby*", searchtype = "common", rows=1:3)
} # }
```
