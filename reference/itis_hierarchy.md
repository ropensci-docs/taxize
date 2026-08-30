# ITIS hierarchy

Get hierarchies from TSN values, full, upstream only, or immediate
downstream only

## Usage

``` r
itis_hierarchy(tsn, what = "full", ...)
```

## Arguments

- tsn:

  One or more TSN's (taxonomic serial number). Required.

- what:

  One of full (full hierarchy), up (immediate upstream), or down
  (immediate downstream)

- ...:

  Further arguments passed on to
  [`ritis::hierarchy_full()`](https://docs.ropensci.org/ritis/reference/hierarchy.html)
  [`ritis::hierarchy_up()`](https://docs.ropensci.org/ritis/reference/hierarchy.html)
  or
  [`ritis::hierarchy_down()`](https://docs.ropensci.org/ritis/reference/hierarchy.html)

## Details

Note that
[`itis_downstream()`](https://docs.ropensci.org/taxize/reference/itis_downstream.md)
gets taxa downstream to a particular rank, while this function only gets
immediate names downstream.

## See also

[`itis_downstream()`](https://docs.ropensci.org/taxize/reference/itis_downstream.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Get full hierarchy
itis_hierarchy(tsn=180543)

# Get hierarchy upstream
itis_hierarchy(tsn=180543, "up")

# Get hierarchy downstream
itis_hierarchy(tsn=180543, "down")

# Many tsn's
itis_hierarchy(tsn=c(180543,41074,36616))
} # }
```
