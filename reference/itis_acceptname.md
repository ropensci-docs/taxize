# Retrieve accepted TSN and name

Retrieve accepted TSN and name

## Usage

``` r
itis_acceptname(searchtsn, ...)
```

## Arguments

- searchtsn:

  One or more TSN for a taxon (numeric/integer)

- ...:

  Curl options passed on
  to[crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

data.frame with with row number equal to input vector length, and with
three columns:

- submittedtsn (numeric) - The submitted TSN

- acceptedname (character) - The accepted name - if the submitted TSN is
  the accepted TSN, then this is `NA_character_` because ITIS does not
  return a name along with the TSN if it's an accepted name. We could
  make an extra HTTP request to ITIS, but that means additional time.

- acceptedtsn (numeric) - The accepted TSN

- author (character) - taxonomic authority

## Examples

``` r
if (FALSE) { # \dontrun{
# TSN accepted - good name
itis_acceptname(searchtsn = 208527)

# TSN not accepted - input TSN is old
itis_acceptname(searchtsn = 504239)

# many accepted names
ids <- c(18161, 18162, 18163, 18164, 18165, 18166, 46173, 46174,
46178, 46181, 46186, 46193, 46196, 46197, 46200, 46201, 46204,
46207, 46867, 46868)
itis_acceptname(searchtsn = ids)

# many unaccepted names
ids <- c(39087, 46208, 46973, 46976, 46978, 46980, 47295, 47445,
47448, 47512, 47515, 47527, 47546, 47622, 47783, 47786, 47787,
47788, 47835, 47839)
itis_acceptname(searchtsn = ids)

# many: mix of accepted and unaccepted names
ids <- c(18161, 18162, 47527, 47546, 47622, 46200)
itis_acceptname(searchtsn = ids)
} # }
```
