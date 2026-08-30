# NCBI taxon information from uids

Downloads summary taxon information from the NCBI taxonomy databases for
a set of taxonomy UIDs using eutils esummary.

## Usage

``` r
ncbi_get_taxon_summary(id, key = NULL, ...)
```

## Arguments

- id:

  (character) NCBI taxonomy uids to retrieve information for. See
  Details.

- key:

  (character) NCBI Entrez API key. optional. See Details.

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

A `data.frame` with the following columns:

- `uid` The uid queried for

- `name` The name of the taxon; a binomial name if the taxon is of rank
  species

- `rank` The taxonomic rank (e.g. 'Genus')

## Details

If your input vector or list of NCBI IDs is longer than about 2500
characters (use `nchar(paste(ids, collapse = "+"))`), split the list up
into chunks since at about that number of characters you will run into
the HTTP 414 error "Request-URI Too Long".

## HTTP version

We hard code `http_version = 2L` to use HTTP/1.1 in HTTP requests to the
Entrez API. See `curl::curl_symbols('CURL_HTTP_VERSION')`

## Authentication

See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication. We strongly recommend getting an API key

## Author

Zachary Foster <zacharyfoster1989@Sgmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ncbi_get_taxon_summary(c(1430660, 4751))

# use curl options
ncbi_get_taxon_summary(c(1430660, 4751), verbose = TRUE)
} # }
```
