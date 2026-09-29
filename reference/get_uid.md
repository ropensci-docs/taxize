# Get the UID codes from NCBI for taxonomic names.

Retrieve the Unique Identifier (UID) of a taxon from NCBI taxonomy
browser.

## Usage

``` r
get_uid(
  sci_com,
  ask = TRUE,
  messages = TRUE,
  rows = NA,
  modifier = NULL,
  rank_query = NULL,
  division_filter = NULL,
  rank_filter = NULL,
  key = NULL,
  sciname = NULL,
  ...
)

as.uid(x, check = TRUE)

# S3 method for class 'uid'
as.uid(x, check = TRUE)

# S3 method for class 'character'
as.uid(x, check = TRUE)

# S3 method for class 'list'
as.uid(x, check = TRUE)

# S3 method for class 'numeric'
as.uid(x, check = TRUE)

# S3 method for class 'data.frame'
as.uid(x, check = TRUE)

# S3 method for class 'uid'
as.data.frame(x, ...)

get_uid_(sci_com, messages = TRUE, rows = NA, key = NULL, sciname = NULL, ...)
```

## Arguments

- sci_com:

  character; scientific or common name. Or, a `taxon_state` object (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- ask:

  logical; should get_uid be run in interactive mode? If TRUE and more
  than one TSN is found for the species, the user is asked for input. If
  FALSE NA is returned for multiple matches.

- messages:

  logical; If `TRUE` (default) the actual taxon queried is printed on
  the console.

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a uid
  class object with one to many identifiers. See `get_uid_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- modifier:

  (character) A modifier to the `sci_com` given. Options include:
  Organism, Scientific Name, Common Name, All Names, Division, Filter,
  Lineage, GC, MGC, Name Tokens, Next Level, PGC, Properties, Rank,
  Subtree, Synonym, Text Word. These are not checked, so make sure they
  are entered correctly, as is.

- rank_query:

  (character) A taxonomic rank name to modify the query sent to NCBI.
  See [rank_ref](https://docs.ropensci.org/taxize/reference/rank_ref.md)
  for possible options. Though note that some data sources use atypical
  ranks, so inspect the data itself for options. Optional. See
  `Querying` below.

- division_filter:

  (character) A division (aka phylum) name to filter data after
  retrieved from NCBI. Optional. See `Filtering` below.

- rank_filter:

  (character) A taxonomic rank name to filter data after retrieved from
  NCBI. See
  [rank_ref](https://docs.ropensci.org/taxize/reference/rank_ref.md) for
  possible options. Though note that some data sources use atypical
  ranks, so inspect the data itself for options. Optional. See
  `Filtering` below.

- key:

  (character) NCBI Entrez API key. optional. See Details.

- sciname:

  Deprecated, see `sci_com`

- ...:

  Ignored

- x:

  Input to `as.uid()`

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.uid()`

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

## Rate limits

In case you run into errors due to your rate limit being exceeded, see
[`taxize_options()`](https://docs.ropensci.org/taxize/reference/taxize_options.md),
where you can set `ncbi_sleep`.

## Querying

The parameter `rank_query` is used in the search sent to NCBI, whereas
`rank_filter` filters data after it comes back. The parameter `modifier`
adds modifiers to the name. For example, `modifier="Organism"` adds that
to the name, giving e.g., `Helianthus[Organism]`.

## Filtering

The parameters `division_filter` and `rank_filter` are not used in the
search to the data provider, but are used in filtering the data down to
a subset that is closer to the target you want. For all these
parameters, you can use regex strings since we use
[`grep()`](https://rdrr.io/r/base/grep.html) internally to match.
Filtering narrows down to the set that matches your query, and removes
the rest.

## Beware

NCBI does funny things sometimes. E.g., if you search on Fringella
morel, a slight misspelling of the genus name, and a non-existent
epithet, NCBI gives back a morel fungal species. In addition, NCBI
doesn't really do fuzzy searching very well, so if there is a slight
mis-spelling in your names, you likely won't get what you are expecting.
The lesson: clean your names before using this function. Other data
sources are better about fuzzy matching.

## Authentication

See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication

Note that even though you can't pass in your key to `as.uid` functions,
we still use your Entrez API key if you have it saved as an R option or
environment variable.

## HTTP version

We hard code `http_version = 2L` to use HTTP/1.1 in HTTP requests to the
Entrez API. See `curl::curl_symbols('CURL_HTTP_VERSION')`

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
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

## Author

Eduard Szoecs, <eduardszoecs@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
get_uid(c("Chironomus riparius", "Chaetopteryx"))
get_uid(c("Chironomus riparius", "aaa vva"))

# When not found
get_uid("howdy")
get_uid(c("Chironomus riparius", "howdy"))

# Narrow down results to a division or rank, or both
## By modifying the query
### w/ modifiers to the name
get_uid(sci_com = "Aratinga acuticauda", modifier = "Organism")
get_uid(sci_com = "bear", modifier = "Common Name")

### w/ rank query
get_uid(sci_com = "Pinus", rank_query = "genus")
get_uid(sci_com = "Pinus", rank_query = "subgenus")
### division query doesn't really work, for unknown reasons, so not available

## By filtering the result
## Echinacea example
### Results w/o narrowing
get_uid("Echinacea")
### w/ division
get_uid(sci_com = "Echinacea", division_filter = "eudicots")
get_uid(sci_com = "Echinacea", division_filter = "sea urchins")

## Satyrium example
### Results w/o narrowing
get_uid(sci_com = "Satyrium")
### w/ division
get_uid(sci_com = "Satyrium", division_filter = "monocots")
get_uid(sci_com = "Satyrium", division_filter = "butterflies")

## Rank example
get_uid(sci_com = "Pinus")
get_uid(sci_com = "Pinus", rank_filter = "genus")
get_uid(sci_com = "Pinus", rank_filter = "subgenus")

# Fuzzy filter on any filtering fields
## uses grep on the inside
get_uid("Satyrium", division_filter = "m")

# specify rows to limit choices available
get_uid('Dugesia') # user prompt needed
get_uid('Dugesia', rows=1) # 2 choices, so returns only 1 row, so no choices
get_uid('Dugesia', ask = FALSE) # returns NA for multiple matches

# Go to a website with more info on the taxon
res <- get_uid("Chironomus riparius")
browseURL(attr(res, "uri"))

# Convert a uid without class information to a uid class
as.uid(get_uid("Chironomus riparius")) # already a uid, returns the same
as.uid(get_uid(c("Chironomus riparius","Pinus contorta"))) # same
as.uid(315567) # numeric
as.uid(c(315567,3339,9696)) # numeric vector, length > 1
as.uid("315567") # character
as.uid(c("315567","3339","9696")) # character vector, length > 1
as.uid(list("315567","3339","9696")) # list, either numeric or character
## dont check, much faster
as.uid("315567", check=FALSE)
as.uid(315567, check=FALSE)
as.uid(c("315567","3339","9696"), check=FALSE)
as.uid(list("315567","3339","9696"), check=FALSE)

(out <- as.uid(c(315567,3339,9696)))
data.frame(out)
as.uid( data.frame(out) )

# Get all data back
get_uid_("Puma concolor")
get_uid_("Dugesia")
get_uid_("Dugesia", rows=2)
get_uid_("Dugesia", rows=1:2)
get_uid_(c("asdfadfasd","Pinus contorta"))

# use curl options
get_uid("Quercus douglasii", verbose = TRUE)
} # }
```
