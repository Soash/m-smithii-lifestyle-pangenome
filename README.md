# Host Industrialization Drives Dietary-Dependent Structural Variation and Gene Shedding in the Human Gut Archaeon *Methanobrevibacter smithii*

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1-ZKFKmX9j_sWk19xfGzZq70B_CoDLOGp?usp=drive_link)
[![GitHub Repository](https://img.shields.io/badge/GitHub-Repository-blue?logo=github)](https://github.com/Soash/m-smithii-lifestyle-pangenome)
[![Dataset](https://img.shields.io/badge/UHGG-v2.0.2-green)](https://www.ebi.ac.uk/metagenomics/)

**Md Abu Sadat Soash**  
*Department of Genetic Engineering and Biotechnology* <br>
*Shahjalal University of Science and Technology, Sylhet, Bangladesh*  
*Email:* [soash.sadat@gmail.com](mailto:soash.sadat@gmail.com)

---

## Abstract

* **Background:** *Methanobrevibacter smithii* is the dominant archaeal keystone species in the human gut, playing a crucial role in syntrophic hydrogen removal. While bacterial responses to host industrialization and Westernized diets are well documented, the adaptive capacity of the gut archaeome remains largely unexplored due to an over-reliance on 16S rRNA amplicon sequencing.
* **Methods:** To investigate archaeal structural adaptation, we conducted a pan-metagenomic analysis of 219 high-quality *M. smithii* Metagenome-Assembled Genomes (MAGs) retrieved from the UHGG catalog. We stratified the genomes into an Industrialized cohort (US and UK; n=172) and a Non-Industrialized cohort (Peru, Fiji, Madagascar; n=47) to identify lifestyle-specific accessory gene biomarkers.
* **Results:** *M. smithii* possesses a highly open pangenome, with a massive cloud genome constituting 77.4% of its genetic repertoire. Statistical enrichment analysis revealed a striking pattern of diet-driven gene shedding. Industrialized strains exhibited a near-total loss of genes related to Vitamin B12 scavenging (BtuC/D) and Lysine biosynthesis, reflecting an adaptation to nutrient-dense Western diets. Conversely, industrialized strains showed significant enrichment in methanogenesis optimization genes, notably the polyferredoxin protein MvhB.
* **Conclusion:** Our findings demonstrate that *M. smithii* is not a static monolithic entity but a highly dynamic symbiote. Its accessory genome is actively sculpted by host dietary history and localized ecological pressures, highlighting the necessity of strain-level structural analysis in understanding microbiome evolution.

---

## 1. Introduction

The human gut microbiome is intimately linked to host health, metabolism, and immune function. While the bacterial fraction of this ecosystem has been exhaustively characterized across diverse human populations, the archaeome, often termed the "dark matter" of the gut microbiome, remains critically understudied. *Methanobrevibacter smithii* is the dominant archaeal keystone species in the human gut, responsible for converting bacterial fermentation byproducts (hydrogen and carbon dioxide) into methane [1]. This syntrophic removal of hydrogen gas is vital for maintaining the thermodynamic efficiency of the entire gut microbial ecosystem.

Recent macro-ecological studies have demonstrated that industrialization—characterized by increased sanitation, antibiotic use, and shifts toward Westernized diets high in animal protein and low in complex fibers—fundamentally alters gut microbiome composition [2], [3]. However, these studies predominantly rely on 16S rRNA amplicon sequencing, treating *M. smithii* as a monolithic, static entity. Genomic structural variation, particularly within the accessory genome, is a primary mechanism by which microbes adapt to localized environmental pressures. We hypothesize that the accessory genome of *M. smithii* is not randomly distributed but is actively sculpted by the industrialized status and dietary habits of the human host. In this study, we utilize a pan-metagenomic approach across 219 high-quality *M. smithii* Metagenome-Assembled Genomes (MAGs) to identify specific, structurally conserved metabolic adaptations driven by host lifestyle.

---

## 2. Methodology

### 2.1 Genomic Data Acquisition and Cohort Definition

A total of 219 high-quality *M. smithii* MAGs were retrieved from the MGnify Unified Human Gastrointestinal Genome (UHGG) catalog (v2.0.2) [4]. To ensure robust downstream genomic comparisons and prevent false-positive inflation of the accessory genome, strict quality control thresholds were applied prior to pangenome construction. Genome completeness and contamination were assessed utilizing the CheckM lineage-specific workflow, and only MAGs meeting the high-quality criteria of >90% completeness and <5% contamination were retained for analysis ([Supplementary Figure 2](#supplementary-figures); [Supplementary Table 1](file:///sup/Supplementary_Table_1_MAG_Metrics.csv)) [5].

To isolate the effects of host industrialization and minimize confounding dietary variables, strict geographic inclusion criteria were applied:
* **Industrialized cohort ($n = 172$):** Restricted to MAGs originating from the United States and the United Kingdom, representing archetypal Western diets and lifestyles.
* **Non-Industrialized cohort ($n = 47$):** Comprised of MAGs from Peru, Fiji, and Madagascar, representing traditional, agrarian, or rural dietary baselines.

Genomes from transitional economies, regions with distinct Mediterranean or Nordic dietary patterns, and those with ambiguous metadata were excluded from the primary analysis to prevent lifestyle admixture from attenuating statistical signals.

<p align="center">
  <img src="fig/Fig_1_v2.png" alt="Figure 1: Bioinformatics Pipeline Workflow" width="85%" />
</p>

**Figure 1: Bioinformatics Pipeline Workflow.** A systematic overview of the analytical framework: (1) Retrieval of *M. smithii* MAGs from the MGnify UHGG catalog (v2.0.2) with strict CheckM quality filtering (>90% completeness, <5% contamination); (2) Cohort stratification into Industrialized (US/UK, $n=172$) and Non-Industrialized (Peru/Fiji/Madagascar, $n=47$); (3) Graph-based pangenome construction and partitioning via PPanGGOLiN; (4) Persistent genome core alignment and FastTree phylogenomic reconstruction; and (5) Accessory gene statistical enrichment via Fisher's Exact Test with False Discovery Rate (FDR) correction.

### 2.2 Pangenome Construction and Partitioning

The pangenome graph was constructed and partitioned using PPanGGOLiN (v2.3.0) [6]. Genes were clustered into homologous families and statistically partitioned into:
* **Persistent genome:** Core gene families present in $\ge 95\%$ of genomes.
* **Shell genome:** Accessory gene families present at intermediate frequencies, conserved in distinct subpopulations.
* **Cloud genome:** Rare accessory gene families present in low frequencies or unique to single strains.

### 2.3 Phylogenetic Analysis

To establish the evolutionary relationships between strains, the persistent genome was utilized to generate a multiple sequence alignment using the MAFFT algorithm integrated within the PPanGGOLiN pipeline [7]. Polytomies were resolved to strictly bifurcating nodes, and negative branch lengths were corrected to ensure topological integrity. A robust phylogenetic tree was constructed utilizing FastTree via the Galaxy Server [8], [9]. To establish the directionality of evolutionary divergence, the resulting phylogeny was subjected to midpoint rooting. The rooted tree was subsequently visualized with overlaid accessory genome metadata matrices using the Interactive Tree Of Life (iTOL), with branch lengths ignored to emphasize the evolutionary branching patterns and topological clustering between cohorts [10].

### 2.4 Statistical Enrichment and Functional Annotation

Differential abundance of accessory gene families between the Industrialized and Non-Industrialized cohorts was calculated using Fisher's Exact Test. To account for multiple testing across the entire pangenome, all p-values were corrected using the False Discovery Rate (FDR) Benjamini-Hochberg procedure.

Functional annotations for gene families exhibiting significant lifestyle specificity were retrieved directly from the MGnify UHGG GFF annotations. Hypothetical proteins lacking defined functional domains were filtered out to isolate specific, biologically characterized metabolic pathways driving host-specific adaptation.

---

## 3. Results

### 3.1 Pangenomic and Phylogenetic Separation

<p align="center">
  <img src="fig/Fig_2.png" alt="Figure 2: Pangenome Partitioning" width="48%" />
  <img src="fig/Fig_3_v2.png" alt="Figure 3: Phylogenomic Analysis" width="48%" />
</p>

**Figure 2 (Left): *M. smithii* Pangenome Structure ($n=219$).** Distribution of gene families across the persistent, shell, and cloud partitions. The persistent genome comprises 13.5% (1,400 families), while the accessory genome is overwhelmingly dominant, split into the shell genome (9.1%, 944 families) and a massive cloud genome (77.4%, 8,047 families).

**Figure 3 (Right): Phylogenomic Analysis of the Persistent Genome.** Maximum-likelihood phylogenetic tree constructed from the 1,400 persistent gene families, annotated with host lifestyle metadata and accessory gene biomarkers. The inner ring denotes host lifestyle (Red: Industrialized, Blue: Non-Industrialized). The outer heatmap illustrates the presence (dark) or absence (white) of key metabolic structural variations, highlighting the clade-specific loss of Vitamin B12 transport systems (`btuC`/`btuD`) and lysine biosynthesis in industrialized hosts.

Analysis of the 219 *M. smithii* MAGs revealed a highly open pangenome structure comprising a total of **10,391 distinct gene families**. The persistent genome—representing the conserved genetic core—constituted only 13.5% (1,400 families) of the total genetic repertoire. In contrast, the accessory genome was overwhelmingly dominant, partitioned into a moderately conserved shell genome of 9.1% (944 families) and a massive cloud genome comprising 77.4% (8,047 families) (**Figure 2**). This vast repository of rare, strain-specific cloud genes indicates extensive horizontal gene transfer and underscores the organism's capacity for rapid, localized adaptation to distinct gut environments.

Phylogenetic reconstruction based on the persistent gene families demonstrated distinct evolutionary clustering driven by host lifestyle (**Figure 3**). Strains isolated from non-industrialized hosts frequently formed distinct evolutionary clades from those isolated from industrialized hosts, suggesting that host environmental pressures exert strong selective forces on overall archaeal genome structure. Principal Coordinate Analysis (PCoA) of the accessory genome further supports this, revealing global structural variations that align with host industrialization status ([Supplementary Figure 1](#supplementary-figures)).

### 3.2 Lifestyle-Specific Accessory Gene Biomarkers

Statistical enrichment analysis of the accessory genome identified highly specific structural variations distinguishing the two cohorts (**Table 1**). A notable loss of key biosynthetic and nutrient scavenging genes was observed in the Industrialized cohort:
* **Lysine Biosynthesis Shedding:** The gene family encoding 2,3,4,5-tetrahydropyridine-2,6-dicarboxylate N-acetyltransferase, a critical enzyme for Lysine biosynthesis, was completely absent (0.00% prevalence) in industrialized strains but conserved in 36.17% of non-industrialized strains (FDR-adjusted $q = 9.23 \times 10^{-10}$; $p = 3.01 \times 10^{-13}$).
* **Environmental Sensing & Signal Transduction Depletion:** The gene family encoding the Sensor histidine kinase RcsC was heavily depleted in the industrialized cohort (22.67% prevalence) compared to the non-industrialized baseline (70.21% prevalence) (FDR-adjusted $q = 3.23 \times 10^{-6}$; $p = 3.16 \times 10^{-9}$). This suggests that the constant, heavily processed nutritional environment of the Western gut relaxes selective pressure to maintain complex environmental monitoring systems.

**Table 1: Statistically Significant Lifestyle-Associated Accessory Gene Biomarkers in *M. smithii*.**

| Gene Family ID | Biological Function / Annotation | <nobr>Industrialized (%)</nobr><br>($n=172$) | <nobr>Non-Industrialized (%)</nobr><br>($n=47$) | <nobr>Raw&nbsp;*p*-value</nobr> | <nobr>FDR&nbsp;*q*-value</nobr> | Functional Impact |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- |
| `MGYG000211034_00116` | 2,3,4,5-tetrahydropyridine-2,6-dicarboxylate N-acetyltransferase | 0.00% | 36.17% | <nobr>3.01&nbsp;×&nbsp;10<sup>-13</sup></nobr> | <nobr>9.23&nbsp;×&nbsp;10<sup>-10</sup></nobr> | Complete loss of Lysine synthesis in Western diets |
| `MGYG000259779_00903` | Sensor histidine kinase RcsC | 22.67% | 70.21% | <nobr>3.16&nbsp;×&nbsp;10<sup>-9</sup></nobr> | <nobr>3.23&nbsp;×&nbsp;10<sup>-6</sup></nobr> | Depletion of environmental sensing machinery |
| `MGYG000211034_01500` | Cobalamin import system permease protein BtuC | 50.00% | 91.49% | <nobr>7.88&nbsp;×&nbsp;10<sup>-8</sup></nobr> | <nobr>5.36&nbsp;×&nbsp;10<sup>-5</sup></nobr> | Loss of high-affinity Vitamin B12 permease |
| `MGYG000259779_01487` | Vitamin B12 import ATP-binding protein BtuD | 8.72% | 42.55% | <nobr>3.42&nbsp;×&nbsp;10<sup>-7</sup></nobr> | <nobr>1.75&nbsp;×&nbsp;10<sup>-4</sup></nobr> | Loss of active Vitamin B12 import ATPase |
| `MGYG000155887_00579` | Vitamin B12-binding protein | 50.00% | 89.36% | <nobr>5.90&nbsp;×&nbsp;10<sup>-7</sup></nobr> | <nobr>2.41&nbsp;×&nbsp;10<sup>-4</sup></nobr> | Depletion of extracellular cobalamin capture |
| `MGYG000259779_01153` | ATP synthase subunit c | 93.02% | 61.70% | <nobr>6.33&nbsp;×&nbsp;10<sup>-7</sup></nobr> | <nobr>2.41&nbsp;×&nbsp;10<sup>-4</sup></nobr> | Enrichment in energy coupling & ATP generation |
| `MGYG000171336_01359` | Polyferredoxin protein MvhB | 81.40% | 44.68% | <nobr>1.63&nbsp;×&nbsp;10<sup>-6</sup></nobr> | <nobr>2.83&nbsp;×&nbsp;10<sup>-4</sup></nobr> | Methanogenesis electron bifurcation optimization |
| `MGYG000190668_00503` | Beta-barrel assembly-enhancing protease | 12.21% | 42.55% | <nobr>1.15&nbsp;×&nbsp;10<sup>-5</sup></nobr> | <nobr>1.76&nbsp;×&nbsp;10<sup>-3</sup></nobr> | Depletion of membrane assembly machinery |

### 3.3 Shifts in Nutrient Scavenging and Methanogenesis

Significant divergence was observed in the machinery responsible for Vitamin B12 (cobalamin) acquisition:
* Cobalamin import system permease proteins (BtuC) and Vitamin B12 import ATP-binding proteins (BtuD) were enriched in non-industrialized strains (up to 91.49% prevalence) compared to their industrialized counterparts (falling to as low as 8.72% prevalence) (FDR-adjusted $q < 0.002$).
* Conversely, industrialized strains exhibited marked enrichment in specific methanogenesis and energy-yielding components, notably the **polyferredoxin protein MvhB** (81.40% vs. 44.68%, FDR-adjusted $q = 2.83 \times 10^{-4}$) and **ATP synthase subunit c** (93.02% vs. 61.70%, FDR-adjusted $q = 1.26 \times 10^{-4}$).

---

## 4. Discussion

The results of this pan-metagenomic analysis provide compelling evidence that *Methanobrevibacter smithii* is a dynamic symbiote whose structural genome is actively sculpted by host industrialization. 

### Dietary Scavenging vs. Evolutionary Gene Shedding
The striking loss of Vitamin B12 scavenging machinery (BtuC/BtuD) and Lysine biosynthesis enzymes in Western/industrialized clades is indicative of host-diet-driven genome reduction. Western diets are characteristically dense in animal proteins and fats, providing an overabundance of free amino acids and cobalamin in the gut lumen. In this nutrient-rich environment, the energetic cost of maintaining endogenous high-affinity B12 pumps and Lysine synthetic factories outweighs their benefit, leading to evolutionary gene shedding. 

In contrast, traditional, non-industrialized diets—often heavily reliant on complex, plant-based carbohydrates and lower in animal products—create a gut environment where essential micronutrients are scarce. *M. smithii* strains inhabiting non-industrialized hosts face intense selective pressure to retain structural genes necessary to scavenge sparse Vitamin B12 and autonomously synthesize essential amino acids to survive.

### Methanogenesis Pathway Adaptation
The enrichment of the polyferredoxin protein MvhB in industrialized strains indicates structural adaptation within the core methanogenesis machinery. Industrialized diets drastically alter the bacterial communities responsible for primary saccharolytic fermentation. This shifts the stoichiometric availability of hydrogen gas ($\text{H}_2$), forcing Western *M. smithii* strains to optimize their electron bifurcation and methanogenic throughput to remain competitive in consuming metabolic byproducts.

### Study Limitations
Despite these robust genomic signatures, our analysis is constrained by the metadata resolution inherent to public metagenomic repositories:
1. **Geographic Stratification as a Proxy:** While geographic cohort selection serves as a reliable macro-level proxy for industrialization, it cannot capture individual-level variables such as exact daily dietary intake, lifetime antibiotic exposure, or specific host metabolic phenotypes.
2. **Archaeal Functional "Dark Matter":** A substantial proportion of the divergent accessory genome identified by PPanGGOLiN consists of hypothetical proteins lacking functional characterization. This highlights limitations in existing archaeal annotation databases and emphasizes the need for future *in vitro* cultivation, metabolomics, transcriptomics, and longitudinal human cohort studies with rigorous nutritional tracking.

Ultimately, *M. smithii* should no longer be viewed as a static species, but rather as an adaptable organism whose genome serves as a biological ledger of human dietary history.

---

## 5. Conclusion

This pan-metagenomic analysis demonstrates that the human gut archaeon *Methanobrevibacter smithii* undergoes profound structural genomic adaptation in response to host industrialization. By partitioning the pangenome of 219 high-quality MAGs, we revealed that the *M. smithii* accessory genome acts as a dynamic repository tailored to specific gut microenvironments:
1. Strains inhabiting industrialized hosts undergo extensive evolutionary gene shedding, discarding biosynthetically expensive micronutrient scavenging pathways (Vitamin B12 and Lysine) due to dietary overabundance in Western food systems.
2. Industrialized strains optimize their core methanogenic machinery (polyferredoxin MvhB and ATP synthase) to adapt to altered microbial fermentation byproducts and hydrogen kinetics.

These findings highlight the limitations of relying solely on species-level 16S rRNA amplicon sequencing and establish that host lifestyle exerts severe selective pressures at the sub-species structural level. Recognizing *M. smithii* as a genetically fluid symbiote provides a critical framework for understanding how modern lifestyles alter the ancient thermodynamic and metabolic balance of the human gut.

---

## 6. Supplementary Figures & Data

<p align="center">
  <img src="sup/Supp_Fig_1_PCoA.png" alt="Supplementary Figure 1: PCoA of Accessory Genome" width="48%" />
  <img src="sup/Supp_Fig_2_MAG_Quality.png" alt="Supplementary Figure 2: MAG Quality Metrics" width="48%" />
</p>

* **Supplementary Figure 1 (Left): Principal Coordinates Analysis (PCoA) of the Accessory Genome.** 2D projection based on accessory gene presence/absence matrices (Red: Industrialized, Blue: Non-Industrialized). Two primary structural clusters are observed across populations, demonstrating that the observed metabolic gene losses represent convergent adaptations rather than simple geographical lineage isolation.
* **Supplementary Figure 2 (Right): CheckM Quality Evaluation of Retrieved MAGs ($n=219$).** Distribution of completeness versus contamination percentages across the analyzed *M. smithii* genomes. Dashed lines denote the strict inclusion thresholds (>90% completeness, <5% contamination). Both cohorts display high assembly quality without systematic sequencing bias.

### Supplementary Data Assets

| File Name | Description |
| :--- | :--- |
| [`Supplementary_Table_1_MAG_Metrics.csv`](file:///sup/Supplementary_Table_1_MAG_Metrics.csv) | CheckM completeness, contamination, genome length, GC%, and country metadata for all 219 MAGs |
| [`Final_annotated_lifestyle_genes_filtered.csv`](file:///sup/Final_annotated_lifestyle_genes_filtered.csv) | Annotated accessory gene families with prevalence, raw $p$-values, and functional annotations |
| [`m_smithii_persistent_tree.nhx`](file:///sup/m_smithii_persistent_tree.nhx) | FastTree-generated Newick/NHX phylogenetic tree inferred from the persistent core genome |
| [`itol_color_strip.txt`](file:///sup/itol_color_strip.txt) | iTOL annotation strip defining the Industrialized (Red) vs. Non-Industrialized (Blue) cohorts |
| [`itol_heatmap.txt`](file:///sup/itol_heatmap.txt) | iTOL annotation matrix for accessory gene presence/absence heatmap visualization |

---

## 7. Code and Reproducibility

All primary bioinformatic and statistical workflows are documented in the interactive Jupyter Notebook [`m-smithii-lifestyle-pangenome.ipynb`](file:///m-smithii-lifestyle-pangenome.ipynb).

### Interactive Execution (Google Colab)
The analysis pipeline is configured for single-click execution in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1-ZKFKmX9j_sWk19xfGzZq70B_CoDLOGp?usp=drive_link)

* **Automated Environment:** Package dependencies and binary tools (including Conda and statistical libraries) are installed automatically upon execution via `condacolab`.
* **Phylogenetic Reproduction (iTOL):**
  1. Upload `sup/m_smithii_persistent_tree.nhx` to the [Interactive Tree Of Life (iTOL)](https://itol.embl.de/).
  2. Drag and drop `itol_color_strip.txt` to display host cohort stratification.
  3. Drag and drop `itol_heatmap.txt` to render the presence/absence profiles of lifestyle biomarker genes.

---

## 8. References

1. B. S. Samuel *et al.*, “Genomic and metabolic adaptations of *Methanobrevibacter smithii* to the human gut,” *Proc. Natl. Acad. Sci.*, vol. 104, no. 25, pp. 10643–10648, Jun. 2007, doi: [10.1073/pnas.0704189104](https://doi.org/10.1073/pnas.0704189104).
2. E. D. Sonnenburg and J. L. Sonnenburg, “The ancestral and industrialized gut microbiota and implications for human health,” *Nat. Rev. Microbiol.*, vol. 17, no. 6, pp. 383–390, Jun. 2019, doi: [10.1038/s41579-019-0191-8](https://doi.org/10.1038/s41579-019-0191-8).
3. T. Yatsunenko *et al.*, “Human gut microbiome viewed across age and geography,” *Nature*, vol. 486, no. 7402, pp. 222–227, Jun. 2012, doi: [10.1038/nature11053](https://doi.org/10.1038/nature11053).
4. A. Almeida *et al.*, “A unified catalog of 204,938 reference genomes from the human gut microbiome,” *Nat. Biotechnol.*, vol. 39, no. 1, pp. 105–114, Jan. 2021, doi: [10.1038/s41587-020-0603-3](https://doi.org/10.1038/s41587-020-0603-3).
5. D. H. Parks, M. Imelfort, C. T. Skennerton, P. Hugenholtz, and G. W. Tyson, “CheckM: assessing the quality of microbial genomes recovered from isolates, single cells, and metagenomes,” *Genome Res.*, vol. 25, no. 7, pp. 1043–1055, Jul. 2015, doi: [10.1101/gr.186072.114](https://doi.org/10.1101/gr.186072.114).
6. G. Gautreau *et al.*, “Correction: PPanGGOLiN: Depicting microbial diversity via a partitioned pangenome graph,” *PLOS Comput. Biol.*, vol. 17, no. 12, p. e1009687, Dec. 2021, doi: [10.1371/journal.pcbi.1009687](https://doi.org/10.1371/journal.pcbi.1009687).
7. K. Katoh, “MAFFT: a novel method for rapid multiple sequence alignment based on fast Fourier transform,” *Nucleic Acids Res.*, vol. 30, no. 14, pp. 3059–3066, Jul. 2002, doi: [10.1093/nar/gkf436](https://doi.org/10.1093/nar/gkf436).
8. The Galaxy Community *et al.*, “The Galaxy platform for accessible, reproducible and collaborative biomedical analyses: 2022 update,” *Nucleic Acids Res.*, vol. 50, no. W1, pp. W345–W351, Jul. 2022, doi: [10.1093/nar/gkac247](https://doi.org/10.1093/nar/gkac247).
9. M. N. Price, P. S. Dehal, and A. P. Arkin, “FastTree 2 – Approximately Maximum-Likelihood Trees for Large Alignments,” *PLoS ONE*, vol. 5, no. 3, p. e9490, Mar. 2010, doi: [10.1371/journal.pone.0009490](https://doi.org/10.1371/journal.pone.0009490).
10. I. Letunic and P. Bork, “Interactive Tree of Life (iTOL) v6: recent updates to the phylogenetic tree display and annotation tool,” *Nucleic Acids Res.*, vol. 52, no. W1, pp. W78–W82, Jul. 2024, doi: [10.1093/nar/gkae268](https://doi.org/10.1093/nar/gkae268).
