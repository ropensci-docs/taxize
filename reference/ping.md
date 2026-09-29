# Ping an API used in taxize to see if it's working.

Ping an API used in taxize to see if it's working.

## Usage

``` r
col_ping(what = "status", ...)

eol_ping(what = "status", ...)

itis_ping(what = "status", ...)

ncbi_ping(what = "status", key = NULL, ...)

tropicos_ping(what = "status", ...)

nbn_ping(what = "status", ...)

gbif_ping(what = "status", ...)

bold_ping(what = "status", ...)

ipni_ping(what = "status", ...)

vascan_ping(what = "status", ...)

fg_ping(what = "status", ...)
```

## Arguments

- what:

  (character) One of status (default), content, or an HTTP status code.
  If status, we just check that the HTTP status code is 200, or similar
  signifying the service is up. If content, we do a simple, quick check
  to determine if returned content matches what's expected. If an HTTP
  status code, it must match an appropriate code. See
  [`status_codes()`](https://docs.ropensci.org/taxize/reference/status_codes.md).

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

- key:

  (character) NCBI Entrez API key. optional. See
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md)

## Value

A logical, TRUE or FALSE

## Details

For ITIS, see
[ritis::description](https://docs.ropensci.org/ritis/reference/description.html),
which provides number of scientific and common names in a character
string.

## HTTP version for NCBI requests

We hard code `http_version = 2L` to use HTTP/1.1 in HTTP requests to the
Entrez API. See `curl::curl_symbols('CURL_HTTP_VERSION')`

## Examples

``` r
if (FALSE) { # \dontrun{
col_ping()
col_ping("content")
col_ping(200)
col_ping("200")
col_ping(204)

itis_ping()
eol_ping()
ncbi_ping()
tropicos_ping()
nbn_ping()

gbif_ping()
gbif_ping(200)

bold_ping()
bold_ping(200)
bold_ping("content")

ipni_ping()
ipni_ping(200)
ipni_ping("content")

vascan_ping()
vascan_ping(200)
vascan_ping("content")

# curl options
vascan_ping(verbose = TRUE)
eol_ping(500, verbose = TRUE)
} # }
```
