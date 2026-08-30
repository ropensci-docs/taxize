# Get a IUCN Redlist taxon data

Used to get IUCN data for other functions to use.

## Usage

``` r
get_iucn_data(names_or_ids, messages = TRUE, key = NULL, latest = FALSE, ...)
```

## Arguments

- latest:

  If `TRUE`, latest use
  [`rredlist::rl_species_latest()`](https://docs.ropensci.org/rredlist/reference/rl_species_latest.html)
  instead of
  [`rredlist::rl_species()`](https://docs.ropensci.org/rredlist/reference/rl_species.html)
