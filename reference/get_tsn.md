# Get the TSN code for a search term.

Retrieve the taxonomic serial numbers (TSN) of a taxon from ITIS.

## Usage

``` r
get_tsn(
  sci_com,
  searchtype = "scientific",
  accepted = FALSE,
  ask = TRUE,
  messages = TRUE,
  rows = NA,
  searchterm = NULL,
  ...
)

as.tsn(x, check = TRUE)

# S3 method for class 'tsn'
as.tsn(x, check = TRUE)

# S3 method for class 'character'
as.tsn(x, check = TRUE)

# S3 method for class 'list'
as.tsn(x, check = TRUE)

# S3 method for class 'numeric'
as.tsn(x, check = TRUE)

# S3 method for class 'data.frame'
as.tsn(x, check = TRUE)

# S3 method for class 'tsn'
as.data.frame(x, ...)

get_tsn_(
  sci_com,
  messages = TRUE,
  searchtype = "scientific",
  accepted = TRUE,
  rows = NA,
  searchterm = NULL,
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

- accepted:

  logical; If TRUE, removes names that are not accepted valid names by
  ITIS. Set to `FALSE` (default) to give back both accepted and
  unaccepted names.

- ask:

  logical; should get_tsn be run in interactive mode? If `TRUE` and more
  than one TSN is found for the species, the user is asked for input. If
  `FALSE` NA is returned for multiple matches.

- messages:

  logical; should progress be printed?

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a tsn
  class object with one to many identifiers. See `get_tsn_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- searchterm:

  Deprecated, see `sci_com`

- ...:

  Ignored

- x:

  Input to as.tsn

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.tsn()`

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
[`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

## Examples

``` r
if (FALSE) { # \dontrun{
get_tsn("Quercus douglasii")
get_tsn("Chironomus riparius")
get_tsn(c("Chironomus riparius","Quercus douglasii"))
splist <- c("annona cherimola", 'annona muricata', "quercus robur",
    "shorea robusta", "pandanus patina", "oryza sativa", "durio zibethinus")
get_tsn(splist, messages=FALSE)

# specify rows to limit choices available
get_tsn('Arni')
get_tsn('Arni', rows=1)
get_tsn('Arni', rows=1:2)

# When not found
get_tsn("howdy")
get_tsn(c("Chironomus riparius", "howdy"))

# Using common names
get_tsn("black bear", searchtype="common")

# Convert a tsn without class information to a tsn class
as.tsn(get_tsn("Quercus douglasii")) # already a tsn, returns the same
as.tsn(get_tsn(c("Chironomus riparius","Pinus contorta"))) # same
as.tsn(19322) # numeric
as.tsn(c(19322,129313,506198)) # numeric vector, length > 1
as.tsn("19322") # character
as.tsn(c("19322","129313","506198")) # character vector, length > 1
as.tsn(list("19322","129313","506198")) # list, either numeric or character
## dont check, much faster
as.tsn("19322", check=FALSE)
as.tsn(19322, check=FALSE)
as.tsn(c("19322","129313","506198"), check=FALSE)
as.tsn(list("19322","129313","506198"), check=FALSE)

(out <- as.tsn(c(19322,129313,506198)))
data.frame(out)
as.tsn( data.frame(out) )

# Get all data back
get_tsn_("Arni")
get_tsn_("Arni", rows=1)
get_tsn_("Arni", rows=1:2)
get_tsn_(c("asdfadfasd","Pinus contorta"), rows=1:5)
} # }
```
