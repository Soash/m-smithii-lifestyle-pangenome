# Dataset & Pangenome Artifacts Directory

This directory stores curated metadata, MAG cohorts, gene presence/absence matrices, and statistical association tables for the *Methanobrevibacter smithii* lifestyle-associated pangenomic investigation.

---

## 1. Directory Structure & Key Files

```
data/
├── hq_m_smithii.tsv                         # High-quality M. smithii MAGs (n=221; completeness >=90%, contamination <=5%)
├── industrialized_m_smithii.tsv             # Industrialized cohort MAGs (n=146; UK and USA) with direct MGnify FTP URLs
├── non_industrialized_m_smithii.tsv         # Non-industrialized cohort MAGs (n=75; Fiji, Peru, Madagascar) with direct FTP URLs
├── m_smithii_map.txt                        # PanACoTA-compatible isolate-to-cohort mapping file
│
├── Supplementary_Table_1_MAG_Metrics.csv    # Consolidated MAG metrics: accession, cohort, country, completeness, contamination
├── lifestyle_specific_genes.csv             # Statistical gene association table (Chi-Square / Fisher exact test)
├── FINAL_annotated_lifestyle_genes.csv      # Functional annotations of lifestyle-associated gene families
├── FINAL_annotated_lifestyle_genes_filtered.csv # High-confidence candidates passing strict FDR correction (q < 0.05)
├── FINAL_annotated_lifestyle_genes_qvalues.csv  # Multiple testing correction FDR q-values
│
├── r_heatmap_data.csv                       # Curated matrix subset for publication heatmap generation in R
├── r_metadata.csv                           # Sample metadata aligned with r_heatmap_data.csv
├── itol_color_strip.txt                     # iTOL tree annotation: lifestyle color strip (Industrialized vs Non-Industrialized)
├── itol_heatmap.txt                         # iTOL tree annotation: gene presence/absence matrix overlay
│
├── m_smithii_matrix/
│   └── matrix.csv                           # Gene presence/absence binary matrix across 221 MAGs (loaded by notebook)
│
└── m_smithii_pangenome_out/
    ├── partitions/                          # Pangenome compartment gene lists:
    │   ├── exact_core.txt                   # Genes in 100% of genomes
    │   ├── soft_core.txt                    # Genes in >=95% of genomes
    │   ├── persistent.txt                   # Core persistent genes
    │   ├── shell.txt                        # Intermediate frequency genes (15% - 95%)
    │   ├── cloud.txt                        # Low frequency strain-specific genes (<15%)
    │   ├── soft_accessory.txt               # Accessory genome (<95%)
    │   └── exact_accessory.txt              # Accessory genome (<100%)
    ├── genomes_statistics.tsv               # Per-genome CDS and sequence length statistics
    ├── mean_persistent_duplication.tsv      # Core gene duplication assessment
    ├── gene_presence_absence.Rtab           # Roary-compatible presence/absence tabular matrix
    └── pangenomeGraph_light.gexf            # Lightweight pangenome graph network for Gephi
```

---

## 2. External Data Retrieval (Large Reference Dumps)

Due to GitHub's 100 MB single-file limitation, large raw reference archives and bulk intermediate sequence files are excluded from version control via `.gitignore`. They can be reproduced or retrieved using the following commands:

### Complete MGnify Gut Catalog Metadata (110 MB)
To download the full uncompressed human gut catalog v2.0.2 metadata:
```bash
wget -P data/ https://ftp.ebi.ac.uk/pub/databases/metagenomics/mgnify_genomes/human-gut/v2.0.2/genomes-all_metadata.tsv
```

### Raw GFF Genome Assemblies (221 MAGs, ~476 MB)
All 221 selected MAGs can be directly fetched from the official EMBL-EBI MGnify FTP repository using the download links in `industrialized_m_smithii.tsv` and `non_industrialized_m_smithii.tsv`:
```bash
mkdir -p data/genomes/industrialized data/genomes/non_industrialized

# Download industrialized genomes (UK, USA)
awk -F '\t' '{print $20}' data/industrialized_m_smithii.tsv | xargs -n 1 wget -P data/genomes/industrialized/

# Download non-industrialized genomes (Fiji, Peru, Madagascar)
awk -F '\t' '{print $20}' data/non_industrialized_m_smithii.tsv | xargs -n 1 wget -P data/genomes/non_industrialized/
```
