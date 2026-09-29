# Resolve names using Open Tree of Life (OTL) resolver

Resolve names using Open Tree of Life (OTL) resolver

## Usage

``` r
tol_resolve(
  names = NULL,
  context_name = NULL,
  do_approximate_matching = TRUE,
  ids = NULL,
  include_suppressed = FALSE,
  ...
)
```

## Arguments

- names:

  (character) taxon names to be queried

- context_name:

  name of the taxonomic context to be searched (length-one character
  vector). Must match (case sensitive) one of the values returned by
  [`rotl::tnrs_contexts()`](https://docs.ropensci.org/rotl/reference/tnrs_contexts.html).

- do_approximate_matching:

  (logical) A logical indicating whether or not to perform approximate
  string (a.k.a. “fuzzy”) matching. Using `FALSE` will greatly improve
  speed. Default: `TRUE`

- ids:

  An array of OTL ids to use for identifying names. These will be
  assigned to each name in the names array. If ids is provided, then ids
  and names must be identical in length.

- include_suppressed:

  (logical) Ordinarily, some quasi-taxa, such as incertae sedis buckets
  and other non-OTUs, are suppressed from TNRS results. If this
  parameter is true, these quasi-taxa are allowed as possible TNRS
  results. Default: `FALSE`

- ...:

  Curl options passed on to
  [`httr::POST`](https://httr.r-lib.org/reference/POST.html) within
  [`rotl::tnrs_match_names()`](https://docs.ropensci.org/rotl/reference/tnrs_match_names.html)

## Value

A data frame summarizing the results of the query. The original query
output is appended as an attribute to the returned object (and can be
obtained using `attr(object, "original_response")`).

## References

https://github.com/OpenTreeOfLife/germinator/wiki/TNRS-API-v3#match_names

## See also

[`gnr_resolve()`](https://docs.ropensci.org/taxize/reference/gnr_resolve.md),
[`tnrs()`](https://docs.ropensci.org/taxize/reference/tnrs-defunct.md)

## Author

Francois Michonneau <francois.michonneau@gmail.com> Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
tol_resolve(names=c("echinodermata", "xenacoelomorpha",
  "chordata", "hemichordata"))
tol_resolve(c("Hyla", "Salmo", "Diadema", "Nautilus"))
tol_resolve(c("Hyla", "Salmo", "Diadema", "Nautilus"),
  context_name = "Animals")

turducken_spp <- c("Meleagris gallopavo", "Anas platyrhynchos",
  "Gallus gallus")
tol_resolve(turducken_spp, context_name="Animals")
} # }
```
