# Get the page name for a Wiki taxon

Get the page name for a Wiki taxon

## Usage

``` r
get_wiki(
  sci_com,
  wiki_site = "species",
  wiki = "en",
  ask = TRUE,
  messages = TRUE,
  limit = 100,
  rows = NA,
  x = NULL,
  ...
)

as.wiki(x, check = TRUE, wiki_site = "species", wiki = "en")

# S3 method for class 'wiki'
as.wiki(x, check = TRUE, wiki_site = "species", wiki = "en")

# S3 method for class 'character'
as.wiki(x, check = TRUE, wiki_site = "species", wiki = "en")

# S3 method for class 'list'
as.wiki(x, check = TRUE, wiki_site = "species", wiki = "en")

# S3 method for class 'numeric'
as.wiki(x, check = TRUE, wiki_site = "species", wiki = "en")

# S3 method for class 'data.frame'
as.wiki(x, check = TRUE, wiki_site = "species", wiki = "en")

# S3 method for class 'wiki'
as.data.frame(x, ...)

get_wiki_(
  x,
  messages = TRUE,
  wiki_site = "species",
  wiki = "en",
  limit = 100,
  rows = NA,
  ...
)
```

## Arguments

- sci_com:

  (character) A vector of common or scientific names. Or, a
  `taxon_state` object (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- wiki_site:

  (character) Wiki site. One of species (default), pedia, commons

- wiki:

  (character) language. Default: en

- ask:

  logical; should get_wiki be run in interactive mode? If `TRUE` and
  more than one wiki is found for the species, the user is asked for
  input. If `FALSE` NA is returned for multiple matches.

- messages:

  logical; should progress be printed?

- limit:

  (integer) number of records to return

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this function still only gives back a wiki
  class object with one to many identifiers. See `get_wiki_()` to get
  back all, or a subset, of the raw data that you are presented during
  the ask process.

- x:

  For `get_wiki()`: deprecated, see `sci_com`. For `as.wiki`, various,
  see examples

- ...:

  Ignored

- check:

  logical; Check if ID matches any existing on the DB, only used in
  `as.wiki()`

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

For `wiki_site = "pedia" `, we use the english language site by default.
Set the `wiki` parameter for a different language site.

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
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

## Examples

``` r
if (FALSE) { # \dontrun{
get_wiki(sci_com = "Quercus douglasii")
get_wiki(sci_com = "Quercu")
get_wiki(sci_com = "Quercu", "pedia")
get_wiki(sci_com = "Quercu", "commons")

# diff. wikis with wikipedia
get_wiki("Malus domestica", "pedia")
get_wiki("Malus domestica", "pedia", "fr")

# as coercion
as.wiki("Malus_domestica")
as.wiki("Malus_domestica", wiki_site = "commons")
as.wiki("Malus_domestica", wiki_site = "pedia")
as.wiki("Malus_domestica", wiki_site = "pedia", wiki = "fr")
as.wiki("Malus_domestica", wiki_site = "pedia", wiki = "da")
} # }
```
