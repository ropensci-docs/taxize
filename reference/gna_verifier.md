# Verify a list of scientific names against biodiversity data-sources.

This service parses incoming names, executes exact or fuzzy matching as
required, and returns the best-scored result. Optionally, it can also
return matches from data-sources selected by a user.

## Usage

``` r
gna_verifier(
  names,
  data_sources = c(1, 12),
  all_matches = FALSE,
  capitalize = FALSE,
  species_group = FALSE,
  fuzzy_uninomial = FALSE,
  stats = FALSE,
  main_taxon_threshold = 0.5,
  output_type = "table",
  ...
)
```

## Arguments

- names:

  A `character` vector of taxon names to verify.

- data_sources:

  A `character` or `integer` vector with numbers corresponding to data
  sources. See the Global Names Architecture documentation for a list of
  available options.

- all_matches:

  When `TRUE`, return all found matches, not only the best one. Multiple
  results are returned in results. These results are sorted by matching
  quality, the first result is the same as bestResult.

- capitalize:

  When `TRUE`, capitalize the first letter of a name-string.

- species_group:

  When `TRUE`, expands the search to species group where applicable.

- fuzzy_uninomial:

  When `TRUE`, allows fuzzy matching for uninomial names.

- stats:

  When `TRUE`, finds out a kingdom and a taxon (main taxon) that contain
  most names. It only takes in account the names matched to the
  Catalogue of Life entries. This option is ignored, if the Catalogue of
  Life is not included in data-sources.

- main_taxon_threshold:

  A `numeric` vector from 0.5 to 1. This sets the minimal percentage for
  the main taxon discovery.

- output_type:

  A `character` vector of length 1, either `table` or `list`, indicating
  the format of the output. The tabular output only contains values that
  consistently appear in all results, so `list` output can have
  additional information. For `list` and `json` outputs, only values for
  unique taxon names are returned, but the `table` output has rows that
  correspond 1-1 with the input data.

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

Depends on the value of the `output_type` option

## Author

Zachary S.L. Foster

## Examples

``` r
if (FALSE) { # \dontrun{
gna_verifier(c("Helianthus annuus", "Homo saapiens"))
gna_verifier(c("Helianthus annuus", "Homo saapiens"), all_matches = TRUE)
} # }
```
