# Search Kew's Plants of the World

Search Kew's Plants of the World

## Usage

``` r
pow_search(sci_com, limit = 100, cursor = "*", sort = NULL, q = NULL, ...)
```

## Arguments

- sci_com:

  (character) query terms, scientific or common name

- limit:

  (integer) Number of records to return. default: 100

- cursor:

  (character) cursor string

- sort:

  (character) The field to sort by and sort order separted with
  underscore, e.g., `sort="name_desc"`

- q:

  Deprecated, see `sci_com`

- ...:

  Further args passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html).

## Value

a list with slots for metadata (`meta`) with list of response
attributes, and data (`data`) with a data.frame of results

## References

https://powo.science.kew.org/

## See also

Other pow:
[`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md),
[`pow_lookup()`](https://docs.ropensci.org/taxize/reference/pow_lookup.md),
[`pow_synonyms()`](https://docs.ropensci.org/taxize/reference/pow_synonyms.md)

## Author

Scott Chamberlain,

## Examples

``` r
if (FALSE) { # \dontrun{
x <- pow_search(sci_com = "Quercus")
x$meta
x$meta$totalResults
x$meta$perPage
x$meta$totalPages
x$meta$page
x$meta$cursor
head(x$data)

# pagination
pow_search(sci_com = "sunflower", limit = 2)

# debug curl stuff
invisible(pow_search(sci_com = "Helianthus annuus", verbose = TRUE))

# sort
desc <- pow_search(sci_com = "Helianthus", sort = "name_desc")
desc$data$name
asc <- pow_search(sci_com = "Helianthus", sort = "name_asc")
asc$data$name
} # }
```
