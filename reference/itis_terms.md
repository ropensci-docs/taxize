# Get ITIS terms, i.e., tsn's, authors, common names, and scientific names.

Get ITIS terms, i.e., tsn's, authors, common names, and scientific
names.

## Usage

``` r
itis_terms(query, what = "both", ...)
```

## Arguments

- query:

  One or more common or scientific names, or partial names

- what:

  One of both (search common and scientific names), common (search just
  common names), or scientific (search just scientific names)

- ...:

  Further arguments passed on to
  [`ritis::terms()`](https://docs.ropensci.org/ritis/reference/terms.html)

## Examples

``` r
if (FALSE) { # \dontrun{
# Get terms searching both common and scientific names
itis_terms(query='bear')

# Get terms searching just common names
itis_terms(query='tarweed', "common")

# Get terms searching just scientific names
itis_terms(query='Poa annua', "scientific")
} # }
```
