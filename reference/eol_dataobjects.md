# Given the identifier for a data object, return all metadata about the object

Given the identifier for a data object, return all metadata about the
object

## Usage

``` r
eol_dataobjects(id, taxonomy = TRUE, language = NULL, ...)
```

## Arguments

- id:

  (character) The EOL data object identifier

- taxonomy:

  (logical) Whether to return any taxonomy details from different taxon
  hierarchy providers, in an array named `taxonconcepts`

- language:

  (character) provides the results in the specified language. one of ms,
  de, en, es, fr, gl, it, nl, nb, oc, pt-BR, sv, tl, mk, sr, uk, ar,
  zh-Hans, zh-Hant, ko

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

A list, optionally with a data.frame if `taxonomy=TRUE`

## Details

It's possible to return JSON or XML with the EOL API. However, this
function only returns JSON for now.

## Examples

``` r
if (FALSE) { # \dontrun{
eol_dataobjects(id = 7561533)

# curl options
eol_dataobjects(id = 7561533, verbose = TRUE)
} # }
```
