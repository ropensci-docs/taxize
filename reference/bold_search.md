# Search Barcode of Life for taxonomic IDs

Search Barcode of Life for taxonomic IDs

## Usage

``` r
bold_search(
  sci = NULL,
  id = NULL,
  fuzzy = FALSE,
  dataTypes = "basic",
  includeTree = FALSE,
  response = FALSE,
  name = NULL,
  ...
)
```

## Arguments

- sci:

  (character) One or more scientific names.

- id:

  (integer) One or more BOLD taxonomic identifiers.

- fuzzy:

  (logical) Whether to use fuzzy search or not (default: `FALSE`). Only
  used if `name` passed.

- dataTypes:

  (character) Specifies the datatypes that will be returned. See Details
  for options. This variable is ignored if `name` parameter is passed,
  but is used if the `id` parameter is passed.

- includeTree:

  (logical) If TRUE (default: FALSE), returns a list containing
  information for parent taxa as well as the specified taxon. Only used
  if `id` passed.

- response:

  (logical) Note that response is the object that returns from the curl
  call, useful for debugging, and getting detailed info on the API call.

- name:

  Deprecated, see `sci`

- ...:

  named curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

A list of data.frame's.

## Details

You must provide one of `sci` or `id` to this function. The other
parameters are optional. Note that when passing in `sci`, `fuzzy` can be
used as well, while if `id` is passed, then `fuzzy` is ignored, and
`dataTypes` `includeTree` can be used.

Options for `dataTypes` parameter:

- all returns all data

- basic returns basic taxon information

- images returns specimen image. Includes copyright information, image
  URL, image metadata.

- stats Returns specimen and sequence statistics. Includes public
  species count, public BIN count, public marker counts, public record
  count, specimen count, sequenced specimen count, barcode specimen
  count, species count, barcode species count.

- geo Returns collection site information. Includes country, collection
  site map.

- sequencinglabs Returns sequencing labs. Includes lab name, record
  count.

- depository Returns specimen depositories. Includes depository name,
  record count.

- thirdparty Returns information from third parties. Includes wikipedia
  summary, wikipedia URL, GBIF map.

## References

http://www.boldsystems.org/index.php/resources/api

## Examples

``` r
if (FALSE) { # \dontrun{
# A basic example
bold_search(sci="Apis")
bold_search(sci="Agapostemon")
bold_search(sci="Poa")

# Fuzzy search
head(bold_search(sci="Po", fuzzy=TRUE))
head(bold_search(sci="Aga", fuzzy=TRUE))

# Many names
bold_search(sci=c("Apis","Puma concolor"))
nms <- names_list('species')
bold_search(sci=nms)

# Searching by ID - dataTypes can be used, and includeTree can be used
bold_search(id=88899)
bold_search(id=88899, dataTypes="stats")
bold_search(id=88899, dataTypes="geo")
bold_search(id=88899, dataTypes="basic")
bold_search(id=88899, includeTree=TRUE)
} # }
```
