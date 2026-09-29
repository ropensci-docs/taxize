# Search UK National Biodiversity Network

Search UK National Biodiversity Network

## Usage

``` r
nbn_search(
  sci_com,
  fq = NULL,
  order = NULL,
  sort = NULL,
  start = 0,
  rows = 25,
  facets = NULL,
  q = NULL,
  ...
)
```

## Arguments

- sci_com:

  (character) The query terms(s), a scientific or common name

- fq:

  (character) Filters to be applied to the original query. These are
  additional params of the form fq=INDEXEDFIELD:VALUE e.g.
  fq=rank:kingdom. See https://species-ws.nbnatlas.org/indexFields for
  all the fields that are queryable.

- order:

  (character) Supports "asc" or "desc"

- sort:

  (character) The indexed field to sort by

- start:

  (integer) Record offset, to enable paging

- rows:

  (integer) Number of records to return

- facets:

  (list) Comma separated list of the fields to create facets on e.g.
  facets=basis_of_record.

- q:

  Deprecated, see `sci`

- ...:

  Further args passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html).

## Value

a list with slots for metadata (`meta`) with list of response
attributes, and data (`data`) with a data.frame of results

## References

https://api.nbnatlas.org/

## See also

Other nbn:
[`get_nbnid()`](https://docs.ropensci.org/taxize/reference/get_nbnid.md),
[`nbn_classification()`](https://docs.ropensci.org/taxize/reference/nbn_classification.md),
[`nbn_synonyms()`](https://docs.ropensci.org/taxize/reference/nbn_synonyms.md)

## Author

Scott Chamberlain,

## Examples

``` r
if (FALSE) { # \dontrun{
x <- nbn_search(sci_com = "Vulpes")
x$meta$totalRecords
x$meta$pageSize
x$meta$urlParameters
x$meta$queryTitle
head(x$data)

nbn_search(sci_com = "blackbird", start = 4)

# debug curl stuff
nbn_search(sci_com = "blackbird", verbose = TRUE)
} # }
```
