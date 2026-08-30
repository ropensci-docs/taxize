# Get Kew's Plants of the World code for a taxon

Get Kew's Plants of the World code for a taxon

## Usage

``` r
get_pow(
  sci_com,
  accepted = FALSE,
  ask = TRUE,
  messages = TRUE,
  rows = NA,
  family_filter = NULL,
  rank_filter = NULL,
  x = NULL,
  ...
)

as.pow(x, check = TRUE)

# S3 method for class 'pow'
as.pow(x, check = TRUE)

# S3 method for class 'character'
as.pow(x, check = TRUE)

# S3 method for class 'list'
as.pow(x, check = TRUE)

# S3 method for class 'data.frame'
as.pow(x, check = TRUE)

# S3 method for class 'pow'
as.data.frame(x, ...)

get_pow_(sci_com, messages = TRUE, rows = NA, x = NULL, ...)
```

## Arguments

- sci_com:

  character; A vector of common or scientific names. Or, a `taxon_state`
  object (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- accepted:

  logical; If TRUE, removes names that are not accepted valid names by
  ITIS. Set to `FALSE` (default) to give back both accepted and
  unaccepted names.

- ask:

  logical; should `get_pow` be run in interactive mode? If TRUE and more
  than one pow is found for teh species, the user is asked for input. If
  FALSE NA is returned for multiple matches.

- messages:

  logical; should progress be printed?

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a pow
  class object with one to many identifiers. See `get_pow_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- family_filter:

  (character) A division (aka phylum) name to filter data after
  retrieved from NCBI. Optional. See `Filtering` below.

- rank_filter:

  (character) A taxonomic rank name to filter data after retrieved from
  NCBI. See
  [rank_ref](https://docs.ropensci.org/taxize/reference/rank_ref.md) for
  possible options. Though note that some data sources use atypical
  ranks, so inspect the data itself for options. Optional. See
  `Filtering` below.

- x:

  For `get_pow()`: deprecated, see `sci_com`. For `as.pow`, various, see
  examples

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.pow()`

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

The parameters `family_filter` an`rank_filter`er are not used in the
search to the data provider, but are used in filtering the data down to
a subset that is closer to the target you want. For these two
parameters, you can use regex strings since we use
[`grep()`](https://rdrr.io/r/base/grep.html) internally to match.
Filtering narrows down to the set that matches your query, and removes
the rest.

## Rate-limits

As of February 2019, KEW was limiting to 5 requests per second. Note
that they may change that number in the future.

If you get errors that contain `429` you are hitting the rate limit, and
you can get around it by doing requests with `Sys.sleep` in between
requests.

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

Other pow:
[`pow_lookup()`](https://docs.ropensci.org/taxize/reference/pow_lookup.md),
[`pow_search()`](https://docs.ropensci.org/taxize/reference/pow_search.md),
[`pow_synonyms()`](https://docs.ropensci.org/taxize/reference/pow_synonyms.md)

Other taxonomic-ids:
[`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md),
[`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
[`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
[`get_ids()`](https://docs.ropensci.org/taxize/reference/get_ids.md),
[`get_iucn()`](https://docs.ropensci.org/taxize/reference/get_iucn.md),
[`get_natservid()`](https://docs.ropensci.org/taxize/reference/get_natservid.md),
[`get_nbnid()`](https://docs.ropensci.org/taxize/reference/get_nbnid.md),
[`get_tolid()`](https://docs.ropensci.org/taxize/reference/get_tolid.md),
[`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
[`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
[`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

## Examples

``` r
if (FALSE) { # \dontrun{
get_pow(sci_com="Helianthus")
get_pow(c("Helianthus","Quercus douglasii"))

# Get back a subset
get_pow(sci_com="Helianthus", rows = 1)
get_pow(sci_com="Helianthus", rows = 1:10)

# When not found
get_pow("howdy")
get_pow(c("Helianthus annuus", "howdy"))

# Narrow down results 
# to accepted names
get_pow("Helianthus", accepted = TRUE)
# to a kingom 
get_pow("Helianthus", rank_filter = "genus")
# to accepted names and rank
get_pow("Helianthus annuus", accepted = TRUE, rank_filter = "species")
# to a family
get_pow("flower", family_filter = "Acanthaceae")

# Convert a pow without class information to a pow class
z <- get_pow("Helianthus annuus", accepted = TRUE, rank_filter = "species")
# already a pow, returns the same
as.pow(z)
as.pow("urn:lsid:ipni.org:names:119003-2")
# character vector, length > 1
ids <- c("urn:lsid:ipni.org:names:119003-2","urn:lsid:ipni.org:names:328247-2")
as.pow(ids)
# list, with character strings
as.pow(as.list(ids)) 
## dont check, much faster
as.pow("urn:lsid:ipni.org:names:119003-2", check=FALSE)
as.pow(ids, check=FALSE)
as.pow(as.list(ids), check=FALSE)

(out <- as.pow(ids))
data.frame(out)
as.pow( data.frame(out) )

# Get all data back
get_pow_("Quercus", rows=1:5)
get_pow_("Quercus", rows=1)
get_pow_(c("Pinus", "Abies"), rows = 1:3)
} # }
```
