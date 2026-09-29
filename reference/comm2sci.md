# Get scientific names from common names.

Get scientific names from common names.

## Usage

``` r
comm2sci(...)

# Default S3 method
comm2sci(
  com,
  db = "ncbi",
  itisby = "search",
  simplify = TRUE,
  commnames = NULL,
  ...
)

# S3 method for class 'tsn'
comm2sci(id, db = "ncbi", itisby = "search", simplify = TRUE, ...)

# S3 method for class 'uid'
comm2sci(id, db = "ncbi", itisby = "search", simplify = TRUE, ...)
```

## Arguments

- ...:

  Further arguments passed on to internal methods.

- com:

  One or more common names or partial names.

- db:

  Data source, one of *"ncbi"* (default), *"itis"*, *"tropicos"*,
  *"eol"*, or *"worms"*. If using ncbi, we recommend getting an API key;
  see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- itisby:

  Search for common names across entire names (search, default), at
  beginning of names (begin), or at end of names (end).

- simplify:

  (logical) If `TRUE`, simplify output to a vector of names. If `FALSE`,
  return variable formats from different sources, usually a data.frame.

- commnames:

  Deprecated, see `com`

- id:

  taxon identifiers, as returned by
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md)
  or
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md)

## Value

If `simplify=TRUE`, a list of scientific names, with list labeled by
your input names. If `simplify=FALSE`, a data.frame with columns that
vary by data source. `character(0)` on no match

## Details

For data sources ITIS and NCBI you can pass in common names directly,
and use
[`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md) or
[`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md) to
get ids first, then pass in to this fxn.

For the other data sources, you can only pass in common names directly.

## Authentication

See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication

## HTTP version for NCBI requests

We hard code `http_version = 2L` to use HTTP/1.1 in HTTP requests to the
Entrez API. See `curl::curl_symbols('CURL_HTTP_VERSION')`

## Rate limits

In case you run into errors due to your rate limit being exceeded, see
[`taxize_options()`](https://docs.ropensci.org/taxize/reference/taxize_options.md),
where you can set `ncbi_sleep`.

## See also

[`sci2comm()`](https://docs.ropensci.org/taxize/reference/sci2comm.md)

## Author

Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
comm2sci(com='american black bear')
comm2sci(com='american black bear', simplify = FALSE)
comm2sci(com='black bear', db='itis')
comm2sci(com='american black bear', db='itis')
comm2sci(com='annual blue grass', db='tropicos')
comm2sci(com=c('annual blue grass','tree of heaven'), db='tropicos')
comm2sci('blue whale', db = "worms")
comm2sci(c('blue whale', 'dwarf surfclam'), db = "worms")

# ncbi: pass in uid's from get_uid() directly
x <- get_uid("western capercaillie", modifier = "Common Name")
comm2sci(x)
# itis: pass in tsn's from get_tsn() directly
x <- get_tsn(c("Louisiana black bear", "american crow"),
  searchtype = "common")
comm2sci(x)
} # }
```
