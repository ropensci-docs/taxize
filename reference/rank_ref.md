# Lookup-table for IDs of taxonomic ranks

data.frame of 46 rows, with 2 columns:

- rankid - a numeric rank id, consecutive

- ranks - a comma separated vector of names that are considered equal to
  one another within the row

## Details

We use this data.frame to do data sorting/filtering based on the
ordering of ranks.

Please let us know if there is a rank that occurs from one of the data
sources taxize that we don't have in `rank_ref` dataset.

Let us know if you disagree with the ordering of ranks.

Note that `rankid` 280 are essentially "genetic variants"; placed just
above 'unspecified' to denote they're not without rank, but they're not
really taxonomic ranks either. As far as I know there's no way to
delineate among these "genetic variant" types.
