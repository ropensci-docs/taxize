# Get the NameID codes from Tropicos for taxonomic names.

Get the NameID codes from Tropicos for taxonomic names.

## Usage

``` r
get_tpsid(
  sci,
  ask = TRUE,
  messages = TRUE,
  key = NULL,
  rows = NA,
  family = NULL,
  rank = NULL,
  sciname = NULL,
  ...
)

as.tpsid(x, check = TRUE)

# S3 method for class 'tpsid'
as.tpsid(x, check = TRUE)

# S3 method for class 'character'
as.tpsid(x, check = TRUE)

# S3 method for class 'list'
as.tpsid(x, check = TRUE)

# S3 method for class 'numeric'
as.tpsid(x, check = TRUE)

# S3 method for class 'data.frame'
as.tpsid(x, check = TRUE)

# S3 method for class 'tpsid'
as.data.frame(x, ...)

get_tpsid_(sci, messages = TRUE, key = NULL, rows = NA, sciname = NULL, ...)
```

## Arguments

- sci:

  (character) One or more scientific name's as a vector or list. Or, a
  `taxon_state` object (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- ask:

  logical; should get_tpsid be run in interactive mode? If TRUE and more
  than one ID is found for the species, the user is asked for input. If
  FALSE NA is returned for multiple matches.

- messages:

  logical; If TRUE the actual taxon queried is printed on the console.

- key:

  Your API key; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a tpsid
  class object with one to many identifiers. See `get_tpsid_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- family:

  (character) A family name. Optional. See `Filtering` below.

- rank:

  (character) A taxonomic rank name. See
  [rank_ref](https://docs.ropensci.org/taxize/reference/rank_ref.md) for
  possible options. Though note that some data sources use atypical
  ranks, so inspect the data itself for options. Optional. See
  `Filtering` below.

- sciname:

  Deprecated, see `sci`

- ...:

  Other arguments passed to
  [`tp_search()`](https://docs.ropensci.org/taxize/reference/tp_search.md).

- x:

  Input to `as.tpsid()`

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.tpsid()`

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

The parameters `family` an`rank`nk are not used in the search to the
data provider, but are used in filtering the data down to a subset that
is closer to the target you want. For all these parameters, you can use
regex strings since we use [`grep()`](https://rdrr.io/r/base/grep.html)
internally to match. Filtering narrows down to the set that matches your
query, and removes the rest.

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
[`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
[`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

## Author

Scott Chamberlain,

## Examples

``` r
if (FALSE) { # \dontrun{
get_tpsid(sci='Poa annua')
get_tpsid(sci='Pinus contorta')

get_tpsid(c("Poa annua", "Pinus contorta"))

# specify rows to limit choices available
get_tpsid('Poa ann')
get_tpsid('Poa ann', rows=1)
get_tpsid('Poa ann', rows=25)
get_tpsid('Poa ann', rows=1:2)

# When not found, NA given (howdy is not a species name, and Chrinomus is a fly)
get_tpsid("howdy")
get_tpsid(c("Chironomus riparius", "howdy"))

# Narrow down results to a division or rank, or both
## Satyrium example
### Results w/o narrowing
get_tpsid("Satyrium")
### w/ rank
get_tpsid("Satyrium", rank = "var.")
get_tpsid("Satyrium", rank = "sp.")

## w/ family
get_tpsid("Poa")
get_tpsid("Poa", family = "Iridaceae")
get_tpsid("Poa", family = "Orchidaceae")
get_tpsid("Poa", family = "Orchidaceae", rank = "gen.")

# Fuzzy filter on any filtering fields
## uses grep on the inside
get_tpsid("Poa", family = "orchidaceae")
get_tpsid("Aga", fuzzy = TRUE, parent = "*idae")

# pass to classification function to get a taxonomic hierarchy
classification(get_tpsid(sci='Poa annua'))

# Convert a tpsid without class information to a tpsid class
as.tpsid(get_tpsid("Pinus contorta")) # already a tpsid, returns the same
as.tpsid(get_tpsid(c("Chironomus riparius","Pinus contorta"))) # same
as.tpsid(24900183) # numeric
as.tpsid(c(24900183,50150089,50079838)) # numeric vector, length > 1
as.tpsid("24900183") # character
as.tpsid(c("24900183","50150089","50079838")) # character vector, length > 1
as.tpsid(list("24900183","50150089","50079838")) # list, either numeric or character
## dont check, much faster
as.tpsid("24900183", check=FALSE)
as.tpsid(24900183, check=FALSE)
as.tpsid(c("24900183","50150089","50079838"), check=FALSE)
as.tpsid(list("24900183","50150089","50079838"), check=FALSE)

(out <- as.tpsid(c(24900183,50150089,50079838)))
data.frame(out)
as.tpsid( data.frame(out) )

# Get all data back
get_tpsid_("Poa annua")
get_tpsid_("Poa annua", rows=2)
get_tpsid_("Poa annua", rows=1:2)
get_tpsid_(c("asdfadfasd","Pinus contorta"), rows=1:5)

# use curl options
invisible(get_tpsid("Quercus douglasii", messages = TRUE))
} # }
```
