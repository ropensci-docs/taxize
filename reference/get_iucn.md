# Get a IUCN Redlist taxon

Get a IUCN Redlist taxon

## Usage

``` r
get_iucn(sci, messages = TRUE, key = NULL, x = NULL, ...)

as.iucn(x, check = TRUE, key = NULL)

# S3 method for class 'iucn'
as.iucn(x, check = TRUE, key = NULL)

# S3 method for class 'character'
as.iucn(x, check = TRUE, key = NULL)

# S3 method for class 'list'
as.iucn(x, check = TRUE, key = NULL)

# S3 method for class 'numeric'
as.iucn(x, check = TRUE, key = NULL)

# S3 method for class 'data.frame'
as.iucn(x, check = TRUE, key = NULL)

# S3 method for class 'iucn'
as.data.frame(x, ...)
```

## Arguments

- sci:

  (character) A vector of scientific names. Or, a `taxon_state` object
  (see
  [taxon-state](https://docs.ropensci.org/taxize/reference/taxon-state.md))

- messages:

  logical; should progress be printed?

- key:

  (character) required. you IUCN Redlist API key. See
  [rredlist::rredlist-package](https://docs.ropensci.org/rredlist/reference/rredlist-package.html)
  for help on authenticating with IUCN Redlist

- x:

  For `get_iucn()`: Deprecated, see `sci`. For `as.iucn()`, various, see
  examples

- ...:

  Ignored

- check:

  (logical) Check if ID matches any existing on the DB, only used in
  `as.iucn()`

## Value

A vector of taxonomic identifiers as an S3 class.

Comes with the following attributes:

- *match* (character) - the reason for NA, either 'not found', 'found'
  or if `ask = FALSE` then 'NA due to ask=FALSE')

- *name* (character) - the taxonomic name, which is needed in
  [`synonyms()`](https://docs.ropensci.org/taxize/reference/synonyms.md)
  and
  [`sci2comm()`](https://docs.ropensci.org/taxize/reference/sci2comm.md)
  methods since they internally use rredlist functions which require the
  taxonomic name, and not the taxonomic identifier

- *ri* (character) - The URI where more information can be read on the
  taxon - includes the taxonomic identifier in the URL somewhere

*multiple_matches* and *pattern_match* do not apply here as in other
`get_*` methods since there is no IUCN Redlist search, so you either get
a match or you do not get a match.

## Details

There is no underscore method, because there's no real search for IUCN,
that is, where you search for a string, and get back a bunch of results
due to fuzzy matching. If that exists in the future we'll add an
underscore method here.

IUCN ids only work with
[`synonyms()`](https://docs.ropensci.org/taxize/reference/synonyms.md)
and
[`sci2comm()`](https://docs.ropensci.org/taxize/reference/sci2comm.md)
methods.

## See also

Other taxonomic-ids:
[`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md),
[`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
[`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
[`get_ids()`](https://docs.ropensci.org/taxize/reference/get_ids.md),
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
get_iucn("Branta canadensis")
get_iucn("Branta bernicla")
get_iucn("Panthera uncia")

} # }
```
