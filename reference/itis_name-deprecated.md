# Get taxonomic names for a given taxonomic name query.

Get taxonomic names for a given taxonomic name query.

## Usage

``` r
itis_name(query = NULL, get = NULL)
```

## Arguments

- query:

  TSN number (taxonomic serial number).

- get:

  The rank of the taxonomic name to get.

## Value

Taxonomic name for the searched taxon.

## Examples

``` r
if (FALSE) { # \dontrun{
itis_name(query="Helianthus annuus", get="family")
} # }
```
