# Get rank for a given taxonomic name.

Get rank for a given taxonomic name.

## Usage

``` r
tax_rank(sci_id, db = NULL, rows = NA, x = NULL, ...)
```

## Arguments

- sci_id:

  (character) Vector of one or more taxon names (character) or IDs
  (character or numeric) to query. Or objects returned from `get_*()`
  functions like
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md)

- db:

  (character) database to query. either `ncbi`, `itis`, `eol`,
  `tropicos`, `gbif`,`nbn`, `worms`, `natserv`, `bold`. Note that each
  taxonomic data source has their own identifiers, so that if you
  provide the wrong `db` value for the identifier you may get a result,
  but it will likely be wrong (not what you were expecting). If using
  ncbi we recommend getting an API key; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- rows:

  numeric; Any number from 1 to infinity. If the default NA, all rows
  are considered. passed down to `get_*()` functions.

- x:

  Deprecated, see `sci_id`

- ...:

  Additional arguments to
  [`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

## Value

A named list of character vectors with ranks (all lower-cased)

## Note

While
[`tax_name()`](https://docs.ropensci.org/taxize/reference/tax_name.md)
returns the name of a specified rank, `tax_rank()` returns the actual
rank of the taxon.

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md),[`tax_name()`](https://docs.ropensci.org/taxize/reference/tax_name.md)

## Examples

``` r
if (FALSE) { # \dontrun{
tax_rank("Helianthus annuus", db = "itis")
tax_rank("Helianthus annuus", db = "natserv")
tax_rank(get_tsn("Helianthus annuus"))
tax_rank(c("Helianthus", "Pinus", "Poa"), db = "itis")

tax_rank(get_boldid("Helianthus annuus"))
tax_rank("421377", db = "bold")
tax_rank(421377, db = "bold")

tax_rank(c("Plantae", "Helianthus annuus",
  "Puma", "Homo sapiens"), db = 'itis')
tax_rank(c("Helianthus annuus", "Quercus", "Fabaceae"), db = 'tropicos')

tax_rank(names_list("species"), db = 'gbif')
tax_rank(names_list("family"), db = 'gbif')

tax_rank(c("Gadus morhua", "Lichenopora neapolitana"),
  db = "worms")
} # }
```
