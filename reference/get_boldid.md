# Get the BOLD (Barcode of Life) code for a search term.

Get the BOLD (Barcode of Life) code for a search term.

## Usage

``` r
get_boldid(
  sci,
  fuzzy = FALSE,
  dataTypes = "basic",
  includeTree = FALSE,
  ask = TRUE,
  messages = TRUE,
  rows = NA,
  rank = NULL,
  division = NULL,
  parent = NULL,
  searchterm = NULL,
  ...
)

as.boldid(x, check = TRUE)

# S3 method for class 'boldid'
as.boldid(x, check = TRUE)

# S3 method for class 'character'
as.boldid(x, check = TRUE)

# S3 method for class 'list'
as.boldid(x, check = TRUE)

# S3 method for class 'numeric'
as.boldid(x, check = TRUE)

# S3 method for class 'data.frame'
as.boldid(x, check = TRUE)

# S3 method for class 'boldid'
as.data.frame(x, ...)

get_boldid_(
  sci,
  messages = TRUE,
  fuzzy = FALSE,
  dataTypes = "basic",
  includeTree = FALSE,
  rows = NA,
  searchterm = NULL,
  ...
)
```

## Arguments

- sci:

  character; A vector of scientific names. Or, a `taxon_state` object
  (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- fuzzy:

  (logical) Whether to use fuzzy search or not (default: FALSE).

- dataTypes:

  (character) Specifies the datatypes that will be returned. See
  [`bold_search()`](https://docs.ropensci.org/taxize/reference/bold_search.md)
  for options.

- includeTree:

  (logical) If TRUE (default: FALSE), returns a list containing
  information for parent taxa as well as the specified taxon.

- ask:

  logical; should get_tsn be run in interactive mode? If TRUE and more
  than one TSN is found for teh species, the user is asked for input. If
  FALSE NA is returned for multiple matches.

- messages:

  logical; should progress be printed?

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a boldid
  class object with one to many identifiers. See `get_boldid_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- rank:

  (character) A taxonomic rank name. See
  [rank_ref](https://docs.ropensci.org/taxize/reference/rank_ref.md) for
  possible options. Though note that some data sources use atypical
  ranks, so inspect the data itself for options. Optional. See
  `Filtering` below.

- division:

  (character) A division (aka phylum) name. Optional. See `Filtering`
  below.

- parent:

  (character) A parent name (i.e., the parent of the target search
  taxon). Optional. See `Filtering` below.

- searchterm:

  Deprecated, see `sci`

- ...:

  Curl options passed on to
  [`crul::verb-GET`](https://docs.ropensci.org/crul/reference/verb-GET.html)

- x:

  Input to `as.boldid()`

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.boldid()`

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

## Filtering

The parameters `division`, `parent`, and `rank` are not used in the
search to the data provider, but are used in filtering the data down to
a subset that is closer to the target you want. For all these
parameters, you can use regex strings since we use
[`grep()`](https://rdrr.io/r/base/grep.html) internally to match.
Filtering narrows down to the set that matches your query, and removes
the rest.

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

Other taxonomic-ids:
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
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

## Examples

``` r
if (FALSE) { # \dontrun{
get_boldid(sci = "Agapostemon")
get_boldid(sci = "Chironomus riparius")
get_boldid(c("Chironomus riparius","Quercus douglasii"))
splist <- names_list('species')
get_boldid(splist, messages=FALSE)

# Fuzzy searching
get_boldid(sci="Osmi", fuzzy=TRUE)

# Get back a subset
get_boldid(sci="Osmi", fuzzy=TRUE, rows = 1)
get_boldid(sci="Osmi", fuzzy=TRUE, rows = 1:10)
get_boldid(sci=c("Osmi","Aga"), fuzzy=TRUE, rows = 1)
get_boldid(sci=c("Osmi","Aga"), fuzzy=TRUE, rows = 1:3)

# found
get_boldid('Epicordulia princeps')
get_boldid('Arigomphus furcifer')

# When not found
get_boldid("howdy")
get_boldid(c("Chironomus riparius", "howdy"))
get_boldid("Cordulegaster erronea")
get_boldid("Nasiaeshna pentacantha")

# Narrow down results to a division or rank, or both
## Satyrium example
### Results w/o narrowing
get_boldid("Satyrium")
### w/ phylum
get_boldid("Satyrium", division = "Plantae")
get_boldid("Satyrium", division = "Animalia")

## Rank example
get_boldid("Osmia", fuzzy = TRUE)
get_boldid("Osmia", fuzzy = TRUE, rank = "genus")

# Fuzzy filter on any filtering fields
## uses grep on the inside
get_boldid("Satyrium", division = "anim")
get_boldid("Aga", fuzzy = TRUE, parent = "*idae")

# Convert a boldid without class information to a boldid class
as.boldid(get_boldid("Agapostemon")) # already a boldid, returns the same
as.boldid(get_boldid(c("Agapostemon","Quercus douglasii"))) # same
as.boldid(1973) # numeric
as.boldid(c(1973,101009,98597)) # numeric vector, length > 1
as.boldid("1973") # character
as.boldid(c("1973","101009","98597")) # character vector, length > 1
as.boldid(list("1973","101009","98597")) # list, either numeric or character
## dont check, much faster
as.boldid("1973", check=FALSE)
as.boldid(1973, check=FALSE)
as.boldid(c("1973","101009","98597"), check=FALSE)
as.boldid(list("1973","101009","98597"), check=FALSE)

(out <- as.boldid(c(1973,101009,98597)))
data.frame(out)
as.boldid( data.frame(out) )

# Get all data back
get_boldid_("Osmia", fuzzy=TRUE, rows=1:5)
get_boldid_("Osmia", fuzzy=TRUE, rows=1)
get_boldid_(c("Osmi","Aga"), fuzzy=TRUE, rows = 1:3)
} # }
```
