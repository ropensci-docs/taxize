# Lookup details for specific names in all taxonomies in GBIF.

This is a taxize version of the same function in the `rgbif` package so
as to not have to import rgbif and thus require GDAL binary
installation.

## Usage

``` r
gbif_name_usage(
  key = NULL,
  name = NULL,
  data = "all",
  language = NULL,
  datasetKey = NULL,
  uuid = NULL,
  sourceId = NULL,
  rank = NULL,
  shortname = NULL,
  start = NULL,
  limit = 20,
  ...
)
```

## Arguments

- key:

  (numeric) A GBIF key for a taxon

- name:

  (character) Filters by a case insensitive, canonical namestring, e.g.
  'Puma concolor'

- data:

  (character) Specify an option to select what data is returned. See
  Description below.

- language:

  (character) Language, default is english

- datasetKey:

  (character) Filters by the dataset's key (a uuid)

- uuid:

  (character) A uuid for a dataset. Should give exact same results as
  datasetKey.

- sourceId:

  (numeric) Filters by the source identifier. Not used right now.

- rank:

  (character) Taxonomic rank. Filters by taxonomic rank as one of:
  CLASS, CULTIVAR, CULTIVAR_GROUP, DOMAIN, FAMILY, FORM, GENUS,
  INFORMAL, INFRAGENERIC_NAME, INFRAORDER, INFRASPECIFIC_NAME,
  INFRASUBSPECIFIC_NAME, KINGDOM, ORDER, PHYLUM, SECTION, SERIES,
  SPECIES, STRAIN, SUBCLASS, SUBFAMILY, SUBFORM, SUBGENUS, SUBKINGDOM,
  SUBORDER, SUBPHYLUM, SUBSECTION, SUBSERIES, SUBSPECIES, SUBTRIBE,
  SUBVARIETY, SUPERCLASS, SUPERFAMILY, SUPERORDER, SUPERPHYLUM,
  SUPRAGENERIC_NAME, TRIBE, UNRANKED, VARIETY

- shortname:

  (character) A short name..need more info on this?

- start:

  Record number to start at

- limit:

  Number of records to return

- ...:

  Curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

A list of length two. The first element is metadata. The second is
either a data.frame (verbose=FALSE, default) or a list (verbose=TRUE)

## References

https://www.gbif.org/developer/summary
