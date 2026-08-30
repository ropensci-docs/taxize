# Search for pages in EOL database using a taxonconceptID.

Search for pages in EOL database using a taxonconceptID.

## Usage

``` r
eol_pages(
  taxonconceptID,
  images_per_page = NULL,
  images_page = NULL,
  videos_per_page = NULL,
  videos_page = NULL,
  sounds_per_page = NULL,
  sounds_page = NULL,
  maps_per_page = NULL,
  maps_page = NULL,
  texts_per_page = NULL,
  texts_page = NULL,
  subjects = "overview",
  licenses = "all",
  details = FALSE,
  common_names = FALSE,
  synonyms = FALSE,
  references = FALSE,
  taxonomy = TRUE,
  vetted = 0,
  cache_ttl = NULL,
  ...
)
```

## Arguments

- taxonconceptID:

  (numeric) a taxonconceptID, which is also the page number

- images_per_page:

  (integer) number of returned image objects (0-75)

- images_page:

  (integer) images page

- videos_per_page:

  (integer) number of returned video objects (0-75)

- videos_page:

  (integer) videos page

- sounds_per_page:

  (integer) number of returned sound objects (0-75)

- sounds_page:

  (integer) sounds page

- maps_per_page:

  (integer) number of returned map objects (0-75)

- maps_page:

  (integer) maps page

- texts_per_page:

  (integer) number of returned text objects (0-75)

- texts_page:

  (integer) texts page

- subjects:

  'overview' (default) to return the overview text (if exists), a pipe
  \| delimited list of subject names from the list of EOL accepted
  subjects (e.g. TaxonBiology, FossilHistory), or 'all' to get text in
  any subject. Always returns an overview text as a first result (if one
  exists in the given context).

- licenses:

  A pipe \| delimited list of licenses or 'all' (default) to get objects
  under any license. Licenses abbreviated cc- are all Creative Commons
  licenses. Visit their site for more information on the various
  licenses they offer.

- details:

  Include all metadata for data objects. (Default: `FALSE`)

- common_names:

  Return all common names for the page's taxon (Default: `FALSE`)

- synonyms:

  Return all synonyms for the page's taxon (Default: `FALSE`)

- references:

  Return all references for the page's taxon (Default: `FALSE`)

- taxonomy:

  (logical) Whether to return any taxonomy details from different taxon
  hierarchy providers, in an array named `taxonconcepts` (Default:
  `TRUE`)

- vetted:

  If 'vetted' is given a value of '1', then only trusted content will be
  returned. If 'vetted' is '2', then only trusted and unreviewed content
  will be returned (untrusted content will not be returned). The default
  is to return all content. (Default: `FALSE`)

- cache_ttl:

  The number of seconds you wish to have the response cached.

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

JSON list object, or data.frame.

## Details

It's possible to return JSON or XML with the EOL API. However, this
function only returns JSON for now.

## Examples

``` r
if (FALSE) { # \dontrun{
(pageid <- eol_search('Pomatomus')$pageid[1])
x <- eol_pages(taxonconceptID = pageid)
x
x$scinames

z <- eol_pages(taxonconceptID = pageid, synonyms = TRUE)
z$synonyms

z <- eol_pages(taxonconceptID = pageid, common_names = TRUE)
z$vernacular
} # }
```
