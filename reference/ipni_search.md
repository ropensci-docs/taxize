# Search for names in the International Plant Names Index (IPNI).

Note: This data source is also provided in the Global Names Index (GNI)
(http://gni.globalnames.org/data_sources). The interface to the data is
different among the two services though.

## Usage

``` r
ipni_search(
  family = NULL,
  infrafamily = NULL,
  genus = NULL,
  infragenus = NULL,
  species = NULL,
  infraspecies = NULL,
  publicationtitle = NULL,
  authorabbrev = NULL,
  includepublicationauthors = NULL,
  includebasionymauthors = NULL,
  geounit = NULL,
  addedsince = NULL,
  modifiedsince = NULL,
  isapnirecord = NULL,
  isgcirecord = NULL,
  isikrecord = NULL,
  ranktoreturn = NULL,
  output = "minimal",
  ...
)
```

## Arguments

- family:

  Family name to search on (Optional)

- infrafamily:

  Infrafamilial name to search on (Optional)

- genus:

  Genus name to search on (Optional)

- infragenus:

  Infrageneric name to search on (Optional)

- species:

  Species name to search on (Optional) - Note, this is the epithet, not
  the full genus - epithet name combination.

- infraspecies:

  Infraspecies name to search on (Optional)

- publicationtitle:

  Publication name or abbreviation to search on. Again, replace any
  spaces with a '+' (e.g. 'J.+Bot.') (Optional)

- authorabbrev:

  Author standard form to search on (publishing author, basionym author
  or both - see below) (Optional)

- includepublicationauthors:

  TRUE (default) to include the taxon author in the search or FALSE to
  exclude it

- includebasionymauthors:

  TRUE (default) to include the basionum author in the search or FALSE
  to exclude it

- geounit:

  Country name or other geographical unit to search on (see the help
  pages for more information and warnings about the use of this option)
  (Optional)

- addedsince:

  Date to search on in the format 'yyyy-mm-dd', e.g. 2005-08-01 for all
  records added since the first of August, 2005. (see the help pages for
  more information and warnings about the use of this option) (Optional.
  If supplied must be in format YYYY-MM-DD and must be greater than or
  equal to 1984-01-01.)

- modifiedsince:

  Date to search on in the format 'yyyy-mm-dd', e.g. 2005-08-01 for all
  records edited since the first of August, 2005. (See the help pages
  for more information about the use of this option) (Optional. If
  supplied must be in format YYYY-MM-DD and must be greater than or
  equal to 1993-01-01.)

- isapnirecord:

  FALSE (default) to exclude records from the Australian Plant Name
  Index

- isgcirecord:

  FALSE (default) to exclude records from the Gray Cards Index

- isikrecord:

  FALSE (default) to exclude records from the Index Kewensis

- ranktoreturn:

  One of a few options to choose the ranks returned. See details.

- output:

  One of minimal (default), classic, short, or extended

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  (Optional). Default: returns all ranks.

## Value

a tibble (data.frame)

## Details

`ranktoreturn` options:

- "all" - all records

- "fam" - family records

- "infrafam" - infrafamilial records

- "gen" - generic records

- "infragen" - infrageneric records

- "spec" - species records

- "infraspec" - infraspecific records

## References

https://web.archive.org/web/20190501132148/http://www.ipni.org/link_to_ipni.html

## Examples

``` r
if (FALSE) { # \dontrun{
ipni_search(genus='Brintonia', isapnirecord=TRUE, isgcirecord=TRUE,
  isikrecord=TRUE)
ipni_search(genus='Ceanothus')
ipni_search(genus='Pinus', species='contorta')

# Different output formats
ipni_search(genus='Ceanothus')
ipni_search(genus='Ceanothus', output='short')
ipni_search(genus='Ceanothus', output='extended')
} # }
```
