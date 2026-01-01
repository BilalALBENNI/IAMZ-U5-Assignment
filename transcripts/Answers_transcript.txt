This was done by Bilal AL BENNI and Sasha KASSIS

# Session 3: Analysis of Transcriptomes

## 3.1 How we solved the exercises:

We performed a Weighted Gene Co-expression Network Analysis (WGCNA) using RNA-seq data from watered (W) samples of Brachypodium distachyon. The analysis was conducted in RStudio to identify clusters of co-expressed genes (modules) and correlate them with plant traits.

### 3.1) Samples and Isoforms

The dataset TPM_counts_Drought_W_dataset.csv contains 9,940 isoforms and 40 samples.
### 3.2) Outlier Analysis

Based on hierarchical clustering of the samples, 1 sample was discarded as an outlier. This sample exceeded the established cut height of 300,000, leaving 39 samples for the network construction.
### 3.3) Power Value

The soft-thresholding power was set to 6. This value was chosen because it was the lowest power that allowed the network to reach a Scale-Free Topology fit index (R^2) above 0.85 (specifically 0.879).
### 3.4) Co-expression Modules

    Before merging: 40 modules were identified.

    After merging: 36 modules remained after merging those with a correlation higher than 0.75.

### 3.5) Hub Isoform

The hub isoform identified for the cyan module is Bradi3g43870.1.
### 3.6) Module-Trait Association

The module with the highest positive correlation with the "blwgrd" (below ground biomass) trait is the MEviolet module, with a correlation of 0.66 (p-value=3×10^−4).
## 3.2 Specific Inputs and Outputs:

    Inputs: TPM_counts_Drought_W_dataset.csv (expression data) and TRAITS_W.csv (phenotypic data).

Outputs: Sample dendrogram, Scale-free topology plots, and the Module-trait association heatmap.

### 3.3 Problems Encountered:

The primary difficulty was a system-level configuration issue where RStudio could not install the WGCNA package due to a missing libcurl library on the Linux host. This required manual intervention via the terminal to install libcurl4-openssl-dev before the R analysis could proceed.
### 3.4 Proposed Experiment:
This co-expression analysis could be applied to a study of heat stress response in different cereal ecotypes. By comparing modules between heat-stressed and control groups, one could identify "thermoprotective" hub genes that drive survival in specific varieties.
