# Search NCBI for children of a taxon

Search the NCBI Taxonomy database for uids of children of taxa. Taxa can
be referenced by name or uid. Referencing by name is faster

In a few cases, different taxa have the same name (e.g. Satyrium; see
examples). If one of these are searched for then the children of both
taxa will be returned. This can be avoided by using a uid instead of the
name or specifying an ancestor. If an ancestor is provided, only
children of both the taxon and its ancestor are returned. This will only
fail if there are two taxa with the same name and the same specified
ancestor.

## Usage

``` r
ncbi_children(
  name = NULL,
  id = NULL,
  start = 0,
  max_return = 1000,
  ancestor = NULL,
  out_type = c("summary", "uid"),
  ambiguous = FALSE,
  key = NULL,
  ...
)
```

## Arguments

- name:

  (`character`) The string to search for. Only exact matches found the
  name given will be returned. Not compatible with `id`.

- id:

  (`character`/`numeric`) The uid to search for. Not compatible with
  `name`.

- start:

  The first record to return. If omitted, the results are returned from
  the first record (start=0).

- max_return:

  (`numeric; length=1`) The maximum number of children to return.

- ancestor:

  (`character`) The ancestor of the taxon being searched for. This is
  useful if there could be more than one taxon with the same name. Has
  no effect if `id` is used.

- out_type:

  (character) Currently either `"summary"` or `"uid"`:

  - `summary` The output is a list of `data.frame` with children uid,
    name, and rank.

  - `uid` A list of character vectors of children uids

- ambiguous:

  `logical; length 1` If `FALSE`, children taxa with words like
  "unclassified", "unknown", "uncultured", or "sp." are removed from the
  output. NOTE: This option only applies when `out_type= "summary"`.

- key:

  (character) NCBI Entrez API key. optional. See Details.

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

The output type depends on the value of the `out_type` parameter. Taxa
that cannot be found will result in `NA`s and a lack of children results
in an empty data structure.

## Authentication

See
[`taxize-authentication()`](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication. We strongly recommend getting an API key

## HTTP version

We hard code `http_version = 2L` to use HTTP/1.1 in HTTP requests to the
Entrez API. See `curl::curl_symbols('CURL_HTTP_VERSION')`

## Rate limits

In case you run into errors due to your rate limit being exceeded, see
[`taxize_options()`](https://docs.ropensci.org/taxize/reference/taxize_options.md),
where you can set `ncbi_sleep`.

## See also

[`ncbi_get_taxon_summary()`](https://docs.ropensci.org/taxize/reference/ncbi_get_taxon_summary.md),
[`children()`](https://docs.ropensci.org/taxize/reference/children.md)

## Author

Zachary Foster <zacharyfoster1989@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ncbi_children(name="Satyrium") #Satyrium is the name of two different genera
ncbi_children(name="Satyrium", ancestor="Eumaeini") # A genus of butterflies
ncbi_children(name="Satyrium", ancestor="Orchidaceae") # A genus of orchids
ncbi_children(id="266948") #"266948" is the uid for the butterfly genus
ncbi_children(id="62858") #"62858" is the uid for the orchid genus

# use curl options
ncbi_children(name="Satyrium", ancestor="Eumaeini", verbose = TRUE)
} # }
```
