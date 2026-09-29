# Global Names Resolver Data Sources

Retrieve data sources used in the Global Names Resolver

## Usage

``` r
gnr_datasources(..., todf)
```

## Arguments

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

- todf:

  defunct, always get a data.frame back now

## Value

data.frame/tibble

## References

https://resolver.globalnames.org/data_sources

## See also

[`gnr_resolve()`](https://docs.ropensci.org/taxize/reference/gnr_resolve.md),
[`gna_search()`](https://docs.ropensci.org/taxize/reference/gna_search.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# all data sources
gnr_datasources()

# give me the id for EOL
out <- gnr_datasources()
out[out$title == "EOL", "id"]

# Fuzzy search for sources with the word zoo
out <- gnr_datasources()
out[agrep("zoo", out$title, ignore.case = TRUE), ]
} # }
```
