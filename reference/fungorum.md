# Index Fungorum

Search for taxonomic names in Index Fungorum

## Usage

``` r
fg_name_search(q, anywhere = TRUE, limit = 10, ...)

fg_author_search(q, anywhere = TRUE, limit = 10, ...)

fg_epithet_search(q, anywhere = TRUE, limit = 10, ...)

fg_name_by_key(key, ...)

fg_name_full_by_lsid(lsid, ...)

fg_all_updated_names(date, ...)

fg_deprecated_names(date, ...)
```

## Arguments

- q:

  (character) Query term

- anywhere:

  (logical) Default: `TRUE`

- limit:

  (integer) Number of results to return. max limit value appears to be
  6000, not positive about that though

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

- key:

  (character) A IndexFungorum taxon key

- lsid:

  (character) an LSID, e.,g. "urn:lsid:indexfungorum.org:names:81085"

- date:

  (character) Date, of the form YYYMMDD

## Value

A `data.frame`, or `NULL` if no results

## References

http://www.indexfungorum.org/, API docs:
http://www.indexfungorum.org/ixfwebservice/fungus.asmx

## Examples

``` r
if (FALSE) { # \dontrun{
# NameSearch
fg_name_search(q = "Gymnopus", limit = 2, verbose = TRUE)
fg_name_search(q = "Gymnopus")

# EpithetSearch
fg_epithet_search(q = "phalloides")

# NameByKey
fg_name_by_key(17703)

# NameFullByKey
fg_name_full_by_lsid("urn:lsid:indexfungorum.org:names:81085")

# AllUpdatedNames
fg_all_updated_names(date = gsub("-", "", Sys.Date() - 2))

# DeprecatedNames
fg_deprecated_names(date=20151001)

# AuthorSearch
fg_author_search(q = "Fayod", limit = 2)
} # }
```
