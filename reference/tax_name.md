# Get taxonomic names for a given rank

Get taxonomic names for a given rank

## Usage

``` r
tax_name(
  sci,
  get,
  db = "itis",
  pref = "ncbi",
  messages = TRUE,
  query = NULL,
  ...
)
```

## Arguments

- sci:

  (character) Vector of taxonomic names to query. required.

- get:

  (character) The ranks of the taxonomic name to get, see
  [rank_ref](https://docs.ropensci.org/taxize/reference/rank_ref.md).
  required.

- db:

  (character) The database to search from: 'itis', 'ncbi' or 'both'. If
  'both' both NCBI and ITIS will be queried. Result will be the union of
  both. If using ncbi, we recommend getting an API key; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- pref:

  (character) If db = 'both', sets the preference for the union. Either
  'ncbi' (default) or 'itis'. Currently not implemented.

- messages:

  (logical) If `TRUE` the actual taxon queried is printed on the
  console.

- query:

  Deprecated, see `sci`

- ...:

  Other arguments passed to
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md)
  or
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md).

## Value

A data.frame with one column for every queried rank, in addition to a
column for db and queried term.

## Note

While
[`tax_rank()`](https://docs.ropensci.org/taxize/reference/tax_rank.md)
returns the actual rank of a taxon, `tax_name()` searches and returns
any specified rank higher in taxonomy.

## Authentication

See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for help on authentication

## See also

[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# A case where itis and ncbi use the same names
tax_name(sci = "Helianthus annuus", get = "family", db = "itis")
tax_name(sci = "Helianthus annuus", get = "family", db = "ncbi")
tax_name(sci = "Helianthus annuus", get = c("genus","family","order"),
  db = "ncbi")

# Case where itis and ncbi use different names
tax_name(sci = "Helianthus annuus", get = "kingdom", db = "itis")
tax_name(sci = "Helianthus annuus", get = "kingdom", db = "ncbi")

# multiple rank arguments
tax_name(sci = c("Helianthus annuus","Baetis rhodani"), get = c("genus",
"kingdom"), db = "ncbi")
tax_name(sci = c("Helianthus annuus","Baetis rhodani"), get = c("genus",
"kingdom"), db = "itis")

# query both sources
tax_name(sci=c("Helianthus annuus", 'Baetis rhodani'), get=c("genus",
"kingdom"), db="both")
} # }
```
