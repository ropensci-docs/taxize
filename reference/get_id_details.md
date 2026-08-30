# Details on `get_*()` functions

Including outputs from `get_*()` functions, as well as their attributes,
and all exception behaviors.

## Details

This document applies to the following functions:

- [`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md)

- [`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md)

- [`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md)

- [`get_ids()`](https://docs.ropensci.org/taxize/reference/get_ids.md)

- [`get_iucn()`](https://docs.ropensci.org/taxize/reference/get_iucn.md)

- [`get_natservid()`](https://docs.ropensci.org/taxize/reference/get_natservid.md)

- [`get_nbnid()`](https://docs.ropensci.org/taxize/reference/get_nbnid.md)

- [`get_tolid()`](https://docs.ropensci.org/taxize/reference/get_tolid.md)

- [`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md)

- [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md)

- [`get_ubioid()`](https://docs.ropensci.org/taxize/reference/get_ubioid-defunct.md)

- [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md)

- [`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md)

- [`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md)

## attributes

Each output from `get_*()` functions have the following attributes:

- *match* (character) - the reason for NA, either 'not found', 'found'
  or if `ask = FALSE` then 'NA due to ask=FALSE')

- *multiple_matches* (logical) - Whether multiple matches were returned
  by the data source. This can be `TRUE`, even if you get 1 name back
  because we try to pattern match the name to see if there's any direct
  matches. So sometimes this attribute is `TRUE`, as well as
  `pattern_match`, which then returns 1 resulting name without user
  prompt.

- *pattern_match* (logical) - Whether a pattern match was made. If
  `TRUE` then`multiple_matches` must be `TRUE`, and we found a perfect
  match to your name, ignoring case. If `FALSE`, there wasn't a direct
  match, and likely you need to pick from many choices or further
  parameters can be used to limit results

- *uri* (character) - The URI where more information can be read on the
  taxon

&nbsp;

- includes the taxonomic identifier in the URL somewhere. This may be
  missing if the value returned is `NA`

## exceptions

The following are the various ways in which `get_*()` functions behave:

- success - the value returned is a character string or numeric

- no matches found - you'll get an NA, refine your search or possible
  the taxon searched for does not exist in the database you're using

- more than on match and `ask = FALSE` - if there's more than one
  matching result, and you have set `ask = FALSE`, then we can't
  determine the single match to return, so we give back `NA`. However,
  in this case we do set the `match` attribute to say
  `NA due to ask=FALSE & > 1 result` so it's very clear what happened -
  and you can even programatically check this as well

- NA due to some other reason - some `get_*()` functions have additional
  parameters for filtering taxa. It's possible that even though there's
  results (that is, `found` will say `TRUE`), you can get back an NA.
  This is most likely if the parameter filters taxa after they are
  returned from the data provider and the value passed to the parameter
  leads to no matches.
