# taxize options

taxize options

## Usage

``` r
taxize_options(taxon_state_messages = NULL, ncbi_sleep = NULL, quiet = FALSE)
```

## Arguments

- taxon_state_messages:

  (logical) suppress messages? default: `NULL` (same as setting
  `FALSE`). Set to `TRUE` to suppress messages, and `FALSE` to not
  suppress messages

- ncbi_sleep:

  (numeric/integer) number of seconds to sleep between NCBI ENTREZ http
  requests. applies to the functions:
  [`classification()`](https://docs.ropensci.org/taxize/reference/classification.md),
  [`comm2sci()`](https://docs.ropensci.org/taxize/reference/comm2sci.md),
  [`genbank2uid()`](https://docs.ropensci.org/taxize/reference/genbank2uid.md),
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md)
  and
  [`ncbi_children()`](https://docs.ropensci.org/taxize/reference/ncbi_children.md).
  defaults: 0.334 (without API key) or 0.101 (with API key). minimum
  value can not be less than 0.101

- quiet:

  (logical) quiet informational output from this function. default:
  `TRUE`

## Examples

``` r
if (FALSE) { # \dontrun{
taxize_options()
taxize_options(FALSE)
taxize_options(TRUE)
taxize_options(ncbi_sleep = 0.4)
taxize_options(taxon_state_messages = TRUE, ncbi_sleep = 0.4)
} # }
```
