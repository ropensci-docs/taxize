# Get the OTT id for a search term

Retrieve the Open Tree of Life Taxonomy (OTT) id of a taxon from
OpenTreeOfLife

## Usage

``` r
get_tolid(sci, ask = TRUE, messages = TRUE, rows = NA, sciname = NULL, ...)

as.tolid(x, check = TRUE)

# S3 method for class 'tolid'
as.tolid(x, check = TRUE)

# S3 method for class 'character'
as.tolid(x, check = TRUE)

# S3 method for class 'list'
as.tolid(x, check = TRUE)

# S3 method for class 'numeric'
as.tolid(x, check = TRUE)

# S3 method for class 'data.frame'
as.tolid(x, check = TRUE)

# S3 method for class 'tolid'
as.data.frame(x, ...)

get_tolid_(sci, messages = TRUE, rows = NA, sciname = NULL)
```

## Arguments

- sci:

  character; one or more scientific names. Or, a `taxon_state` object
  (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- ask:

  logical; should `get_tolid` be run in interactive mode? If `TRUE` and
  more than one TOL is found for the species, the user is asked for
  input. If `FALSE` NA is returned for multiple matches.

- messages:

  logical; should progress be printed?

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a tol
  class object with one to many identifiers. See `get_tolid_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- sciname:

  Deprecated, see `sci`

- ...:

  Ignored

- x:

  Input to `as.tolid`

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.tolid()`

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
[`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
[`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
[`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

## Examples

``` r
if (FALSE) { # \dontrun{
get_tolid(sci = "Quercus douglasii")
get_tolid(sci = "Chironomus riparius")
get_tolid(c("Chironomus riparius","Quercus douglasii"))
splist <- c("annona cherimola", 'annona muricata', "quercus robur",
    "shorea robusta", "pandanus patina", "oryza sativa", "durio zibethinus")
get_tolid(splist, messages=FALSE)

# specify rows to limit choices available
get_tolid('Arni')
get_tolid('Arni', rows=1)
get_tolid('Arni', rows=1:2)

# When not found
get_tolid("howdy")
get_tolid(c("Chironomus riparius", "howdy"))

# Convert a tol without class information to a tol class
as.tolid(get_tolid("Quercus douglasii")) # already a tol, returns the same
as.tolid(get_tolid(c("Chironomus riparius","Pinus contorta"))) # same
as.tolid(5907893) # numeric
as.tolid(c(3930798,515712,872577)) # numeric vector, length > 1
as.tolid("3930798") # character
as.tolid(c("3930798","515712","872577")) # character vector, length > 1
as.tolid(list("3930798","515712","872577")) # list, either numeric or character
## dont check, much faster
as.tolid("3930798", check=FALSE)
as.tolid(3930798, check=FALSE)
as.tolid(c("3930798","515712","872577"), check=FALSE)
as.tolid(list("3930798","515712","872577"), check=FALSE)

(out <- as.tolid(c(3930798,515712,872577)))
data.frame(out)
as.tolid( data.frame(out) )

# Get all data back
get_tolid_("Arni")
get_tolid_("Arni", rows=1)
get_tolid_("Arni", rows=1:2)
get_tolid_(c("asdfadfasd","Pinus contorta"))
} # }
```
