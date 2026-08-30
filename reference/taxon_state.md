# Keep track of queries in `get_*` functions

Keep track of queries in `get_*` functions

Keep track of queries in `get_*` functions

## Details

This object lives inside each `get_*` function call, maintaining results
as they are accumulated.

## Public fields

- `initialized`:

  (time) time job started

- `finalized`:

  (time) time job finished

- `class`:

  (character) a class name (e.g., "gbif")

- `names`:

  (character) one or more taxon names

## Active bindings

- `count`:

  (integer) count number of records

- `exit`:

  record date/time function exited

## Methods

### Public methods

- [`taxon_state$new()`](#method-taxon_state-new)

- [`taxon_state$print()`](#method-taxon_state-print)

- [`taxon_state$add()`](#method-taxon_state-add)

- [`taxon_state$get()`](#method-taxon_state-get)

- [`taxon_state$remove()`](#method-taxon_state-remove)

- [`taxon_state$purge()`](#method-taxon_state-purge)

- [`taxon_state$taxa_remaining()`](#method-taxon_state-taxa_remaining)

- [`taxon_state$taxa_completed()`](#method-taxon_state-taxa_completed)

- [`taxon_state$clone()`](#method-taxon_state-clone)

------------------------------------------------------------------------

### Method `new()`

Create a new `taxon_state` object

#### Usage

    taxon_state$new(class, names)

#### Arguments

- `class`:

  (character) a class name (e.g., "gbif")

- `names`:

  (character) one or more taxon names

#### Returns

A new `taxon_state` object

------------------------------------------------------------------------

### Method [`print()`](https://rdrr.io/r/base/print.html)

print method for the `taxon_state` class

#### Usage

    taxon_state$print(x, ...)

#### Arguments

- `x`:

  self

- `...`:

  ignored

------------------------------------------------------------------------

### Method `add()`

add a record with it's result; duplicates allowed

#### Usage

    taxon_state$add(query, result)

#### Arguments

- `query`:

  (character), a taxon name

- `result`:

  (list) a named list

#### Returns

nothing returned; sets only

------------------------------------------------------------------------

### Method [`get()`](https://rdrr.io/r/base/get.html)

get all records matching 'query'

#### Usage

    taxon_state$get(query = NULL)

#### Arguments

- `query`:

  (character), a taxon name

#### Returns

a named list, with slots for the taxon id, and other attributes, named
by the taxon name

------------------------------------------------------------------------

### Method [`remove()`](https://rdrr.io/r/base/rm.html)

remove's all records matching 'query'

#### Usage

    taxon_state$remove(query)

#### Arguments

- `query`:

  (character), a taxon name

#### Returns

nothing, removes records matching query

------------------------------------------------------------------------

### Method `purge()`

removes all records

#### Usage

    taxon_state$purge()

#### Returns

nothing returned; sets only

------------------------------------------------------------------------

### Method `taxa_remaining()`

get remaining taxa

#### Usage

    taxon_state$taxa_remaining()

#### Returns

sorted taxon names

------------------------------------------------------------------------

### Method `taxa_completed()`

get completed taxa

#### Usage

    taxon_state$taxa_completed()

#### Returns

sorted taxon names

------------------------------------------------------------------------

### Method `clone()`

The objects of this class are cloneable with this method.

#### Usage

    taxon_state$clone(deep = FALSE)

#### Arguments

- `deep`:

  Whether to make a deep clone.

## Examples

``` r
if (FALSE) { # \dontrun{
if (interactive()) {
ts <- taxon_state$new()
taxon_last()
ts
res <- list(
  id = 123456,
  att = "found",
  multiple = FALSE,
  direct = FALSE,
  class = "tsn"
)
ts$add(query = "Quercus robur", result = res)
ts
ts$get(query = "Quercus robur")
ts$count
ts$remove(query = "Quercus robur")
ts
ts$count

res2 <- list(
  id = 3430834535,
  att = "found",
  multiple = FALSE,
  direct = FALSE,
  class = "gbifid"
)
ts$add(query = "Poa annua", result = res2)
res3 <- list(
  id = 1223424,
  att = "found",
  multiple = FALSE,
  direct = FALSE,
  class = "uid"
)
ts$add(query = "Puma concolor", result = res3)
ts
ts$count
ts$get("Puma concolor")
ts$get()

# cleanup
ts$purge()
ts$count
}
} # }
```
