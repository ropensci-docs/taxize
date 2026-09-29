# Search for taxonomy data from Plantminer.com

Search for taxonomy data from Plantminer.com

## Usage

``` r
plantminer(plants, from = "tpl", messages = TRUE, ...)
```

## Arguments

- plants:

  (character) Vector of plant species names. Required.

- from:

  (character) One of tpl (for theplantlist.com data), or flora (for
  Brazilian Flora Checklist). Required. Default: `tpl`

- messages:

  (logical) informative messages or not. Default: `TRUE`

- ...:

  curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

data.frame of results.

## Note

you used to need an API key for Plantminer; it's no longer needed

## Examples

``` r
if (FALSE) { # \dontrun{
# A single taxon
plantminer("Ocotea pulchella")

# Many taxa
plants <- c("Myrcia lingua", "Myrcia bella", "Ocotea pulchella",
    "Miconia", "Coffea arabica var. amarella", "Bleh")
plantminer(plants)

# By deafult, tpl is used, for Theplantlist data,
# toggle the from parameter here
plantminer("Ocotea pulchella", from = "flora")
} # }
```
