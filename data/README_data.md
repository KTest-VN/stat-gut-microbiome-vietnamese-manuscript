# Data Directory


## Test Data (`*_TEST.xlsx`)

Synthetic files with **randomly generated values** — for pipeline testing only.
Do not use for biological interpretation.

| File | Replaces | Content |
|------|----------|---------|
| `species_abundance_TEST.xlsx` | `species_abundance.xlsx` | 10 samples × 30 species; sheets: `species_relabund`, `species_counts`, `species_counts_transposed` |
| `metadata_TEST.xlsx` | `metadata.xlsx` | 10 samples; sheet: `metadata` (SampleID, Age, Gender, BMI, Enterotype, GMWI2, GMWI2Q) |
| `pathway_abundance_TEST.xlsx` | `pathway_abundance.xlsx` | 20 MetaCyc pathways (CPM); sheet: `pathway_cpm` |
| `gmwi2_scores_TEST.xlsx` | `gmwi2_scores.xlsx` | 3 mock populations; sheets: `gmwi2`, `gmwi2_taxa` |
| `hack_taxa_list_TEST.xlsx` | `hack_taxa_list.xlsx` | 12 mock HACK taxa; sheet: `hack_taxa_list` |

## Using Test Data

Rename files before running scripts (if any):

```bash
cd data/
for f in *_TEST.xlsx; do cp "$f" "${f/_TEST/}"; done
```

Or edit the `here("data", ...)` paths at the top of each script directly.
