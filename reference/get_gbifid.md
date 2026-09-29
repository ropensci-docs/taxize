# Get the GBIF backbone taxon ID from taxonomic names.

Get the GBIF backbone taxon ID from taxonomic names.

## Usage

``` r
get_gbifid(
  sci,
  ask = TRUE,
  messages = TRUE,
  rows = NA,
  phylum = NULL,
  class = NULL,
  order = NULL,
  family = NULL,
  rank = NULL,
  method = "backbone",
  sciname = NULL,
  ...
)

as.gbifid(x, check = FALSE)

# S3 method for class 'gbifid'
as.gbifid(x, check = FALSE)

# S3 method for class 'character'
as.gbifid(x, check = TRUE)

# S3 method for class 'list'
as.gbifid(x, check = TRUE)

# S3 method for class 'numeric'
as.gbifid(x, check = TRUE)

# S3 method for class 'data.frame'
as.gbifid(x, check = TRUE)

# S3 method for class 'gbifid'
as.data.frame(x, ...)

get_gbifid_(
  sci,
  messages = TRUE,
  rows = NA,
  method = "backbone",
  sciname = NULL
)
```

## Arguments

- sci:

  (character) one or more scientific names. Or, a `taxon_state` object
  (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- ask:

  logical; should get_gbifid be run in interactive mode? If TRUE and
  more than one ID is found for the species, the user is asked for
  input. If FALSE NA is returned for multiple matches.

- messages:

  logical; If TRUE the actual taxon queried is printed on the console.

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a gbifid
  class object with one to many identifiers. See `get_gbifid_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- phylum:

  (character) A phylum (aka division) name. Optional. See `Filtering`
  below.

- class:

  (character) A class name. Optional. See `Filtering` below.

- order:

  (character) An order name. Optional. See `Filtering` below.

- family:

  (character) A family name. Optional. See `Filtering` below.

- rank:

  (character) A taxonomic rank name. See
  [rank_ref](https://docs.ropensci.org/taxize/reference/rank_ref.md) for
  possible options. Though note that some data sources use atypical
  ranks, so inspect the data itself for options. Optional. See
  `Filtering` below.

- method:

  (character) one of "backbone" or "lookup". See Details.

- sciname:

  Deprecated, see `sci`

- ...:

  Ignored

- x:

  Input to `as.gbifid()`

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.gbifid()`

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

## Details

Internally in this function we use a function to search GBIF's taxonomy,
and if we find an exact match we return the ID for that match. If there
isn't an exact match we return the options to you to pick from.

## method parameter

"backbone" uses the `/species/match` GBIF API route, matching against
their backbone taxonomy. We turn on fuzzy matching by default, as the
search without fuzzy against backbone is quite narrow. "lookup" uses the
`/species/search` GBIF API route, doing a full text search of name
usages covering scientific and vernacular named, species descriptions,
distributions and the entire classification.

## Filtering

The parameters `phylum`, `class`, `order`, `family`, and `rank` are not
used in the search to the data provider, but are used in filtering the
data down to a subset that is closer to the target you want. For all
these parameters, you can use regex strings since we use
[`grep()`](https://rdrr.io/r/base/grep.html) internally to match.
Filtering narrows down to the set that matches your query, and removes
the rest.

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

Other taxonomic-ids:
[`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md),
[`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
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

## Author

Scott Chamberlain,

## Examples

``` r
if (FALSE) { # \dontrun{
get_gbifid(sci='Poa annua')
get_gbifid(sci='Pinus contorta')
get_gbifid(sci='Puma concolor')

#lots of queries
spp <- names_list("species", 10)
res <- get_gbifid(spp)
res
xx <- taxon_last()
xx

# multiple names
get_gbifid(c("Poa annua", "Pinus contorta"))

# specify rows to limit choices available
get_gbifid(sci='Pinus')
get_gbifid(sci='Pinus', rows=10)
get_gbifid(sci='Pinus', rows=1:3)

# When not found, NA given
get_gbifid(sci="uaudnadndj")
get_gbifid(c("Chironomus riparius", "uaudnadndj"))

# Narrow down results to a division or rank, or both
## Satyrium example
### Results w/o narrowing
get_gbifid("Satyrium")
### w/ phylum
get_gbifid("Satyrium", phylum = "Tracheophyta")
get_gbifid("Satyrium", phylum = "Arthropoda")
### w/ phylum & rank
get_gbifid("Satyrium", phylum = "Arthropoda", rank = "genus")

## Rank example
get_gbifid("Poa", method = "lookup")
get_gbifid("Poa", method = "lookup", rank = "genus")
get_gbifid("Poa", method = "lookup", family = "Thripidae")

# Fuzzy filter on any filtering fields
## uses grep on the inside
get_gbifid("Satyrium", phylum = "arthropoda")
get_gbifid("A*", method = "lookup", order = "*tera")
get_gbifid("A*", method = "lookup", order = "*ales")

# Convert a uid without class information to a uid class
as.gbifid(get_gbifid("Poa annua")) # already a uid, returns the same
as.gbifid(get_gbifid(c("Poa annua","Puma concolor"))) # same
as.gbifid(2704179) # numeric
as.gbifid(c(2704179,2435099,3171445)) # numeric vector, length > 1
as.gbifid("2704179") # character
as.gbifid(c("2704179","2435099","3171445")) # character vector, length > 1
as.gbifid(list("2704179","2435099","3171445")) # list, either numeric or character
## dont check, much faster
as.gbifid("2704179", check=FALSE)
as.gbifid(2704179, check=FALSE)
as.gbifid(2704179, check=FALSE)
as.gbifid(c("2704179","2435099","3171445"), check=FALSE)
as.gbifid(list("2704179","2435099","3171445"), check=FALSE)

(out <- as.gbifid(c(2704179,2435099,3171445)))
data.frame(out)
as.uid( data.frame(out) )

# Get all data back
get_gbifid_("Puma concolor")
get_gbifid_(c("Pinus", "uaudnadndj"))
get_gbifid_(c("Pinus", "Puma"), rows=5)
get_gbifid_(c("Pinus", "Puma"), rows=1:5)

# use curl options
invisible(get_gbifid("Quercus douglasii", verbose = TRUE))
} # }
```
