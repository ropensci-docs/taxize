# Last taxon state object from a `get_*` function call

Last taxon state object from a `get_*` function call

## Usage

``` r
taxon_last()

taxon_clear()
```

## Value

`taxon_last()` returns an object of class `taxon_state`, the last one
used, else `NULL` if none found. `taxon_clear()` clears the saved state

## Details

- `taxon_last()`: get the last `taxon_state` object in use

- `taxon_clear()`: clear any data from last `taxon_state` object

The `taxon_state` object is an R6 object that holds data and methods
used for keeping track of results gathered within a `get_*` function.
You shouldn't create `taxon_state` R6 objects yourself.

Behaviors to be aware of:

- If a `taxon_state` object is not passed you don't need to worry about
  a previously run `get_*` function interfering with another `get_*`
  function call - you have to explicitly pass a `taxon_state` object to
  use `taxon_state`

- The passed in `taxon_state` object must have a `$class` matching that
  of the `get_*` function being called. For example, you can only pass a
  `taxon_state` with `$class` of `gbifid` to
  [`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
  and so on.

- If you run `taxon_clear()` while a `get*` function is running, you may
  lose track of any state known to this package before it was cleared

See the internal method
[progressor](https://docs.ropensci.org/taxize/reference/progressor.md)
for information on how we control messages in `get*` functions

## Examples

``` r
if (FALSE) { # \dontrun{
spp <- names_list("species", 3)
res <- get_gbifid(spp)
z <- taxon_last()
z
z$taxa_remaining()
z$taxa_completed()
z$count # active binding; no parens needed

# cleanup
taxon_clear()
} # }
```
