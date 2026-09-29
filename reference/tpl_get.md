# Get The Plant List csv files.

Get The Plant List csv files.

## Usage

``` r
tpl_get(x, family = NULL, ...)
```

## Arguments

- x:

  Directory to write csv files to.

- family:

  If you want just one, or \>1 family, but not all, list them in a
  vector.

- ...:

  (list) Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

Returns nothing to console, except a message and progress bar. Writes
csv files to x.

## Details

Throws a warning if you already have a directory of the one provided,
but still works. Writes to your home directory, change x as needed.

## References

The Plant List http://www.theplantlist.org

## See also

[`tpl_families()`](https://docs.ropensci.org/taxize/reference/tpl_families.md)

## Author

John Baumgartner <johnbb@student.unimelb.edu.au>

## Examples

``` r
if (FALSE) { # \dontrun{
# Get a few families
dir <- file.path(tempdir(), "abc")
tpl_get(dir, family = c("Platanaceae","Winteraceae"))
readLines(file.path(dir, "Platanaceae.csv"), n = 5)

# You can now get Gymnosperms as well
dir1 <- file.path(tempdir(), "def")
tpl_get(dir1, family = c("Pinaceae","Taxaceae"))

# You can get mosses too!
dir2 <- file.path(tempdir(), "ghi")
tpl_get(dir2, family = "Echinodiaceae")

# Get all families
## Beware, will take a while
## dir3 <- file.path(tempdir(), "jkl")
## tpl_get("dir3)
} # }
```
