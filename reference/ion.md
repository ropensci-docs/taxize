# ION - Index to Organism Names

ION - Index to Organism Names

## Usage

``` r
ion(x, ...)
```

## Arguments

- x:

  An LSID number. Required.

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

A data.frame

## References

http://www.organismnames.com

## Examples

``` r
if (FALSE) { # \dontrun{
ion(155166)
ion(298678)
ion(4796748) # ursus americanus
ion(1280626) # puma concolor
} # }
```
