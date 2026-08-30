# Taxonomic IDs to taxonomic names

Taxonomic IDs to taxonomic names

## Usage

``` r
id2name(id, db = NULL, x = NULL, ...)

# Default S3 method
id2name(id, db = NULL, x = NULL, ...)

# S3 method for class 'tolid'
id2name(id, ...)

# S3 method for class 'tsn'
id2name(id, ...)

# S3 method for class 'uid'
id2name(id, ...)

# S3 method for class 'wormsid'
id2name(id, ...)

# S3 method for class 'gbifid'
id2name(id, ...)

# S3 method for class 'boldid'
id2name(id, ...)
```

## Arguments

- id:

  vector of taxonomic IDs (character or numeric)

- db:

  (character) database to query. One or more of `tol`, `itis`, `ncbi`,
  `worms`, `gbif`, or `bold`. Note that each taxonomic data source has
  their own identifiers, so that if you provide the wrong `db` value for
  the identifier you could get a result, but it will likely be wrong
  (not what you were expecting). If using ncbi we recommend getting API
  keys; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- x:

  Deprecated, see `id`

- ...:

  Further args passed on to `tol_id2name` or
  [itis_getrecord](https://docs.ropensci.org/taxize/reference/itis_getrecord.md),
  or other internal functions. See those functions for what parameters
  can be passed on.

## Value

A named list of data.frames, named by the input taxonomic ids

## HTTP version for NCBI requests

We hard code `http_version = 2L` to use HTTP/1.1 in HTTP requests to the
Entrez API. See `curl::curl_symbols('CURL_HTTP_VERSION')`

## Examples

``` r
if (FALSE) { # \dontrun{
# ITIS
id2name(19322, db = "itis")

# TOL
id2name(515698, db = "tol")
# get NCBI ID and pass to classification()
x <- id2name(515698, db = "tol")
classification(as.uid(x[[1]]$tax_sources_ncbi))

# NCBI
id2name(315567, db = "ncbi")
id2name(3339, db = "ncbi")
id2name(9696, db = "ncbi")
id2name(c(9695, 9696), db = "ncbi")

# WORMS
id2name(105706, db = "worms")

# GBIF
id2name(2441176, db = "gbif")

# BOLD
id2name(88899, db = "bold")
} # }
```
