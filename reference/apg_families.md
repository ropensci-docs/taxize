# MOBOT family names

Family names and their replacements from the Angiosperm Phylogeny
Website system of flowering plant classification.

## Format

A data frame with 1705 rows and 6 variables:

- `family`: family name

- `synonym`: if `accepted=FALSE`, this is the accepted name; if
  `accepted=TRUE`, this is `NA`, and the name in `family` is accepted

- `order`: order name for the family

- `accepted`: logical, if name in `family` column is accepted or not

- `original`: original data record from APG website, mapping name in
  `family` column to a new name, if there is one

- `accepted_name`: accepted name. accepted names, combining those that
  are accepted from `family` column, with the new name from `synonym` if
  applicable

## Source

http://www.mobot.org/MOBOT/research/APweb/

## Details

This dataset is from Version 14, incorporated on 2020-06-03, generated
using
[`apgFamilies()`](https://docs.ropensci.org/taxize/reference/apg.md)

(update script in inst/ignore/apg_script.R)
