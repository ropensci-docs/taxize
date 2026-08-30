# Defunct functions in taxize

The following functions are now defunct (no longer available):

- All COL functions are defunct:
  `as.colid, `col_children`, `col_classification`, `col_downstream`, `col_search`, `get_colid`, `get_colid\_`, `as.data.frame.colid`, `children.colid`, `classification.colid`, `downstream.colid`, `id2name.colid`, `lowest_common.colid`, `synonyms.colid`, `upstream.colid\`

- [`col_classification()`](https://docs.ropensci.org/taxize/reference/col-defunct.md):
  See[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

- [`tp_classification()`](https://docs.ropensci.org/taxize/reference/tp_classification-defunct.md):
  See[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

- [`eol_hierarchy()`](https://docs.ropensci.org/taxize/reference/eol_hierarchy-defunct.md):
  See[`classification()`](https://docs.ropensci.org/taxize/reference/classification.md)

- [`eol_invasive()`](https://docs.ropensci.org/taxize/reference/eol_invasive-defunct.md):
  See `eol` in the originr package.

- [`use_eol()`](https://docs.ropensci.org/taxize/reference/use_eol-defunct.md):
  EOL no longer requires an API key

- [`tpl_search()`](https://docs.ropensci.org/taxize/reference/tpl_search-defunct.md):
  Use the Taxonstand functions `TPL` or `TPLck` directly.

- [`get_seqs()`](https://docs.ropensci.org/taxize/reference/get_seqs-defunct.md):
  This function changed name
  to[`ncbi_getbyname()`](https://docs.ropensci.org/taxize/reference/ncbi_getbyname-defunct.md)()\].

- [`get_genes()`](https://docs.ropensci.org/taxize/reference/get_genes-defunct.md):
  This function changed name
  to[`ncbi_getbyid()`](https://docs.ropensci.org/taxize/reference/ncbi_getbyid-defunct.md)()\].

- [`get_genes_avail()`](https://docs.ropensci.org/taxize/reference/get_genes_avail-defunct.md):
  This function changed name
  to[`ncbi_search()`](https://docs.ropensci.org/taxize/reference/ncbi_search-defunct.md)()\].

- [`ncbi_getbyname()`](https://docs.ropensci.org/taxize/reference/ncbi_getbyname-defunct.md):
  See `ncbi_byname` in the traits package.

- [`ncbi_getbyid()`](https://docs.ropensci.org/taxize/reference/ncbi_getbyid-defunct.md):
  See `ncbi_byid` in the traits package.

- [`ncbi_search()`](https://docs.ropensci.org/taxize/reference/ncbi_search-defunct.md):
  See `ncbi_searcher` in the traits package.

- [`gisd_isinvasive()`](https://docs.ropensci.org/taxize/reference/gisd_invasive-defunct.md):
  See `gisd` in the originr package.

- [`ubio_classification()`](https://docs.ropensci.org/taxize/reference/ubio_classification-defunct.md):
  The uBio web services was down for quite a while, is now (as of
  2016-05-09) back up, but we don't trust that it will stay up and
  available.

- [`ubio_classification_search()`](https://docs.ropensci.org/taxize/reference/ubio_classification_search-defunct.md):
  The uBio web services was down for quite a while, is now (as of
  2016-05-09) back up, but we don't trust that it will stay up and
  available.

- [`ubio_id()`](https://docs.ropensci.org/taxize/reference/ubio_id-defunct.md):
  The uBio web services was down for quite a while, is now (as of
  2016-05-09) back up, but we don't trust that it will stay up and
  available.

- [`ubio_ping()`](https://docs.ropensci.org/taxize/reference/ubio_ping-defunct.md):
  The uBio web services was down for quite a while, is now (as of
  2016-05-09) back up, but we don't trust that it will stay up and
  available.

- [`ubio_search()`](https://docs.ropensci.org/taxize/reference/ubio_search-defunct.md):
  The uBio web services was down for quite a while, is now (as of
  2016-05-09) back up, but we don't trust that it will stay up and
  available.

- [`ubio_synonyms()`](https://docs.ropensci.org/taxize/reference/ubio_synonyms-defunct.md):
  The uBio web services was down for quite a while, is now (as of
  2016-05-09) back up, but we don't trust that it will stay up and
  available.

- [`get_ubioid()`](https://docs.ropensci.org/taxize/reference/get_ubioid-defunct.md):
  The uBio web services are apparently down indefinitely.

- [`phylomatic_tree()`](https://docs.ropensci.org/taxize/reference/phylomatic_tree-defunct.md):
  This function is defunct. See `phylomatic` in the package brranching

- [`phylomatic_format()`](https://docs.ropensci.org/taxize/reference/phylomatic_format-defunct.md):
  This function is defunct. See `phylomatic_names` in the package
  brranching

- [`eubon()`](https://docs.ropensci.org/taxize/reference/eubon-defunct.md):
  This function is defunct. Use
  [`eubon_search()`](https://docs.ropensci.org/taxize/reference/eubon_search.md)

- [`tnrs()`](https://docs.ropensci.org/taxize/reference/tnrs-defunct.md):
  This function is defunct. Was too unreliable

- [`tnrs_sources()`](https://docs.ropensci.org/taxize/reference/tnrs_sources-defunct.md):
  This function is defunct. Was too unreliable
