# Print a subset of a character vector

Prints the start and end values for a character vector. The number of
values printed depend on the width of the screen by default.

## Usage

``` r
limited_print(
  chars,
  prefix = "",
  max_chars = getOption("width") - nchar(prefix) - 5,
  type = "message"
)
```

## Arguments

- chars:

  (`character`) What to print.

- prefix:

  (`character` of length 1) What to print before `chars`, on the same
  line.

- max_chars:

  (`numeric` of length 1) The maximum number of characters to print.

- type:

  (`"error"`, `"warning"`, `"message"`, `"cat"`, `"print"`, `"silent"`)

## Value

`NULL`
