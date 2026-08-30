# Get TSN from LSID

Get TSN from LSID

## Usage

``` r
itis_lsid(lsid = NULL, what = "tsn", ...)
```

## Arguments

- lsid:

  One or more lsid's

- what:

  What to retrieve. One of tsn, record, or fullrecord

- ...:

  Further arguments passed on to
  [`ritis::lsid2tsn()`](https://docs.ropensci.org/ritis/reference/lsid2tsn.html),
  [`ritis::record()`](https://docs.ropensci.org/ritis/reference/record.html),
  or
  [`ritis::full_record()`](https://docs.ropensci.org/ritis/reference/full_record.html)

## Examples

``` r
if (FALSE) { # \dontrun{
# Get TSN
itis_lsid("urn:lsid:itis.gov:itis_tsn:180543")
itis_lsid(lsid=c("urn:lsid:itis.gov:itis_tsn:180543","urn:lsid:itis.gov:itis_tsn:28726"))

# Get partial record
itis_lsid("urn:lsid:itis.gov:itis_tsn:180543", "record")

# Get full record
itis_lsid("urn:lsid:itis.gov:itis_tsn:180543", "fullrecord")

# An invalid lsid (a tsn actually)
itis_lsid(202385)
} # }
```
