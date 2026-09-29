# methods for preparing/printing info for prompts for `get_*` functions

methods for preparing/printing info for prompts for `get_*` functions

methods for preparing/printing info for prompts for `get_*` functions

## Public fields

- `total`:

  (integer) x

- `found`:

  (integer) list of results when name found

- `not_found`:

  (integer) list of results when name not found

- `done`:

  (integer) x

- `suppress`:

  (integer) x

## Active bindings

- `p`:

  (integer) percent done

- `d`:

  (integer) number done

## Methods

### Public methods

- [`progressor$new()`](#method-progressor-new)

- [`progressor$completed()`](#method-progressor-completed)

- [`progressor$completed_found()`](#method-progressor-completed_found)

- [`progressor$completed_not_found()`](#method-progressor-completed_not_found)

- [`progressor$prog_start()`](#method-progressor-prog_start)

- [`progressor$prog()`](#method-progressor-prog)

- [`progressor$prog_found()`](#method-progressor-prog_found)

- [`progressor$prog_not_found()`](#method-progressor-prog_not_found)

- [`progressor$prog_summary()`](#method-progressor-prog_summary)

- [`progressor$clone()`](#method-progressor-clone)

------------------------------------------------------------------------

### Method `new()`

Create a new `progressor` object

#### Usage

    progressor$new(items, suppress = FALSE)

#### Arguments

- `items`:

  (character) xxx

- `suppress`:

  (logical) suppress messages. default: `FALSE`

#### Returns

A new `progressor` object

------------------------------------------------------------------------

### Method `completed()`

add results to found or not found

#### Usage

    progressor$completed(name, att)

#### Arguments

- `name`:

  (character) vector of names

- `att`:

  (character) one of "found" or "not found"

#### Returns

nothing returned; adds to `$found` or `$not_found`

------------------------------------------------------------------------

### Method `completed_found()`

add to found results

#### Usage

    progressor$completed_found(name)

#### Arguments

- `name`:

  (character) vector of taxon names

#### Returns

nothing returned; adds to `$found`

------------------------------------------------------------------------

### Method `completed_not_found()`

add to not found results

#### Usage

    progressor$completed_not_found(name)

#### Arguments

- `name`:

  (character) vector of taxon names

#### Returns

nothing returned; adds to `$not_found`

------------------------------------------------------------------------

### Method `prog_start()`

print messages of total queries to do, and percent completed

#### Usage

    progressor$prog_start()

------------------------------------------------------------------------

### Method `prog()`

prints message of found or not found using packages cli and crayon

#### Usage

    progressor$prog(att)

#### Arguments

- `att`:

  (character) one of "found" or "not found"

#### Returns

messages

------------------------------------------------------------------------

### Method `prog_found()`

prints found message using packages cli and crayon

#### Usage

    progressor$prog_found()

#### Returns

messages

------------------------------------------------------------------------

### Method `prog_not_found()`

prints not found message using packages cli and crayon

#### Usage

    progressor$prog_not_found()

#### Returns

messages

------------------------------------------------------------------------

### Method `prog_summary()`

prints summary at end of result with total found and not found

#### Usage

    progressor$prog_summary()

#### Returns

messages

------------------------------------------------------------------------

### Method `clone()`

The objects of this class are cloneable with this method.

#### Usage

    progressor$clone(deep = FALSE)

#### Arguments

- `deep`:

  Whether to make a deep clone.

## Examples

``` r
if (FALSE) { # \dontrun{
# nms <- c("Quercus", "Sasdsfasdf")
# x <- progressor$new(items = nms)
# x
# x$prog_start()

# x$completed(nms[1], "found")
# x$prog_found()

# x$completed(nms[2], "not found")
# x$prog_not_found()

# x$prog_summary()

# suppress cli::cat_line
# x <- progressor$new(items = nms, suppress = TRUE)
# x$prog_summary()
} # }
```
