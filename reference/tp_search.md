# Search Tropicos by scientific name, common name, or Tropicos ID.

Search Tropicos by scientific name, common name, or Tropicos ID.

## Usage

``` r
tp_search(
  sci = NULL,
  com = NULL,
  nameid = NULL,
  orderby = NULL,
  sortorder = NULL,
  pagesize = NULL,
  startrow = NULL,
  type = NULL,
  key = NULL,
  name = NULL,
  commonname = NULL,
  ...
)
```

## Arguments

- sci:

  A scientific name, e.g., "poa annua". See Details.

- com:

  A common name, e.g., "annual blue grass"

- nameid:

  Your search string. e.g., "25509881"

- orderby:

  Your search string. e.g., "1"

- sortorder:

  Your search string. e.g., "ascending"

- pagesize:

  Your search string. e.g., "100"

- startrow:

  Your search string. e.g., "1"

- type:

  Type of search, "wildcard" (default) will add a wildcard to the end of
  your search string. "exact" will use your search string exactly.

- key:

  Your Tropicos API key; See
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
  for help on authentication

- name:

  Deprecated, see `sci`

- commonname:

  Deprecated, see `com`

- ...:

  Further args passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

List or dataframe.

## Details

More details on the `name` parameter: Tropicos will fail if you include
a period (`.`) in your name string, e.g., `var.`, so we replace periods
before the request is made to the Tropicos web service. In addition,
Tropicos for some reason doesn't want to see sub-specific rank names
like `var`/`subsp`, so remove those from your query.

## References

http://services.tropicos.org/help?method=SearchNameXml

## Examples

``` r
if (FALSE) { # \dontrun{
tp_search(sci = 'Poa annua')
tp_search(sci = 'Poa annua subsp. annua')
tp_search(sci = 'Poa annua var. annua')
tp_search(sci = 'Poa annua var annua')
tp_search(sci = 'Poa annua annua')
} # }
```
