# EUBON children

EUBON children

## Usage

``` r
eubon_children(id, providers = NULL, timeout = 0, ...)
```

## Arguments

- id:

  (character) identifier for the taxon. (LSID, DOI, URI, or any other
  identifier used by the checklist provider)

- providers:

  (character) A list of provider id strings concatenated by comma
  characters. The default : "pesi,bgbm-cdm-server\[col\] will be used if
  this parameter is not set. A list of all available provider ids can be
  obtained from the '/capabilities' service end point. Providers can be
  nested, that is a parent provider can have sub providers. If the id of
  the parent provider is supplied all subproviders will be queried. The
  query can also be restricted to one or more subproviders by using the
  following syntax: parent-id\[sub-id-1,sub-id2,...\]

- timeout:

  (numeric) The maximum of milliseconds to wait for responses from any
  of the providers. If the timeout is exceeded the service will just
  return the responses that have been received so far. The default
  timeout is 0 ms (wait for ever)

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

a data.frame or an empty list if no results found

## Note

There is no pagination in this method, so you may or may not be getting
all the results for a search. Sorry, out of our control

## References

https://cybertaxonomy.eu/eu-bon/utis/1.3/doc.html

## See also

Other eubon-methods:
[`eubon_capabilities()`](https://docs.ropensci.org/taxize/reference/eubon_capabilities.md),
[`eubon_hierarchy()`](https://docs.ropensci.org/taxize/reference/eubon_hierarchy.md),
[`eubon_search()`](https://docs.ropensci.org/taxize/reference/eubon_search.md)

## Examples

``` r
if (FALSE) { # \dontrun{
x <- eubon_children(id = "urn:lsid:marinespecies.org:taxname:126141",
  providers = 'worms')
head(x)
} # }
```
