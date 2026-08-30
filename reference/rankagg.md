# Aggregate data by given taxonomic rank

Aggregate data by given taxonomic rank

## Usage

``` r
rankagg(data = NULL, datacol = NULL, rank = NULL, fxn = "sum")
```

## Arguments

- data:

  A data.frame. Column headers must have capitalized ranks (e.g., Genus,
  Tribe, etc.) (data.frame)

- datacol:

  The data column (character)

- rank:

  Taxonomic rank to aggregate by (character)

- fxn:

  Arithmetic function or vector or functions (character)

## Examples

``` r
if (require(vegan)) {
data(dune.taxon, dune, package='vegan')
dat <- dune.taxon
dat$abundance <- colSums(dune)
rankagg(data=dat, datacol="abundance", rank="Genus")
rankagg(data=dat, "abundance", rank="Family")
rankagg(data=dat, "abundance", rank="Genus", fxn="mean")
rankagg(data=dat, "abundance", rank="Subclass")
rankagg(data=dat, "abundance", rank="Subclass", fxn="sd")
}
#> Loading required package: vegan
#> Loading required package: permute
#>      Subclass       sd
#> 1     Bryidae 27.57716
#> 2 Magnoliidae 18.45558
```
