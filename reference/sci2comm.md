# Get common names from scientific names.

Get common names from scientific names.

## Usage

``` r
sci2comm(...)

# Default S3 method
sci2comm(sci, db = "ncbi", simplify = TRUE, scinames = NULL, ...)

# S3 method for class 'uid'
sci2comm(id, ...)

# S3 method for class 'tsn'
sci2comm(id, simplify = TRUE, ...)

# S3 method for class 'wormsid'
sci2comm(id, simplify = TRUE, ...)

# S3 method for class 'iucn'
sci2comm(id, simplify = TRUE, ...)
```

## Arguments

- ...:

  Further arguments passed on to functions
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md).

- sci:

  character; One or more scientific names or partial names.

- db:

  character; Data source, one of `"ncbi"` (default), `"itis"` `"eol"`,
  `"worms"`, or `"iucn"`. Note that each taxonomic data source has their
  own identifiers, so that if you provide the wrong `db` value for the
  identifier you could get a result, but it will likely be wrong (not
  what you were expecting). If using ncbi or iucn we recommend getting
  an API key; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- simplify:

  (logical) If TRUE, simplify output to a vector of names. If FALSE,
  return variable formats from different sources, usually a data.frame.
  Only applies to eol and itis. Specify `FALSE` to obtain the language
  of each vernacular in the output for eol and itis.

- scinames:

  Deprecated, see `sci`

- id:

  character; identifiers, as returned by
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md).

## Value

List of character vectors, named by input taxon name, or taxon ID.
`character(0)` on no match

## Authentication

See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication

## HTTP version for NCBI requests

We hard code `http_version = 2L` to use HTTP/1.1 in HTTP requests to the
Entrez API. See `curl::curl_symbols('CURL_HTTP_VERSION')`

## See also

[`comm2sci()`](https://docs.ropensci.org/taxize/reference/comm2sci.md)

## Author

Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
sci2comm(sci='Helianthus annuus')
sci2comm(sci='Helianthus annuus', db='eol')
sci2comm(sci=c('Helianthus annuus', 'Poa annua'))
sci2comm(sci='Puma concolor', db='ncbi')
sci2comm('Gadus morhua', db='worms')
sci2comm('Pomatomus saltatrix', db='worms')
sci2comm('Loxodonta africana', db='iucn')

# Passing id in, works for sources: itis and ncbi, not eol
sci2comm(get_uid('Helianthus annuus'))
sci2comm(get_wormsid('Gadus morhua'))
sci2comm(get_iucn('Loxodonta africana'))

# Don't simplify returned
sci2comm(get_iucn('Loxodonta africana'), simplify=FALSE)

# Use curl options
sci2comm('Helianthus annuus', db="ncbi", verbose = TRUE)
} # }
```
