# Get the EOL ID from Encyclopedia of Life from taxonomic names.

Note that EOL doesn't expose an API endpoint for directly querying for
EOL taxon ID's, so we first use the function
[`eol_search()`](https://docs.ropensci.org/taxize/reference/eol_search.md)
to find pages that deal with the species of interest, then use
[`eol_pages()`](https://docs.ropensci.org/taxize/reference/eol_pages.md)
to find the actual taxon IDs.

## Usage

``` r
get_eolid(
  sci_com,
  ask = TRUE,
  messages = TRUE,
  rows = NA,
  rank = NULL,
  data_source = NULL,
  sciname = NULL,
  ...
)

as.eolid(x, check = TRUE)

# S3 method for class 'eolid'
as.eolid(x, check = TRUE)

# S3 method for class 'character'
as.eolid(x, check = TRUE)

# S3 method for class 'list'
as.eolid(x, check = TRUE)

# S3 method for class 'numeric'
as.eolid(x, check = TRUE)

# S3 method for class 'data.frame'
as.eolid(x, check = TRUE)

# S3 method for class 'eolid'
as.data.frame(x, ...)

get_eolid_(sci_com, messages = TRUE, rows = NA, sciname = NULL, ...)
```

## Arguments

- sci_com:

  character; one or more scientific or common names. Or, a `taxon_state`
  object (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- ask:

  logical; should get_eolid be run in interactive mode? If TRUE and more
  than one ID is found for the species, the user is asked for input. If
  FALSE NA is returned for multiple matches.

- messages:

  logical; If `TRUE` the actual taxon queried is printed on the console.

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a eolid
  class object with one to many identifiers. See `get_eolid_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- rank:

  (character) A taxonomic rank name. See
  [rank_ref](https://docs.ropensci.org/taxize/reference/rank_ref.md) for
  possible options. Though note that some data sources use atypical
  ranks, so inspect the data itself for options. Optional. See
  `Filtering` below.

- data_source:

  (character) A data source inside of EOL. These are longish names like
  e.g., "Barcode of Life Data Systems" or "USDA PLANTS images".
  Optional. See `Filtering` below.

- sciname:

  Deprecated, see `sci_com`

- ...:

  Further args passed on to
  [`eol_search()`](https://docs.ropensci.org/taxize/reference/eol_search.md)

- x:

  Input to `as.eolid()`

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.eolid()`

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

EOL is a bit odd in that they have page IDs for each taxon, but then
within that, they have taxon ids for various taxa within that page
(e.g., GBIF and NCBI each have a taxon they refer to within the page
\[i.e., taxon\]). And we need the taxon ids from a particular data
provider (e.g, NCBI) to do other things, like get a higher
classification tree. However, humans want the page id, not the taxon id.
So, the id returned from this function is the taxon id, not the page id.
You can get the page id for a taxon by using
[`eol_search()`](https://docs.ropensci.org/taxize/reference/eol_search.md)
and
\`[`eol_pages()`](https://docs.ropensci.org/taxize/reference/eol_pages.md),
and the URI returned in the attributes for a taxon will lead you to the
taxon page, and the ID in the URL is the page id.

## Filtering

The parameters `rank` and `data_source` are not used in the search to
the data provider, but are used in filtering the data down to a subset
that is closer to the target you want. For all these parameters, you can
use regex strings since we use
[`grep()`](https://rdrr.io/r/base/grep.html) internally to match.
Filtering narrows down to the set that matches your query, and removes
the rest.

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

Other taxonomic-ids:
[`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md),
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

## Author

Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
get_eolid(sci_com='Pinus contorta')
get_eolid(sci_com='Puma concolor')

get_eolid(c("Puma concolor", "Pinus contorta"))

# specify rows to limit choices available
get_eolid('Poa annua')
get_eolid('Poa annua', rows=1)
get_eolid('Poa annua', rows=2)
get_eolid('Poa annua', rows=1:2)

# When not found
get_eolid(sci_com="uaudnadndj")
get_eolid(c("Chironomus riparius", "uaudnadndj"))

# filter results to a rank or data source, or both
get_eolid("Satyrium")
get_eolid("Satyrium", rank = "genus")
get_eolid("Satyrium", data_source = "INAT")
get_eolid("Satyrium", rank = "genus",
  data_source = "North Pacific Species List")

# Convert a eolid without class information to a eolid class
# already a eolid, returns the same
as.eolid(get_eolid("Chironomus riparius"))
# same
as.eolid(get_eolid(c("Chironomus riparius","Pinus contorta")))
# numeric
as.eolid(10247706)
# numeric vector, length > 1
as.eolid(c(6985636,12188704,10247706))
# character
as.eolid("6985636")
# character vector, length > 1
as.eolid(c("6985636","12188704","10247706"))
# list, either numeric or character
as.eolid(list("6985636","12188704","10247706"))
## dont check, much faster
as.eolid("6985636", check=FALSE)
as.eolid(6985636, check=FALSE)
as.eolid(c("6985636","12188704","10247706"), check=FALSE)
as.eolid(list("6985636","12188704","10247706"), check=FALSE)

(out <- as.eolid(c(6985636,12188704,10247706)))
data.frame(out)
as.eolid( data.frame(out) )

# Get all data back
get_eolid_("Poa annua")
get_eolid_("Poa annua", rows=2)
get_eolid_("Poa annua", rows=1:2)
get_eolid_(c("asdfadfasd", "Pinus contorta"))
} # }
```
