# Get metadata about GNA data sources

Downloads metadata about Global Names Architecture (GNA) data sources
available to be used in other GNA functions.

## Usage

``` r
gna_data_sources(output_type = "table", ...)
```

## Arguments

- output_type:

  What format of output to return. Either `'json'`, `'list'`, or
  `'table'`.

- ...:

  Passed to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html).

## Author

Zachary S.L. Foster

## Examples

``` r
if (FALSE) { # \dontrun{

gna_data_sources()
} # }
```
