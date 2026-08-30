# Search the CANADENSYS Vascan API.

Search the CANADENSYS Vascan API.

## Usage

``` r
vascan_search(q, format = "json", raw = FALSE, ...)
```

## Arguments

- q:

  (character) Can be a scientific name, a vernacular name or a VASCAN
  taxon identifier (e.g. 861)

- format:

  (character) One of json (default) or xml.

- raw:

  (logical) If TRUE, raw json or xml returned, if FALSE, parsed data
  returned.

- ...:

  (list) Further args passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

json, xml or a list.

## Details

Note that we lowercase all outputs in data.frame's, but when a list is
given back, we don't touch the list names.

## References

API docs https://data.canadensys.net/vascan/api

## Author

Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
vascan_search(q = "Helianthus annuus")
vascan_search(q = "Helianthus annuus", raw=TRUE)
vascan_search(q = c("Helianthus annuus", "Crataegus dodgei"), raw=TRUE)

# format type
## json
c <- vascan_search(q = "Helianthus annuus", format="json", raw=TRUE)
library("jsonlite")
fromJSON(c, FALSE)

## xml
d <- vascan_search(q = "Helianthus annuus", format="xml", raw=TRUE)
library("xml2")
xml2::read_xml(d)

# lots of names, in this case 50
splist <- names_list(rank='species', size=50)
vascan_search(q = splist)

# Curl options
invisible(vascan_search(q = "Helianthus annuus", verbose = TRUE))
} # }
```
