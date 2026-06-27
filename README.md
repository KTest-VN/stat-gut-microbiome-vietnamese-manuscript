# Taxonomic and Functional Profiling of Gut Microbiome from Urban Healthy Vietnamese Adults

This repository contains the R analysis code for the manuscript:

> **"Taxonomic and Functional Profiling of Gut Microbiome from a Cohort of Urban Healthy Vietnamese and Health Index Assessment"**  
> *Submitted to PLOS ONE*

---

## Study Overview

Shotgun metagenomic analysis of gut microbiome from 29 apparently healthy urban adults in Ho Chi Minh City, Vietnam. This is an exploratory study providing reference data for an underrepresented populations in microbiome research.

---

## Repository Structure

```
├── analysis/
│   ├── 01_enterotype_clustering.Rmd      # PAM clustering, JSD distance, CH index, silhouette
│   ├── 02_alpha_diversity.Rmd            # Richness, Shannon, Pielou evenness, rarefaction
│   ├── 03_beta_diversity_aitchison.Rmd   # Aitchison distance, PERMANOVA, PCoA plot
│   ├── 04_core_microbiome.Rmd            # Core species, prevalence thresholds, boxplots
│   ├── 05_taxa_LEfSe.Rmd     		       # LEfSe analysis for taxa, LDA scores
│   ├── 06_cooccurrence_network.Rmd       # SparCC bootstrap co-occurrence networks
│   ├── 07_pathway_heatmap.Rmd            # Heatmap of HUMAnN3 MetaCyc pathways
│   ├── 08_pathway_LEfSe.Rmd              # LEfSe analysis for pathways, LDA scores
│   ├── 09_gmwi2_analysis.Rmd             # GMWI2 distribution, cross-population comparison
│   ├── 10_gmwi2_hack_prevalence.Rmd      # HACK taxa prevalence across GMWI2 quartiles
│   └── 11_gmwi2_taxa_heatmap.Rmd         # Heatmap of GMWI2-associated taxa across populations
├── data/
│   └── README_data.md                    # Data description and access instructions
├── output/                               # Generated figures and tables (gitignored)
├── .gitignore
└── README.md
```

---

## Data Availability

Raw sequencing data are deposited at NCBI under BioProject PRJNA1438977.

Sample input data files (place in `data/` directory):

| File | Description | Sheet(s) used |
|------|-------------|---------------|
| `species_abundance.xlsx` | MetaPhlAn3 species-level profiles | `species_relabund`, `species_counts`, `species_counts_transpose` |
| `metadata.xlsx` | Sample metadata (anonymized) | `metadata` |
| `pathway_abundance.xlsx` | HUMAnN3 MetaCyc pathway abundance (CPM) | `pathway_cpm` |
| `gmwi2_scores.xlsx` | GMWI2 scores across populations | `gmwi2`, `gmwi2_taxa` |
| `hack_taxa_list.xlsx` | HACK taxa reference list | Sheet 1 |

> **Note**: Raw sequencing data are not included in this repository.

---

## Dependencies

All analyses were performed in **R v4.4.2**. Required packages:

```r
# CRAN
install.packages(c(
  "readxl", "openxlsx", "writexl", "here",
  "tidyverse", "ggplot2", "ggpubr", "pheatmap", "RColorBrewer",
  "vegan", "cluster", "fpc", "dendextend",
  "phyloseq", "igraph", "ggraph",
  "rstatix", "multcomp", "agricolae", "Hmisc"
))

# Bioconductor
if (!require("BiocManager")) install.packages("BiocManager")
BiocManager::install(c(
  "phyloseq", "microbiomeMarker"
))

# GitHub
devtools::install_github("pmartinezarbizu/pairwiseAdonis/pairwiseAdonis")
devtools::install_github("zhanxw/SpiecEasi")
```

---

## Usage

Each `.Rmd` file is self-contained and can be run independently. Set the following parameters before knitting:

```r
# At the top of each script (params section):
params:
  run_name: "HGM_study"    # prefix for output files
  output_dir: "output"     # output directory path
```

Run a single analysis:
```r
rmarkdown::render("analysis/01_enterotype_clustering.Rmd")
```

---

## Citation

If you use this code, please cite:

> Nguyen et al. Taxonomic and Functional Profiling of Gut Microbiome from a Cohort of Urban Healthy Vietnamese and Health Index Assessment. *PLOS ONE* (under review).

---

## License

Code is released under the [MIT License](LICENSE).
