# Retrieve the upstream taxa for a given taxon name or ID.

This function uses a while loop to continually collect taxa up to the
taxonomic rank that you specify in the `upto` parameter. You can get
data from ITIS (itis) only currently. There is no method exposed by itis
for getting taxa at a specific taxonomic rank, so we do it ourselves
inside the function.

## Usage

``` r
upstream(...)

# Default S3 method
upstream(sci_id, db = NULL, upto = NULL, rows = NA, x = NULL, ...)

# S3 method for class 'tsn'
upstream(sci_id, db = NULL, upto = NULL, ...)

# S3 method for class 'ids'
upstream(sci_id, db = NULL, upto = NULL, ...)
```

## Arguments

- ...:

  Further args passed on to
  [`itis_downstream()`](https://docs.ropensci.org/taxize/reference/itis_downstream.md)

- sci_id:

  Vector of taxa names (character) or IDs (character or numeric) to
  query.

- db:

  character; database to query. One or both of `itis`. Note that each
  taxonomic data source has their own identifiers, so that if you
  provide the wrong `db` value for the identifier you could get a
  result, but it will likely be wrong (not what you were expecting).

- upto:

  What taxonomic rank to go down to. One of: 'superkingdom', 'kingdom',
  'subkingdom','infrakingdom','phylum','division','subphylum',
  'subdivision','infradivision',
  'superclass','class','subclass','infraclass',
  'superorder','order','suborder','infraorder','superfamily','family',
  'subfamily','tribe','subtribe','genus','subgenus',
  'section','subsection',
  'species','subspecies','variety','form','subvariety','race', 'stirp',
  'morph','aberration','subform', or 'unspecified'

- rows:

  (numeric) Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this parameter is ignored if you pass in a
  taxonomic id of any of the acceptable classes: tsn.

- x:

  Deprecated, see `sci_id`

## Value

A named list of data.frames with the upstream names of every supplied
taxa. You get an NA if there was no match in the database.

## Examples

``` r
if (FALSE) { # \dontrun{
upstream('Pinus contorta', db = 'itis', upto = 'genus')
} # }
```
