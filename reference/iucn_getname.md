# Get any matching IUCN species names

Get any matching IUCN species names

## Usage

``` r
iucn_getname(name, verbose = TRUE, ...)
```

## Arguments

- name:

  character; taxon name

- verbose:

  logical; should messages be printed?

- ...:

  Further arguments passed on to
  [`iucn_summary()`](https://docs.ropensci.org/taxize/reference/iucn_summary.md),
  note that you'll need an API key.

## Value

Character vector of names that matched in IUCN

## Details

Beware: IUCN functions can give back incorrect data. This isn't our
fault. We do our best to get you the correct data quickly, but sometimes
IUCN gives back the wrong data, and sometimes Global Names gives back
the wrong data. We will fix these as soon as possible. In the meantime,
just make sure that the data you get back is correct.

## See also

[`iucn_summary()`](https://docs.ropensci.org/taxize/reference/iucn_summary.md)
[`iucn_status()`](https://docs.ropensci.org/taxize/reference/iucn_status.md)

## Examples

``` r
if (FALSE) { # \dontrun{
iucn_getname(name = "Cyanistes caeruleus")
iucn_getname(name = "Panthera uncia")

# not found in IUCN search
iucn_getname(name = "Acacia allenii")
} # }
```
