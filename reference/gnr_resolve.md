# Resolve names using Global Names Resolver

NOTE: this function is depreciated and will be removed in a future
version. The service this function interacts with is no longer
maintained and has been replaced by GNA Verifier, which can be used with
the
[`gna_verifier()`](https://docs.ropensci.org/taxize/reference/gna_verifier.md)
function.

## Usage

``` r
gnr_resolve(
  sci,
  data_source_ids = NULL,
  resolve_once = FALSE,
  with_context = FALSE,
  canonical = FALSE,
  highestscore = TRUE,
  best_match_only = FALSE,
  preferred_data_sources = NULL,
  with_canonical_ranks = FALSE,
  http = "get",
  cap_first = TRUE,
  fields = "minimal",
  names = NULL,
  ...
)
```

## Arguments

- sci:

  character; taxonomic names to be resolved. Doesn't work for
  vernacular/common names.

- data_source_ids:

  character; IDs to specify what data source is searched. See
  [`gnr_datasources()`](https://docs.ropensci.org/taxize/reference/gnr_datasources.md).

- resolve_once:

  logical; Find the first available match instead of matches across all
  data sources with all possible renderings of a name. When `TRUE`,
  response is rapid but incomplete.

- with_context:

  logical; Reduce the likelihood of matches to taxonomic homonyms. When
  `TRUE` a common taxonomic context is calculated for all supplied names
  from matches in data sources that have classification tree paths.
  Names out of determined context are penalized during score
  calculation.

- canonical:

  logical; If `FALSE` (default), gives back names with taxonomic
  authorities. If `TRUE`, returns canocial names (without tax.
  authorities and abbreviations).

- highestscore:

  logical; Return those names with the highest score for each searched
  name? Defunct

- best_match_only:

  (logical) If `TRUE`, best match only returned. Default: `FALSE`

- preferred_data_sources:

  (character) A vector of one or more data source IDs.

- with_canonical_ranks:

  (logical) Returns names with infraspecific ranks, if present. If
  `TRUE`, we force `canonical=TRUE`, otherwise this parameter would have
  no effect. Default: `FALSE`

- http:

  The HTTP method to use, one of "get" or "post". Default: "get". Use
  `http="post"` with large queries. Queries with \> 300 records use
  "post" automatically because "get" would fail

- cap_first:

  (logical) For each name, fix so that the first name part is
  capitalized, while others are not. This web service is sensitive to
  capitalization, so you'll get different results depending on
  capitalization. First name capitalized is likely what you'll want and
  is the default. If `FALSE`, names are not modified. Default: `TRUE`

- fields:

  (character) One of minimal (default) or all. Minimal gives back just
  four fields, whereas all gives all fields back.

- names:

  Deprecated, see `sci`

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

A data.frame with one attribute `not_known`: a character vector of taxa
unknown to the Global Names Index. Access like
`attr(output, "not_known")`, or `attributes(output)$not_known`.

Columns of the output data.frame:

- user_supplied_name (character) - the name you passed in to the `names`
  parameter, unchanged.

- submitted_name (character) - the actual name submitted to the GNR
  service

- data_source_id (integer/numeric) - data source ID

- data_source_title (character) - data source name

- gni_uuid (character) - Global Names Index UUID (aka identifier)

- matched_name (character) - the matched name in the GNR service

- matched_name2 (character) - returned if `canonical=TRUE`, in which
  case **matched_name** is not returned

- classification_path (character) - names of the taxonomic
  classification tree, with names separated by pipes (`|`)

- classification_path_ranks (character) - ranks of the taxonomic
  classification tree, with names separated by pipes (`|`)

- classification_path_ids (character) - identifiers of the taxonomic
  classification tree, with names separated by pipes (`|`)

- taxon_id (character) - taxon identifier

- edit_distance (integer/numeric) - edit distance

- imported_at (character) - date imported

- match_type (integer/numeric) - match type

- match_value (character) - description of match type

- prescore (character) - pre score

- score (numeric) - score

- local_id (character) - local identifier

- url (character) - URL for taxon

- global_id (character) - global identifier

- current_taxon_id (character) - current taxon id

- current_name_string (character) - current name string

  Note that names (i.e. rows) are dropped that are NA, are zero length
  strings, are not character vectors, or are not found by the API.

## Details

See section **Age of datasets in the Global Names Resolver**

## Age of datasets in the Global Names Resolver

IMPORTANT: Datasets used in the Global Names Resolver vary in how
recently they've been updated. See the `updated_at` field in the output
of
[`gnr_datasources()`](https://docs.ropensci.org/taxize/reference/gnr_datasources.md)
for dates when each dataset was last updated.

## preferred_data_sources

If `preferred_data_sources` is used, only the preferred data is
returned - if it has any results.

## References

http://gnrd.globalnames.org/api http://gnrd.globalnames.org/

## See also

[`gnr_datasources()`](https://docs.ropensci.org/taxize/reference/gnr_datasources.md)

## Author

Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
gnr_resolve(sci = c("Helianthus annuus", "Homo sapiens"))
gnr_resolve(sci = c("Asteraceae", "Plantae"))

# Using data source 12 (Encyclopedia of Life)
sources <- gnr_datasources()
sources
eol <- sources$id[sources$title == 'EOL']
gnr_resolve(names=c("Helianthos annuus","Homo sapians"), data_source_ids=eol)

# Two species in the NE Brazil catalogue
sps <- c('Justicia brasiliana','Schinopsis brasiliensis')
gnr_resolve(sci = sps, data_source_ids = 145)

# Best match only, compare the two
gnr_resolve(sci = "Helianthus annuus", best_match_only = FALSE)
gnr_resolve(sci = "Helianthus annuus", best_match_only = TRUE)

# Preferred data source
gnr_resolve(sci = "Helianthus annuus", preferred_data_sources = c(3,4))

# Return canonical names - default is canonical=FALSE
head(gnr_resolve(sci = "Helianthus annuus"))
head(gnr_resolve(sci = "Helianthus annuus", canonical=TRUE))

# Return canonical names with authority stripped but
# ranks still present
gnr_resolve("Scorzonera hispanica L. subsp. asphodeloides Wallr.")
## vs.
gnr_resolve("Scorzonera hispanica L. subsp. asphodeloides Wallr.",
   with_canonical_ranks = TRUE)
} # }
```
