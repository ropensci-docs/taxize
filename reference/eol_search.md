# Search for terms in EOL database.

Search for terms in EOL database.

## Usage

``` r
eol_search(
  sci,
  page = 1,
  exact = NULL,
  filter_tid = NULL,
  filter_heid = NULL,
  filter_by_string = NULL,
  cache_ttl = NULL,
  terms = NULL,
  ...
)
```

## Arguments

- sci:

  (character) scientific name

- page:

  A maximum of 30 results are returned per page. This parameter allows
  you to fetch more pages of results if there are more than 30 matches
  (Default 1)

- exact:

  Will find taxon pages if the preferred name or any synonym or common
  name exactly matches the search term.

- filter_tid:

  Given an EOL page ID, search results will be limited to members of
  that taxonomic group

- filter_heid:

  Given a Hierarchy Entry ID, search results will be limited to members
  of that taxonomic group

- filter_by_string:

  Given a search term, an exact search will be made and that matching
  page will be used as the taxonomic group against which to filter
  search results

- cache_ttl:

  The number of seconds you wish to have the response cached.

- terms:

  Deprecated, see `sci`

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

A data frame with four columns:

- pageid: pageid, this is the same as the eolid you can get from
  [`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md)

- name: taxonomic name, may or may not contain the taxonomic authority

- link: URL for the taxon in question

- content: a string of semi-colon separated names. it's not clear to us
  what these represent exactly, but figured why not give it to users in
  case some may find it useful

## Details

It's possible to return JSON or XML with the EOL API. However, this
function only returns JSON for now.

## Examples

``` r
if (FALSE) { # \dontrun{
eol_search(sci='Homo')
eol_search(sci='Salix', verbose = TRUE)
eol_search(sci='Ursus americanus')
eol_search('Pinus contorta')
} # }
```
