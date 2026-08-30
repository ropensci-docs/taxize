# Retrieve immediate children taxa for a given taxon name or ID.

This function is different from
[`downstream()`](https://docs.ropensci.org/taxize/reference/downstream.md)
in that it only collects immediate taxonomic children, while
[`downstream()`](https://docs.ropensci.org/taxize/reference/downstream.md)
collects taxonomic names down to a specified taxonomic rank, e.g.,
getting all species in a family.

## Usage

``` r
children(...)

# Default S3 method
children(sci_id, db = NULL, rows = NA, x = NULL, ...)

# S3 method for class 'tsn'
children(sci_id, db = NULL, ...)

# S3 method for class 'wormsid'
children(sci_id, db = NULL, ...)

# S3 method for class 'ids'
children(sci_id, db = NULL, ...)

# S3 method for class 'uid'
children(sci_id, db = NULL, ...)

# S3 method for class 'boldid'
children(sci_id, db = NULL, ...)
```

## Arguments

- ...:

  Further args passed on to
  [`ritis::hierarchy_down()`](https://docs.ropensci.org/ritis/reference/hierarchy.html),
  [`ncbi_children()`](https://docs.ropensci.org/taxize/reference/ncbi_children.md),
  [`worrms::wm_children()`](https://docs.ropensci.org/worrms/reference/wm_children.html),
  [`bold_children()`](https://docs.ropensci.org/taxize/reference/bold_children.md)
  See those functions for what parameters can be passed on.

- sci_id:

  Vector of taxa names (character) or IDs (character or numeric) to
  query.

- db:

  character; database to query. One or more of `itis`, `ncbi`, `worms`,
  or `bold`. Note that each taxonomic data source has their own
  identifiers, so that if you provide the wrong `db` value for the
  identifier you could get a result, but it will likely be wrong (not
  what you were expecting). If using ncbi, we recommend getting an API
  key; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- rows:

  (numeric) Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this parameter is ignored if you pass in a
  taxonomic id of any of the acceptable classes: tsn. NCBI has a method
  for this function but rows doesn't work.

- x:

  Deprecated, see `sci_id`

## Value

A named list of data.frames with the children names of every supplied
taxa. You get an NA if there was no match in the database.

## ncbi

note that with `db = "ncbi"`, we set `ambiguous = TRUE`; that is,
children taxa with words like "unclassified", "unknown", "uncultured",
"sp." are NOT removed

## bold

BEWARE: `db="bold"` scrapes the BOLD website, so may be unstable. That
is, one day it may work, and the next it may fail. Open an issue if you
encounter an error: https://github.com/ropensci/taxize/issues

## Examples

``` r
if (FALSE) { # \dontrun{
# Plug in taxonomic IDs
children(161994, db = "itis")
children(8028, db = "ncbi")
## works with numeric if as character as well
children(161994, db = "itis")
children(88899, db = "bold")
children(as.boldid(88899))

# Plug in taxon names
children("Salmo", db = 'itis')
children("Salmo", db = 'ncbi')
children("Salmo", db = 'worms')
children("Salmo", db = 'bold')

# Plug in IDs
(id <- get_wormsid("Gadus"))
children(id)

# Many taxa
sp <- c("Tragia", "Schistocarpha", "Encalypta")
children(sp, db = 'itis')

# Two data sources
(ids <- get_ids("Apis", db = c('ncbi','itis')))
children(ids)
## same result
children(get_ids("Apis", db = c('ncbi','itis')))

# Use the rows parameter
children("Poa", db = 'itis')
children("Poa", db = 'itis', rows=1)

# use curl options
res <- children("Poa", db = 'itis', rows=1, verbose = TRUE)
} # }
```
