# Get NCBI taxonomy UID from GenBankID

Get NCBI taxonomy UID from GenBankID

## Usage

``` r
genbank2uid(id, batch_size = 100, key = NULL, ...)
```

## Arguments

- id:

  A GenBank accession alphanumeric string, or a gi numeric string.

- batch_size:

  The number of queries to submit at a time.

- key:

  (character) NCBI Entrez API key. optional. See Details.

- ...:

  Curl args passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

one or more NCBI taxonomic IDs

## Details

See https://www.ncbi.nlm.nih.gov/Sitemap/sequenceIDs.html for help on
why there are two identifiers, and the difference between them.

## Authentication

See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication. We recommend getting an API key.

## HTTP version

We hard code `http_version = 2L` to use HTTP/1.1 in HTTP requests to the
Entrez API. See `curl::curl_symbols('CURL_HTTP_VERSION')`

## Rate limits

In case you run into errors due to your rate limit being exceeded, see
[`taxize_options()`](https://docs.ropensci.org/taxize/reference/taxize_options.md),
where you can set `ncbi_sleep`.

## Examples

``` r
if (FALSE) { # \dontrun{
# with accession numbers
genbank2uid(id = 'AJ748748')
genbank2uid(id = 'Y13155')
genbank2uid(id = 'X78312')
genbank2uid(id = 'KM495596')

# with gi numbers
genbank2uid(id = 62689767)
genbank2uid(id = 22775511)
genbank2uid(id = 156446673)

# pass in many accession or gi numbers
genbank2uid(c(62689767,156446673))
genbank2uid(c('X78312','KM495596'))
genbank2uid(list('X78312',156446673))

# curl options
res <- genbank2uid(id = 156446673, verbose = TRUE)
} # }
```
