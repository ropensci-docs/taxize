# Search for taxonomic names using the Global Names Architecture

Uses the Global Names Index, see http://gni.globalnames.org

## Usage

``` r
gna_search(sci, justtotal = FALSE, parse_names = FALSE, ...)
```

## Arguments

- sci:

  (character) required. Name pattern you want to search for. WARNING:
  Does not work for common names. Search term may include following
  options:

  - `n`: A shortcut that allows to put together several elements (e.g.,
    `n:B. bubo Linn. 1750-1800`)

  - `g`: a genus name. (e.g. `g:B.`, `g:Bub.`, `g:Bubo`)

  - `isp`: an infraspecies name (e.g. `sp:bubo`, `sp:gallop.`)

  - `asp`: either species or infraspecies (all sp) (e.g. `asp:bubo`)

  - `ds`: data-sources IDs (e.g., `ds:1,2,3`)

  - `tx`: parent taxon . Uses classification of the first data-source
    from `ds`. If data-sources are not set, uses Catalogue of Life.
    (e.g. `tx:Aves`)

  - `au`: author - Search by author word (e.g. `au:Linnaeus`,
    `au:Linn.`)

  - `y`: year - Search by year (e.g. `y:2005`)

- justtotal:

  Return only the total results found.

- parse_names:

  If `TRUE` use
  [`gni_parse()`](https://docs.ropensci.org/taxize/reference/gni_parse.md)
  on the outputs.

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

data.frame of results.

## References

http://gni.globalnames.org/ https://apidoc.globalnames.org/gnames

## See also

[`gnr_datasources()`](https://docs.ropensci.org/taxize/reference/gnr_datasources.md),
`gna_search()`

## Author

Scott Chamberlain, Zachary Foster

## Examples

``` r
if (FALSE) { # \dontrun{
gna_search('n:B. bubo ds:1,2 au:Linn. y:1700-')
} # }
```
