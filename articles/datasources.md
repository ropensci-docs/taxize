# taxize data sources

Data sources currently implemented in taxize

| Souce | Function prefix | API Docs | API key |
|:---|:---|:---|:---|
| Encylopedia of Life | `eol` | [link](https://eol.org/docs/what-is-eol/data-services) | none |
| Integrated Taxonomic Information Service | `itis` | [link](https://www.itis.gov/ws_description.html) | none |
| Global Names Resolver | `gnr` | [link](http://resolver.globalnames.org/api) | none |
| Global Names Index | `gni` | [link](https://github.com/dimus/gni/wiki/api) | none |
| IUCN Red List | `iucn` | [link](https://api.iucnredlist.org/) | [link](https://api.iucnredlist.org/) |
| Tropicos | `tp` | [link](http://services.tropicos.org/help) | [link](http://services.tropicos.org/help?requestkey) |
| Theplantlist dot org | `tpl` | \*\* | none |
| National Center for Biotechnology Information | `ncbi` | none | none |
| CANADENSYS Vascan name search API | `vascan` | [link](https://data.canadensys.net/vascan/api) | none |
| International Plant Names Index (IPNI) | `ipni` | none | none |
| Barcode of Life Data Systems (BOLD) | `bold` | [link](https://boldsystems.org/data/api/) | none |
| National Biodiversity Network (UK) | `nbn` | [link](https://data.nbn.org.uk/Documentation/Web_Services/Web_Services-REST/resources/restapi/rest.html) | none |
| Index Fungorum | `fg` | none | none |
| EU BON | `eubon` | [link](https://cybertaxonomy.eu/eubon-utis/doc.html) | none |
| Index of Names (ION) | `ion` | [link](http://www.organismnames.com/) | none |
| Open Tree of Life (TOL) | `tol` | [link](https://github.com/OpenTreeOfLife/germinator/wiki/Open-Tree-of-Life-Web-APIs) | none |
| World Register of Marine Species (WoRMS) | `worms` | [link](https://www.marinespecies.org/aphia.php?p=webservice) | none |
| NatureServe | `natserv` | [link](https://services.natureserve.org/BrowseServices/getSpeciesData/getSpeciesListREST.jsp) | [link](https://services.natureserve.org/developer/index.jsp) |
| Wikipedia | `wiki` | [link](https://www.mediawiki.org/wiki/API:Main_page) | none |
| Kew’s Plants of the World | `pow` | none | none |

\*\*: There are none! We suggest using `TPL` and `TPLck` functions in
the [taxonstand package](https://cran.r-project.org/package=Taxonstand).
We provide two functions to get bulk data: `tpl_families` and `tpl_get`.

\*\*\*: There are none! The function scrapes the web directly.

May be in taxize in the future: See the `datasources` label
(<https://github.com/ropensci/taxize/labels/datasources>) in the issue
tracker
