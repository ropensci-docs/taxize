# Get APG names

Generic names and their replacements from the Angiosperm Phylogeny Group
III system of flowering plant classification.

## Usage

``` r
apgOrders(...)

apgFamilies(...)
```

## Arguments

- ...:

  Curl args passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## References

http://www.mobot.org/MOBOT/research/APweb/

## Examples

``` r
if (FALSE) { # \dontrun{
head(apgOrders())
head(apgFamilies())
} # }
```
