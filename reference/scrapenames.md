# Find taxon names using Global Names Recognition and Discovery

Uses the Global Names Recognition and Discovery service, see
http://gnrd.globalnames.org/

NOTE: This function sometimes gives data back and sometimes not. The API
that this function is using is extremely buggy.

## Usage

``` r
scrapenames(
  url = NULL,
  text = NULL,
  format = "csv",
  bytes_offset = FALSE,
  return_content = FALSE,
  unique_names = TRUE,
  ambiguous_names = FALSE,
  no_bayes = FALSE,
  odds_details = FALSE,
  language = "detect",
  words_around = 0,
  verification = TRUE,
  sources = NULL,
  all_matches = FALSE,
  ...,
  file = NULL,
  unique = NULL,
  engine = NULL,
  detect_language = NULL,
  data_source_ids = NULL
)
```

## Arguments

- url:

  (character) If text parameter is empty, and `url` is given, GNfinder
  will process the URL and will find names in the content of its body.

- text:

  (character) Contains the text which will be checked for scientific
  names. If this parameter is not empty, the `url` parameter is ignored.

- format:

  (character) Sets the output format. It can be set to: `"csv"` (the
  default), `"tsv"`, or `"json"`.

- bytes_offset:

  (logical) This changes how the position of a detected name in text is
  calculated. Normally a name's start and end positions are given as the
  number of UTF-8 characters from the beginning of the text. If this is
  `TRUE`, the start and end offsets are recalculated in the number of
  bytes.

- return_content:

  (logical) If this is `TRUE`, the text used for the name detection is
  returned back. This is especially useful if the input was not a plain
  UTF-8 text and had to be prepared for name-finding. Then the returned
  content can be used together with start and end fields of detected
  name-strings to locate the strings in the text.

- unique_names:

  (logical) If this is `TRUE`, the output returns a list of unique
  names, instead of a list of all name occurrences. Unique list of names
  does not provide position information of a name in the text.

- ambiguous_names:

  (logical) If this is `TRUE`, strings which are simultaneously
  scientific names and "normal" words are not filtered out from the
  results. For example, generic names like America, Cancer, Cafeteria
  will be returned in the results.

- no_bayes:

  (logical) If this is `TRUE`, only heuristic algorithms are used for
  name detection.

- odds_details:

  (logical) If `TRUE`, the result will contain odds of all features used
  for calculation of NaiveBayes odds. Odds describe probability of a
  name to be 'real'. The higher the odds, the higher the probability
  that a detected name is not a false positive. Odds are calculated by
  multiplication of the odds of separate features. Odds details explain
  how the final odds value is calculated.

- language:

  (character) The language of the text. Language value is used for
  calculation of Bayesian odds. If this parameter is not given, `"eng"`
  is used by default. Currently only English and German languages are
  supported. Valid values are: `"eng"`, `"deu"`, and `"detect"`.

- words_around:

  (integer) Allows to see the context surrounding a name-string. This
  sets the number of words located immediately before or after a
  detected name. These words are then returned in the output. Default is
  0, maximum value is 5.

- verification:

  (character) When this `TRUE`, there is an additional verification step
  for detected names. This step requires internet connection and uses
  https://verifier.globalnames.org/api/v1 for verification queries.

- sources:

  Pipe separated list of data source ids to resolve found names against.
  See list of Data Sources http://resolver.globalnames.org/data_sources

- all_matches:

  When this option is true all found results are returned, not only the
  bestResults. The bestResult field in this case is null, and results
  field should contain found results of the matches.

- ...:

  Further args passed to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

- file:

  Defunct. If you feel this is important functionality submit an issue
  at "https://github.com/ropensci/taxize"

- unique:

  Defunct. See the `unique_names` option.

- engine:

  Defunct. The API used no longer supports this option.

- detect_language:

  Defunct. See the `language` option.

- data_source_ids:

  Defunct. See the `sources` option.

## Value

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
or list representing parsed JSON output depending on the value of the
`format` option.

## Author

Scott Chamberlain, Zachary Foster

## Examples

``` r
if (FALSE) { # \dontrun{
# Get data from a website using its URL
scrapenames('https://en.wikipedia.org/wiki/Spider')
scrapenames('https://en.wikipedia.org/wiki/Animal')
scrapenames('https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0095068')
scrapenames('https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0080498')

scrapenames(url = 'https://en.wikipedia.org/wiki/Spider', source=c(1, 169))

# Get data from text string
scrapenames(text='A spider named Pardosa moesta Banks, 1892')

# return OCR content
scrapenames(text='A spider named Pardosa moesta Banks, 1892',
            return_content = TRUE, format = 'json')
} # }
```
