# Get full ITIS record for one or more ITIS TSN's or lsid's.

Get full ITIS record for one or more ITIS TSN's or lsid's.

## Usage

``` r
itis_getrecord(values, by = "tsn", ...)
```

## Arguments

- values:

  (character) One or more TSN's (taxonomic serial number) or lsid's for
  a taxonomic group

- by:

  (character) By "tsn" (default) or "lsid"

- ...:

  Further arguments passed on to
  [ritis::full_record](https://docs.ropensci.org/ritis/reference/full_record.html)

## Details

You can only enter values in tsn parameter or lsid, not both.

## Examples

``` r
if (FALSE) { # \dontrun{
# by TSN
itis_getrecord(202385)
itis_getrecord(c(202385,70340))

# by lsid
itis_getrecord("urn:lsid:itis.gov:itis_tsn:202385", "lsid")
} # }
```
