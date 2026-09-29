# Get The Plant List families.

Get The Plant List families.

## Usage

``` r
tpl_families(...)
```

## Arguments

- ...:

  (list) Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

Returns a `data.frame` including the names of all families indexed by
The Plant List, and the major groups into which they fall (i.e.
Angiosperms, Gymnosperms, Bryophytes and Pteridophytes).

## Details

Requires an internet connection in order to connect to
\<www.theplantlist.org\>.

## See also

[`tpl_get()`](https://docs.ropensci.org/taxize/reference/tpl_get.md)

## Author

John Baumgartner (johnbb@student.unimelb.edu.au)

## Examples

``` r
if (FALSE) { # \dontrun{
# Get a data.frame of plant families, with the group name 
# (Angiosperms, etc.)
head(tpl_families())
} # }
```
