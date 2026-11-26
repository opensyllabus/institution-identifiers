# Institution Identifiers

> **This repository is no longer maintained.** `latest.csv` was last updated in
> May 2025 and will not change. Its successor is
> [**os-institutions**](https://github.com/opensyllabus/os-institutions), which
> builds the same ROR / GRID / IPEDS / Wikidata crosswalk reproducibly and
> publishes it with every release.

## Moving to os-institutions

The `institutions.parquet` asset on each
[os-institutions release](https://github.com/opensyllabus/os-institutions/releases)
has the same columns as `latest.csv` (`ror_id`, `grid_id`, `wikidata_id`,
`unitid`, `name`), plus more (URLs, coordinates, alternate names, ...).

From Python:

```python
import os_institutions

dataset = os_institutions.load_dataset()  # pandas DataFrame
crosswalk = dataset[["ror_id", "grid_id", "wikidata_id", "unitid", "name"]]
crosswalk.to_csv("latest.csv", index=False)
```

or download `institutions.parquet` from the latest release directly. See the
[os-institutions README](https://github.com/opensyllabus/os-institutions#readme)
for installation and for the institution matcher.

Row counts and coverage differ from the old CSV, since the new dataset is
rebuilt from current ROR, IPEDS and Wikidata data.

## Legacy schema

`ror_id`: [Research Organization Registry](https://ror.org/) (ROR) identifier. Educational institutions only.

`grid_id`: [Global Research Identifier Database](https://www.grid.ac/) (GRID) identifier. GRID has been deprecated and superseded by ROR.

`wikidata_id`: [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) identifier. Used for creating the crosswalk between identifiers.

`unitid`: [Integrated Postsecondary Education Data System](https://nces.ed.gov/ipeds) (IPEDS) identifier. US only by nature.

`name`: Name of the institution. There may be some errors and/or the exact name might be different from other records.

## Reporting issues

Please open issues for the dataset or matcher in
[os-institutions](https://github.com/opensyllabus/os-institutions/issues).
