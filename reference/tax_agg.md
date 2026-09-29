# Aggregate species data to given taxonomic rank

Aggregate species data to given taxonomic rank

## Usage

``` r
tax_agg(x, rank, db = "ncbi", messages = FALSE, ...)

# S3 method for class 'tax_agg'
print(x, ...)
```

## Arguments

- x:

  Community data matrix. Taxa in columns, samples in rows.

- rank:

  character; Taxonomic rank to aggregate by.

- db:

  character; taxonomic API to use, 'ncbi, 'itis' or both, see
  [`tax_name()`](https://docs.ropensci.org/taxize/reference/tax_name.md).
  Note that each taxonomic data source has their own identifiers, so
  that if you provide the wrong `db` value for the identifier you could
  get a result, but it will likely be wrong (not what you were
  expecting). If using ncbi we recommend getting an API key; see
  [taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)

- messages:

  (logical) If FALSE (Default) suppress messages

- ...:

  Other arguments passed to
  [`get_tsn()`](https://docs.ropensci.org/taxize/reference/get_tsn.md)
  or
  [`get_uid()`](https://docs.ropensci.org/taxize/reference/get_uid.md)

## Value

A list of class `tax_agg` with the following items:

- `x` Community data matrix with aggregated data.

- `by` A lookup-table showing which taxa were aggregated.

- `n_pre` Number of taxa before aggregation.

- `rank` Rank at which taxa have been aggregated.

## Details

`tax_agg` aggregates (sum) taxa to a specific taxonomic level. If a
taxon is not found in the database (ITIS or NCBI) or the supplied taxon
is on higher taxonomic level this taxon is not aggregated.

## See also

[tax_name](https://docs.ropensci.org/taxize/reference/tax_name.md)

## Examples

``` r
if (FALSE) { # \dontrun{
if (requireNamespace("vegan", quietly = TRUE)) {
  # use dune dataset
  data(dune, package='vegan')
  species <- c("Achillea millefolium", "Agrostis stolonifera",
    "Aira praecox", "Alopecurus geniculatus", "Anthoxanthum odoratum",
    "Bellis perennis", "Bromus hordeaceus", "Chenopodium album",
    "Cirsium arvense", "Comarum palustre", "Eleocharis palustris",
    "Elymus repens", "Empetrum nigrum", "Hypochaeris radicata",
    "Juncus articulatus", "Juncus bufonius", "Lolium perenne",
    "Plantago lanceolata", "Poa pratensis", "Poa trivialis",
    "Ranunculus flammula", "Rumex acetosa", "Sagina procumbens",
    "Salix repens", "Scorzoneroides autumnalis", "Trifolium pratense",
    "Trifolium repens", "Vicia lathyroides", "Brachythecium rutabulum",
    "Calliergonella cuspidata")
  colnames(dune) <- species

  # aggregate sample to families
  (agg <- tax_agg(dune, rank = 'family', db = 'ncbi'))

  # extract aggregated community data matrix for further usage
  agg$x
  # check which taxa have been aggregated
  agg$by
}

# A use case where there are different taxonomic levels in the same dataset
spnames <- c('Puma','Ursus americanus','Ursidae')
df <- data.frame(c(1,2,3), c(11,12,13), c(1,4,50))
names(df) <- spnames
out <- tax_agg(x=df, rank = 'family', db='itis')
out$x

# You can input a matrix too
mat <- matrix(c(1,2,3, 11,12,13), nrow = 2, ncol = 3,
 dimnames=list(NULL, c('Puma concolor','Ursus americanus','Ailuropoda melanoleuca')))
tax_agg(mat, rank = 'family', db='itis')
} # }
```
