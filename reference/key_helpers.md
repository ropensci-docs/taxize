# Helpers to set up authentication for the different providers.

Sets up authentication to diverse providers by providing the user a
detailed prompt.

## Usage

``` r
use_tropicos()

use_entrez()

use_iucn()
```

## Details

Key helpers

## `use_tropicos()`

Browses to Tropicos API key request URL and provides instruction on how
to store the key. After filling the form you will get the key soon, but
not immediately.

## `use_entrez()`

Browse NCBI Entrez to help make an API key request and provides
instruction on how to store the key. There's no direct URL to request a
key, one first needs to log in or register and then to generate a key
from one's account.

Note that NCBI Entrez doesn't require that you use an API key, but you
should get higher rate limit with a key, so do get one.

## `use_iucn()`

Browse IUCN Red List API key request URL and provides instruction on how
to store the key. This function wraps
[`rredlist::rl_use_iucn()`](https://docs.ropensci.org/rredlist/reference/rl_use_iucn.html)
from the `rredlist` package. After filling the form you will get the key
soon, but not immediately.

## See also

[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
