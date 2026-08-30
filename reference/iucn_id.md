# Get an ID for a IUCN listed taxon

Get an ID for a IUCN listed taxon

## Usage

``` r
iucn_id(sciname, key = NULL, ...)
```

## Arguments

- sciname:

  character; Scientific name. Should be cleaned and in the format
  `*<Genus> <Species>*`. One or more.

- key:

  (character) required. you IUCN Redlist API key. See
  [rredlist::rredlist-package](https://docs.ropensci.org/rredlist/reference/rredlist-package.html)
  for help on authenticating with IUCN Redlist

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

A named list (names are input taxa names) of one or more IUCN IDs. Taxa
that aren't found are silently dropped.

## Author

Scott Chamberlain,

## Examples

``` r
if (FALSE) { # \dontrun{
iucn_id("Branta canadensis")
iucn_id("Branta bernicla")
iucn_id("Panthera uncia")
iucn_id("Lynx lynx")

# many names
iucn_id(c("Panthera uncia", "Lynx lynx"))

# many names, some not found
iucn_id(c("Panthera uncia", "Lynx lynx", "foo bar", "Gorilla gorilla gorilla"))

# a name not found
iucn_id("Foo bar")
} # }
```
