# EUBON taxonomy search

EUBON taxonomy search

## Usage

``` r
eubon_search(
  query,
  providers = "pesi",
  searchMode = "scientificNameExact",
  addSynonymy = FALSE,
  addParentTaxon = FALSE,
  timeout = 0,
  dedup = NULL,
  limit = 20,
  page = 1,
  ...
)
```

## Arguments

- query:

  (character) The scientific name to search for. For example: "Bellis
  perennis", "Prionus" or "Bolinus brandaris". This is an exact search
  so wildcard characters are not supported

- providers:

  (character) A list of provider id strings concatenated by comma
  characters. The default : "pesi,bgbm-cdm-server\[col\]" will be used
  if this parameter is not set. A list of all available provider ids can
  be obtained from the '/capabilities' service end point. Providers can
  be nested, that is a parent provider can have sub providers. If the id
  of the parent provider is supplied all subproviders will be queried.
  The query can also be restricted to one or more subproviders by using
  the following syntax: parent-id\[sub-id-1,sub-id2,...\]

- searchMode:

  (character) Specifies the searchMode. Possible search modes are:
  `scientificNameExact`, `scientificNameLike` (begins with),
  `vernacularNameExact`, `vernacularNameLike` (contains),
  `findByIdentifier`. If the a provider does not support the chosen
  searchMode it will be skipped and the status message in the
  tnrClientStatus will be set to 'unsupported search mode' in this case.

- addSynonymy:

  (logical) Indicates whether the synonymy of the accepted taxon should
  be included into the response. Turning this option on may cause an
  increased response time. Default: `FALSE`

- addParentTaxon:

  (logical) Indicates whether the the parent taxon of the accepted taxon
  should be included into the response. Turning this option on may cause
  a slightly increased response time. Default: `FALSE`

- timeout:

  (numeric) The maximum of milliseconds to wait for responses from any
  of the providers. If the timeout is exceeded the service will just
  return the responses that have been received so far. The default
  timeout is 0 ms (wait for ever)

- dedup:

  (character) Allows to deduplicate the results by making use of a
  deduplication strategy. The deduplication is done by comparing
  specific properties of the taxon:

  - id: compares 'taxon.identifier'

  - id_name: compares 'taxon.identifier' AND
    'taxon.taxonName.scientificName'

  - name: compares 'taxon.taxonName.scientificName' Using the pure
    'name' strategy is not recommended.

- limit:

  (numeric/integer) number of records to retrieve. default: 20. This
  only affects the search mode `scientificNameLike` and
  `vernacularNameLike`; other search modes are expected to return only
  one record per check list

- page:

  (numeric/integer) page to retrieve. default: 1. This only affects the
  search mode `scientificNameLike` and `vernacularNameLike`; other
  search modes are expected to return only one record per check list

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## References

https://cybertaxonomy.eu/eu-bon/utis/1.3/doc.html

## See also

Other eubon-methods:
[`eubon_capabilities()`](https://docs.ropensci.org/taxize/reference/eubon_capabilities.md),
[`eubon_children()`](https://docs.ropensci.org/taxize/reference/eubon_children.md),
[`eubon_hierarchy()`](https://docs.ropensci.org/taxize/reference/eubon_hierarchy.md)

## Examples

``` r
if (FALSE) { # \dontrun{
eubon_search("Prionus")
eubon_search("Salmo", "pesi")
eubon_search("Salmo", c("pesi", "worms"))
eubon_search("Salmo", "worms", "scientificNameLike")
eubon_search("Salmo", "worms", "scientificNameLike", limit = 3)
eubon_search("Salmo", "worms", "scientificNameLike", limit = 20, page = 2)
eubon_search("Salmo", "worms", addSynonymy = TRUE)
eubon_search("Salmo", "worms", addParentTaxon = TRUE)
} # }
```
