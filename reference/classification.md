# Retrieve the taxonomic hierarchy for a given taxon ID.

Retrieve the taxonomic hierarchy for a given taxon ID.

## Usage

``` r
classification(...)

# Default S3 method
classification(
  sci_id,
  db = NULL,
  callopts = list(),
  return_id = TRUE,
  rows = NA,
  x = NULL,
  ...
)

# S3 method for class 'tsn'
classification(id, return_id = TRUE, ...)

# S3 method for class 'uid'
classification(
  id,
  callopts = list(),
  return_id = TRUE,
  batch_size = 50,
  max_tries = 3,
  ...
)

# S3 method for class 'eolid'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'tpsid'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'gbifid'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'nbnid'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'tolid'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'wormsid'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'natservid'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'boldid'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'wiki'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'pow'
classification(id, callopts = list(), return_id = TRUE, ...)

# S3 method for class 'ids'
classification(id, ...)

# S3 method for class 'classification'
cbind(...)

# S3 method for class 'classification'
rbind(...)

# S3 method for class 'classification_ids'
cbind(...)

# S3 method for class 'classification_ids'
rbind(...)
```

## Arguments

- ...:

  For `classification`: other arguments passed to
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
  [`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
  [`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
  [`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
  [`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md),
  [`get_natservid()`](https://docs.ropensci.org/taxize/reference/get_natservid.md),
  [`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md),
  [`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
  [`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md).
  For `rbind.classification` and `cbind.classification`: one or more
  objects of class `classification`

- sci_id:

  Vector of taxa names (character) or IDs (character or numeric) to
  query. For `db = "eol"`, EOL expects you to pass it a taxon id, called
  `eolid` in the output of
  [`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md).

- db:

  character; database to query. either `ncbi`, `itis`, `eol`,
  `tropicos`, `gbif`, `nbn`, `worms`, `natserv`, `bold`, `wiki`, or
  `pow`. Note that each taxonomic data source has, their own
  identifiers, so that if you provide the wrong `db` value for the
  identifier you could get a result, but it will likely be wrong (not
  what you were expecting). If using ncbi, and/or tropicos, we recommend
  getting an API key; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- callopts:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

- return_id:

  (logical) If `TRUE` (default), return the taxon id as well as the name
  and rank of taxa in the lineage returned. Ignored for natserv as they
  don't return IDs in their taxonomic classification data.

- rows:

  (numeric) Any number from 1 to infinity. If the default NA, all rows
  are considered. Note that this parameter is ignored if you pass in a
  taxonomic id instead of a name of class character.

- x:

  Deprecated, see `sci_id`

- id:

  character; identifiers, returned by
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
  [`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
  [`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
  [`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
  [`get_tolid()`](https://docs.ropensci.org/taxize/reference/get_tolid.md),
  [`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md),
  [`get_natservid()`](https://docs.ropensci.org/taxize/reference/get_natservid.md),
  [`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md),
  [`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
  [`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md)

- batch_size:

  (numeric) For NCBI queries, specify the number of IDs to lookup for
  each query.

- max_tries:

  (numeric) For NCBI queries, the number of times a particular query
  will be attempted, assuming the first does not work.

## Value

A named list of data.frames with the taxonomic classification of every
supplied taxa.

## Details

If IDs are supplied directly (not from the `get_*` functions) you must
specify the type of ID. There is a timeout of 1/3 seconds between
queries to NCBI.

BEWARE: Right now, NBN doesn't return the queried taxon in the
classification. But you can attach it yourself quite easily of course.
This behavior is different from the other data sources.

## Lots of results

It may happen sometimes that you get more results back from your query
than will show in the data.frame on screen. Our advice is to refine your
query in those cases. On a data source basis we can attempt to help make
it easier to refine queries, whether it be with the data provider
(unlikely to happen), or in the code in this package (more likely) - let
us know if you run into too many results problem and we'll see what we
can do.

## Authentication

See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

## EOL

EOL does not have very good failure behavior. For example, if you submit
an ID that does not exist they'll return a 500 HTTP error, which is not
an appropriate error; it's probably that that ID does not exist in their
database, but we can't know for sure. Isn't that fun?

## NCBI Rate limits

In case you run into NCBI errors due to your rate limit being exceeded,
see
[`taxize_options()`](https://docs.ropensci.org/taxize/reference/taxize_options.md),
where you can set `ncbi_sleep`.

## HTTP version for NCBI requests

We hard code `http_version = 2L` to use HTTP/1.1 in HTTP requests to the
Entrez API. See `curl::curl_symbols('CURL_HTTP_VERSION')`

## See also

[`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md),
[`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md),
[`get_eolid()`](https://docs.ropensci.org/taxize/reference/get_eolid.md),
[`get_tpsid()`](https://docs.ropensci.org/taxize/reference/get_tpsid.md),
[`get_gbifid()`](https://docs.ropensci.org/taxize/reference/get_gbifid.md),
[`get_wormsid()`](https://docs.ropensci.org/taxize/reference/get_wormsid.md),
[`get_natservid()`](https://docs.ropensci.org/taxize/reference/get_natservid.md),
[`get_boldid()`](https://docs.ropensci.org/taxize/reference/get_boldid.md),
[`get_wiki()`](https://docs.ropensci.org/taxize/reference/get_wiki.md),
[`get_pow()`](https://docs.ropensci.org/taxize/reference/get_pow.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Plug in taxon IDs
classification(9606, db = 'ncbi')
classification(c(9606, 55062), db = 'ncbi')
classification(129313, db = 'itis')
classification(6985636, db = 'eol')
classification(126436, db = 'worms')
classification('Helianthus annuus', db = 'pow')
classification('Helianthus', db = 'pow')
classification('Asteraceae', db = 'pow')
classification("134717", db = 'natserv')
classification(c(2704179, 6162875, 8286319, 2441175, 731), db = 'gbif')
classification(25509881, db = 'tropicos')
classification("NBNSYS0000004786", db = 'nbn')
classification(as.nbnid("NBNSYS0000004786"), db = 'nbn')
classification(3930798, db = 'tol')

## works the same if IDs are in class character
classification(c("2704179", "2441176"), db = 'gbif')
classification("Agapostemon", db = "bold")

# wikispecies
classification("Malus domestica", db = "wiki")
classification("Pinus contorta", db = "wiki")
classification("Pinus contorta", db = "wiki", wiki_site = "commons")
classification("Pinus contorta", db = "wiki", wiki_site = "pedia")
classification("Pinus contorta", db = "wiki", wiki_site = "pedia",
  wiki = "fr")

classification(get_wiki("Malus domestica", "commons"))
classification(get_wiki("Malus domestica", "species"))
classification(c("Pinus contorta", "Malus domestica"), db = "wiki")

# Plug in taxon names
## in this case, we use get_*() fxns internally to first get taxon IDs
classification("Oncorhynchus mykiss", db = "eol")
classification(c("Chironomus riparius", "aaa vva"), db = 'ncbi')
classification(c("Chironomus riparius", "aaa vva"), db = 'ncbi',
  messages=FALSE)
classification(c("Chironomus riparius", "aaa vva"), db = 'itis')
classification(c("Chironomus riparius", "aaa vva"), db = 'itis',
  messages=FALSE)
classification(c("Chironomus riparius", "aaa vva"), db = 'eol')
classification("Alopias vulpinus", db = 'nbn')
classification('Gadus morhua', db = 'worms')
classification('Aquila chrysaetos', db = 'natserv')
classification('Gadus morhua', db = 'natserv')
classification('Pomatomus saltatrix', db = 'natserv')
classification('Aquila chrysaetos', db = 'natserv')
classification(c("Chironomus riparius", "asdfasdfsfdfsd"), db = 'gbif')
classification("Chironomus", db = 'tol')
classification("Poa annua", db = 'tropicos')

# Use methods for get_uid, get_tsn, get_eolid, get_tpsid
classification(get_uid(c("Chironomus riparius", "Puma concolor")))

classification(get_uid(c("Chironomus riparius", "aaa vva")))
classification(get_tsn(c("Chironomus riparius", "aaa vva")))
classification(get_tsn(c("Chironomus riparius", "aaa vva"),
  messages = FALSE))
classification(get_eolid(c("Chironomus riparius", "aaa vva")))
classification(get_tpsid(c("Poa annua", "aaa vva")))
classification(get_gbifid(c("Poa annua", "Bison bison")))

# Pass many ids from class "ids"
(out <- get_ids("Puma concolor", db = c('ncbi','gbif')))
(cl <- classification(out))

# Bind width-wise from class classification_ids
cbind(cl)

# Bind length-wise
rbind(cl)

# Many names to get_ids
(out <- get_ids(c("Puma concolor","Accipiter striatus"),
  db = c('ncbi','itis')))
(cl <- classification(out))
rbind(cl)
## cbind with so many names results in some messy data
cbind(cl)
## so you can turn off return_id
cbind( classification(out, return_id=FALSE) )

(cl_uid <- classification(get_uid(c("Puma concolor",
  "Accipiter striatus")), return_id=FALSE))
rbind(cl_uid)
cbind(cl_uid)
## cbind works a bit odd when there are lots of ranks without names
(cl_uid <- classification(get_uid(c("Puma concolor","Accipiter striatus")),
  return_id=TRUE))
cbind(cl_uid)

(cl_tsn <- classification(get_tsn(c("Puma concolor","Accipiter striatus"))))
rbind(cl_tsn)
cbind(cl_tsn)

(tsns <- get_tsn(c("Puma concolor","Accipiter striatus")))
(cl_tsns <- classification(tsns))
cbind(cl_tsns)

# NBN data
(res <- classification(c("Alopias vulpinus","Pinus sylvestris"),
  db = 'nbn'))
rbind(res)
cbind(res)

# Return taxonomic IDs
## the return_id parameter is logical, and you can turn it on or off.
## It's TRUE by default
classification(c("Alopias vulpinus","Pinus sylvestris"), db = 'ncbi',
  return_id = TRUE)
classification(c("Alopias vulpinus","Pinus sylvestris"), db = 'ncbi',
  return_id = FALSE)

# Use rows parameter to select certain
classification('Poa annua', db = 'tropicos')
classification('Poa annua', db = 'tropicos', rows=1:4)
classification('Poa annua', db = 'tropicos', rows=1)
classification('Poa annua', db = 'tropicos', rows=6)

# Queries of many IDs are processed in batches for NCBI
ids <- c("13083", "2650392", "1547764", "230054", "353934", "656984", 
"271789", "126272", "184644", "73213", "662816", "1161803", "1239353", 
"59420", "665675", "866969", "1091219", "1431218", "1471898", 
"864321", "251768", "2486276", "2068772", "1825808", "2006532", 
"128287", "1195738", "1084683", "1886461", "508296", "377247", 
"1489665", "329325", "219243", "1176946", "339893", "197933", 
"174510", "1704048", "212897", "154842", "1239280", "260135", 
"405735", "1566412", "2083462", "651348", "983204", "165380", 
"2338856", "2068760", "167262", "34229", "1213340", "478939", 
"1933585", "49951", "1277794", "1671089", "1502538", "362355", 
"746473", "242879", "158219", "313664", "2093188", "1541232", 
"584742", "1331091", "147639", "284492", "75642", "1412882", 
"391782", "1406855", "434506", "2053357", "217315", "1444328", 
"329249", "2294004", "84942", "324458", "538247", "69452", "49170", 
"1993845", "261646", "127633", "228146", "1420004", "1629772", 
"577055", "697062", "231660", "648380", "554953", "746496", "2602969")
result <- classification(ids, db = 'ncbi')
} # }
```
