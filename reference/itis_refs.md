# Get references related to a ITIS TSN.

Get references related to a ITIS TSN.

## Usage

``` r
itis_refs(tsn, ...)
```

## Arguments

- tsn:

  One or more TSN's (taxonomic serial number) for a taxonomic group
  (numeric)

- ...:

  Further arguments passed on to getpublicationsfromtsn

## Examples

``` r
if (FALSE) { # \dontrun{
itis_refs(202385)
itis_refs(c(202385, 70340))
} # }
```
