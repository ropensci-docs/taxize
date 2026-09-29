# Get citations and licenses for data sources used in taxize

Get citations and licenses for data sources used in taxize

## Usage

``` r
taxize_cite(fxn = "itis", what = "citation")
```

## Arguments

- fxn:

  Function to search on. A special case is the package name 'taxize'
  that will give the citations for the package.

- what:

  One of citation (default), license, or both.

## Examples

``` r
taxize_cite(fxn='eol_search')
#> Source: eol
#>   Home page: http://eol.org/
#>   API help: http://eol.org/api/
#> 
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues
taxize_cite(fxn='itis_hierarchy')
#> Source: itis
#>   Home page: https://www.itis.gov/
#>   API help: https://www.itis.gov/ws_description.html
#>   Citation: Retrieved [month, day, year], from the Integrated Taxonomic Information System on-line database, https://www.itis.gov.
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues
taxize_cite(fxn='tp_classification')
#> Source: tropicos
#>   Home page: http://tropicos.org/
#>   API help: http://services.tropicos.org/
#> 
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues
taxize_cite(fxn='gbif_ping')
#> Source: gbif
#>   Home page: http://www.gbif.org
#>   API help: http://www.gbif.org/developer/summary
#>   Citation: GBIF (2013). GBIF (Ed.), Global Biodiversity Information Facility Data Portal (2013)
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues
taxize_cite(fxn='plantminer')
#> Source: plantminer
#>   Home page: http://www.plantminer.com/
#>   API help: http://www.plantminer.com/help
#>   Citation: See The Plant List or Tropicos citations
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues
taxize_cite(fxn='get_natservid_')
#> Source: natserv
#>   Home page: http://www.natureserve.org/
#>   API help: https://services.natureserve.org/index.jsp
#>   Citation: Citation: Natureserve. 2017. NatureServe Web Service. Arlington, VA. U.S.A. Available http://services.natureserve.org. (Accessed: <date>)
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues
taxize_cite(fxn='as.natservid')
#> Source: natserv
#>   Home page: http://www.natureserve.org/
#>   API help: https://services.natureserve.org/index.jsp
#>   Citation: Citation: Natureserve. 2017. NatureServe Web Service. Arlington, VA. U.S.A. Available http://services.natureserve.org. (Accessed: <date>)
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues
taxize_cite(fxn='get_wormsid')
#> Source: worms
#>   Home page: http://www.marinespecies.org/
#>   API help: http://www.marinespecies.org/rest/
#>   Citation: We ask you to cite the individual global or regional species lists, or species pages as appropriate. Their citations are shown on their web pages. The database as a whole is to be cited as follows:
#> 
#>      WoRMS Editorial Board (2017). World Register of Marine Species. Available from http://www.marinespecies.org at VLIZ. Accessed <date>. doi:10.14284/170
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues
taxize_cite(fxn='as.wormsid')
#> Source: worms
#>   Home page: http://www.marinespecies.org/
#>   API help: http://www.marinespecies.org/rest/
#>   Citation: We ask you to cite the individual global or regional species lists, or species pages as appropriate. Their citations are shown on their web pages. The database as a whole is to be cited as follows:
#> 
#>      WoRMS Editorial Board (2017). World Register of Marine Species. Available from http://www.marinespecies.org at VLIZ. Accessed <date>. doi:10.14284/170
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues

# Functions that use many data sources
taxize_cite(fxn='synonyms')
#> Source: itis
#>   Home page: https://www.itis.gov/
#>   API help: https://www.itis.gov/ws_description.html
#>   Citation: Retrieved [month, day, year], from the Integrated Taxonomic Information System on-line database, https://www.itis.gov.
#> 
#> Source: tropicos
#>   Home page: http://tropicos.org/
#>   API help: http://services.tropicos.org/
#> 
#> 
#> Source: nbn
#>   Home page: http://www.nbn.org.uk/
#>   API help: https://data.nbn.org.uk/Documentation/Web_Services/
#> 
#> 
#> Source: worms
#>   Home page: http://www.marinespecies.org/
#>   API help: http://www.marinespecies.org/rest/
#>   Citation: We ask you to cite the individual global or regional species lists, or species pages as appropriate. Their citations are shown on their web pages. The database as a whole is to be cited as follows:
#> 
#>      WoRMS Editorial Board (2017). World Register of Marine Species. Available from http://www.marinespecies.org at VLIZ. Accessed <date>. doi:10.14284/170
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues
taxize_cite(fxn='classification')
#> Source: itis
#>   Home page: https://www.itis.gov/
#>   API help: https://www.itis.gov/ws_description.html
#>   Citation: Retrieved [month, day, year], from the Integrated Taxonomic Information System on-line database, https://www.itis.gov.
#> 
#> Source: ncbi
#>   Home page: http://www.ncbi.nlm.nih.gov/taxonomy
#>   API help: http://www.ncbi.nlm.nih.gov/books/NBK25501/
#>   Citation: Federhen S: The NCBI Taxonomy database. Nucleic Acids Res 2012, 40 (Database issue): D136-D143.
#> 
#> Source: gbif
#>   Home page: http://www.gbif.org
#>   API help: http://www.gbif.org/developer/summary
#>   Citation: GBIF (2013). GBIF (Ed.), Global Biodiversity Information Facility Data Portal (2013)
#> 
#> Source: eol
#>   Home page: http://eol.org/
#>   API help: http://eol.org/api/
#> 
#> 
#> Source: troicos
#>   Home page: http://tropicos.org/
#>   API help: http://services.tropicos.org/
#> 
#> 
#> Source: nbn
#>   Home page: http://www.nbn.org.uk/
#>   API help: https://data.nbn.org.uk/Documentation/Web_Services/
#> 
#> 
#> Source: worms
#>   Home page: http://www.marinespecies.org/
#>   API help: http://www.marinespecies.org/rest/
#>   Citation: We ask you to cite the individual global or regional species lists, or species pages as appropriate. Their citations are shown on their web pages. The database as a whole is to be cited as follows:
#> 
#>      WoRMS Editorial Board (2017). World Register of Marine Species. Available from http://www.marinespecies.org at VLIZ. Accessed <date>. doi:10.14284/170
#> 
#> Source: natserv
#>   Home page: http://www.natureserve.org/
#>   API help: https://services.natureserve.org/index.jsp
#>   Citation: Citation: Natureserve. 2017. NatureServe Web Service. Arlington, VA. U.S.A. Available http://services.natureserve.org. (Accessed: <date>)
#> 
#> Can any of these citations be improved? https://github.com/ropensci/taxize/issues

# Get the taxize citation
taxize_cite(fxn='taxize')
#> The paper:
#> Scott Chamberlain and Eduard Szocs (2013). taxize - taxonomic search
#> and retrieval in R. F1000Research, 2:191. URL:
#> https://f1000research.com/articles/2-191/v2
#> 
#> A BibTeX entry for LaTeX users is
#> 
#>   @Article{,
#>     title = {taxize - taxonomic search and retrieval in R},
#>     journal = {F1000Research},
#>     author = {{Scott Chamberlain} and {Eduard Szocs}},
#>     year = {2013},
#>     url = {https://f1000research.com/articles/2-191/v2},
#>   }
#> 
#> The software:
#> Scott Chamberlain, Eduard Szoecs, Zachary Foster, Zebulun Arendsee,
#> Carl Boettiger, Karthik Ram, Ignasi Bartomeus, John Baumgartner, James
#> O'Donnell, Jari Oksanen, Bastian Greshake Tzovaras, Philippe Marchand,
#> Vinh Tran, Maëlle Salmon, Gaopeng Li, and Matthias Grenié. (2020)
#> taxize: Taxonomic information from around the web. R package version
#> 0.9.98. https://github.com/ropensci/taxize
#> 
#> A BibTeX entry for LaTeX users is
#> 
#>   @Manual{,
#>     title = {taxize: Taxonomic information from around the web},
#>     author = {Scott Chamberlain and Eduard Szoecs and Zachary Foster and Zebulun Arendsee and Carl Boettiger and Karthik Ram and Ignasi Bartomeus and John Baumgartner and James O'Donnell and Jari Oksanen and Bastian Greshake Tzovaras and Philippe Marchand and Vinh Tran and Maëlle Salmon and Gaopeng Li and Matthias Grenié},
#>     year = {2020},
#>     note = {R package version 0.9.98},
#>     url = {https://github.com/ropensci/taxize},
#>   }

# Get license information
taxize_cite(fxn='taxize', "license")
#> License: MIT
#> URL:     https://opensource.org/licenses/MIT
```
