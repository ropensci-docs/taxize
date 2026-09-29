# Function to get API key.

Checks first to get key from your .Rprofile or .Renviron (or similar)
file

## Usage

``` r
getkey(x = NULL, service)
```

## Arguments

- x:

  (character) An API key, defaults to `NULL`

- service:

  (character) The API data provider, used to match to default guest key
  (for Tropicos; there's no guest key for NCBI or IUCN, for which you
  have to get your own)

## Examples

``` r
if (FALSE) { # \dontrun{
getkey(service="tropicos")
getkey(service="iucn")
getkey(service="entrez")
} # }
```
