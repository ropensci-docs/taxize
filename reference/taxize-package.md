# Taxonomic Information from Around the Web

This package interacts with a suite of web 'APIs' for taxonomic tasks,
such as verifying species names, getting taxonomic hierarchies, and
verifying name spelling.

## About

Allows users to search over many websites for species names (scientific
and common) and download up- and downstream taxonomic hierarchical
information - and many other things.

The functions in the package that hit a specific API have a prefix and
suffix separated by an underscore. They follow the format of
`service_whatitdoes`. For example, `gnr_resolve` uses the Global Names
Resolver API to resolve species names.

General functions in the package that don't hit a specific API don't
have two words separated by an underscore, e.g., `classification`

You need API keys for some data sources. See
[taxize-authentication](https://docs.ropensci.org/taxize/reference/taxize-authentication.md)
for more information.

## Currently supported APIs

|                                                        |         |       |
|--------------------------------------------------------|---------|-------|
| API                                                    | prefix  | SOAP? |
| Encyclopedia of Life (EOL)                             | eol     | FALSE |
| Integrated Taxonomic Information Service (ITIS)        | itis    | FALSE |
| Global Names Resolver (from EOL/GBIF)                  | gnr     | FALSE |
| Global Names Index (from EOL/GBIF)                     | gni     | FALSE |
| IUCN Red List                                          | iucn    | FALSE |
| Tropicos (from Missouri Botanical Garden)              | tp      | FALSE |
| Theplantlist.org                                       | tpl     | FALSE |
| National Center for Biotechnology Information          | ncbi    | FALSE |
| CANADENSYS Vascan name search API                      | vascan  | FALSE |
| International Plant Names Index (IPNI)                 | ipni    | FALSE |
| World Register of Marine Species (WoRMS)               | worms   | TRUE  |
| Barcode of Life Data Systems (BOLD)                    | bold    | FALSE |
| Pan-European Species directories Infrastructure (PESI) | pesi    | TRUE  |
| Mycobank                                               | myco    | TRUE  |
| National Biodiversity Network (UK)                     | nbn     | FALSE |
| Index Fungorum                                         | fg      | FALSE |
| EU BON                                                 | eubon   | FALSE |
| Index of Names (ION)                                   | ion     | FALSE |
| Open Tree of Life (TOL)                                | tol     | FALSE |
| World Register of Marine Species (WoRMS)               | worms   | FALSE |
| NatureServe                                            | natserv | FALSE |

If the source above has a `TRUE` in the `SOAP?` column, it is not
available in this package. They are available from a different package
called **taxizesoap**. See the GitHub repo for how to install
https://github.com/ropensci/taxizesoap

## Catalogue of Life (COL)

COL introduced rate limiting recently in 2019 - which has made the API
essentially unusable - CoL+ is coming soon and we'll incorporate it here
when it's stable. See https://github.com/ropensci/colpluz for the R
implementation for CoL+

## Author

Scott Chamberlain

Eduard Szoecs <eduardszoecs@gmail.com>

Zachary Foster <zacharyfoster1989@gmail.com>

Carl Boettiger <cboettig@gmail.com>

Karthik Ram <karthik@ropensci.org>

Ignasi Bartomeus <nacho.bartomeus@gmail.com>

John Baumgartner <johnbb@student.unimelb.edu.au>

James O'Donnell <jodonnellbio@gmail.com>
