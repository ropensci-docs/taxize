# Get jurisdiction data, i.e., native or not native in a region.

Get jurisdiction data, i.e., native or not native in a region.

## Usage

``` r
itis_native(tsn = NULL, what = "bytsn", ...)
```

## Arguments

- tsn:

  One or more TSN's (taxonomic serial number)

- what:

  One of bytsn, values, or originvalues

- ...:

  Further arguments passed on to
  [`ritis::jurisdictional_origin()`](https://docs.ropensci.org/ritis/reference/jurisdiction.html),
  [`ritis::jurisdiction_values()`](https://docs.ropensci.org/ritis/reference/jurisdiction.html),
  or
  [`ritis::jurisdiction_origin_values()`](https://docs.ropensci.org/ritis/reference/jurisdiction.html)

## Examples

``` r
if (FALSE) { # \dontrun{
# Get values
itis_native(what="values")

# Get origin values
itis_native(what="originvalues")

# Get values by tsn
itis_native(tsn=180543)
itis_native(tsn=c(180543,41074,36616))
} # }
```
