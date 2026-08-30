# Lookup in the APGIII taxonomy and replace family names

Lookup in the APGIII taxonomy and replace family names

## Usage

``` r
apg_lookup(taxa, rank = "family")
```

## Arguments

- taxa:

  (character) Taxonomic name to lookup a synonym for in APGIII taxonomy.

- rank:

  (character) Taxonomic rank to lookup a synonym for. One of family or
  order.

## Value

A APGIII family or order name, the original name if the name is the same
as APG has, or NA if no match found

## Details

Internally in this function, we use the datasets
[apg_families](https://docs.ropensci.org/taxize/reference/apg_families.md)
and
[apg_orders](https://docs.ropensci.org/taxize/reference/apg_orders.md) -
see their descriptions for the data in them. The functions
[`apgOrders()`](https://docs.ropensci.org/taxize/reference/apg.md)
[`apgFamilies()`](https://docs.ropensci.org/taxize/reference/apg.md) are
for scraping current content from the
http://www.mobot.org/MOBOT/research/APweb/ website

The datasets used in this function are from the most recent version of
APGIII, Version 14 (http://www.mobot.org/MOBOT/research/APweb/)

## Examples

``` r
# New name found
apg_lookup(taxa = "Hyacinthaceae", rank = "family")
#> new name...
#> [1] "Asparagaceae"
# Name is the same
apg_lookup(taxa = "Poaceae", rank = "family")
#> name is the same...
#> [1] "Poaceae"
apg_lookup(taxa = "Asteraceae", rank = "family")
#> name is the same...
#> [1] "Asteraceae"
# Name not found
apg_lookup(taxa = "Foobar", rank = "family")
#> no match found...
#> [1] NA

# New name found
apg_lookup(taxa = "Acerales", rank = "order")
#> new name...
#> [1] "Sapindales"
# Name is the same
apg_lookup(taxa = "Acorales", rank = "order")
#> name is the same...
#> [1] "Acorales"
# Name not found
apg_lookup(taxa = "Foobar", rank = "order")
#> no match found...
#> [1] NA
```
