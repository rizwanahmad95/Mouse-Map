# Mouse Atlas Project

A single-cell transcriptomic atlas of neuroblastoma in preclinical mouse models. This project integrates in-house and public scRNA-seq datasets to map the tumor and immune microenvironment.

### The contents of this repository have been kept private until publication. The content can be shared upon reasonable request.

## 🔬 Project Overview

- **Goal**: This project aims to construct an integrated single-cell RNA-seq (and some single-nucleus data) reference atlas of mouse neuroblastoma tumors by combining data from four independent studies.
- **Data**: Includes one in-house dataset and three public datasets.
-         Chapple2024 - scRNAseq in Dbh-iCre;LSL-MYCN mouse model of neuroblasoma: GSE229226
-         Van De Velde2021 - Neuroblastoma Formation Requires Unconventional CD4 T Cells and Arginase-1–Dependent Myeloid Cells: PRJNA662418
-         Costa2022 - Single-cell transcriptomics reveals shared immunosuppressive landscapes of mouse and human neuroblastoma: GSE180101
- **Tools**: Seurat, Harmony, scVI, custom R scripts.
- **Applications**: Understanding immune modulation and tumor heterogeneity in Neuroblastoma Mouse Models.

## 📁 Repository Structure

```
NBMap/
├── data/ # Input raw/processed datasets

        All datasets are available via Zenodo:
        - 🔗 [Raw Data] (https://zenodo.org/records/15435388/files/All_Studies.RData)
        - 🔗 [Pre-Processed Data] (https://zenodo.org/records/15434777/files/PreProcessed_Seu.rds)
        - 🔗 [scVI Coordinates and Metadata] (https://zenodo.org/records/15470814/files/scVI_Coordinates_Metadata.RData)
        - 🔗 [h5 Global Expression Matrix for ScanPy] (https://zenodo.org/records/15436589/files/Expression_matrix.h5)
        - 🔗 [h5 Global Expression Metadata for ScanPy] (https://zenodo.org/records/15436589/files/Expression_metadata.csv)
        - 🔗 [h5 Immune Expression Matrix for ScanPy] (https://zenodo.org/records/15436815/files/Immune_Expression_matrix.h5)
        - 🔗 [h5 Immune Expression Metadata for ScanPy] (https://zenodo.org/records/15436815/files/Immune_Expression_metadata.csv)
        - 🔗 [Shiny_Global_Object] (https://zenodo.org/records/15434175/files/Global_Atlas_Shiny_Object.rds)
        - 🔗 [Shiny_Immune_Object] (https://zenodo.org/records/15434175/files/Immune_Zoom_Shiny_Object.rds)

├── scripts/ # R scripts for analysis
├── figures/ # Plots and visualizations
├── results/ # DEG tables, metadata, etc.
├── shiny_app/ # Code for interactive Shiny app
├── .gitignore # File to exclude unnecessary files from version control
└── README.md # Project overview and usage
```

## 💻 Usage

1. **Install required R packages** (if not already installed):

```r
install.packages(c("Seurat", "ggplot2", "dplyr", "patchwork"))
# If using Harmony:
# remotes::install_github("immunogenomics/harmony")
# If using scVI (Python-based), see instructions in a separate notebook or conda environment
```

2. **Run the preprocessing and integration scripts:**

```r
source("scripts/1_Data_Loading_and_PreProcessing.Rmd")
source("scripts/2_Harmony_Integration_Script.Rmd")
source("scripts/5_scVI_Global_Integration.ipynb")
```

3. **Generate visualizations and perform downstream analysis:**

```r
source("scripts/6_scVI_UMAP_QC_Script.R")
source("scripts/7_Cell_Type_Annotation.R")
```

4. **Explore results interactively using the Shiny app:**

```r
shiny::runApp("Global_Atlas/Scripts/App.R")
shiny::runApp("Immune_Zoom/Scripts/App.R")
```
