# 10x Genomics Spatial Methods


## Overview

This repository contains a Google Colab notebook demonstrating spatial transcriptomics analysis using Scanpy and Squidpy.

The project covers:
- Basic Scanpy workflows
- Visium fluorescence dataset analysis
- Visium H&E dataset analysis
- Xenium tiny dataset workflow
- PCA and UMAP dimensionality reduction
- Leiden clustering
- Spatial visualization and gene expression analysis

---

## Workflow Pipeline
  
<img width="990" height="251" alt="workflow_pipeline" src="https://github.com/user-attachments/assets/a6d09cef-ce79-470b-abcd-9b319c1e25e1" />

---

# Technologies Used

| Tool | Purpose |
|---|---|
| Scanpy | Single-cell RNA-seq analysis |
| Squidpy | Spatial transcriptomics analysis |
| AnnData | Genomics data structure |
| Matplotlib | Visualization |
| NumPy | Numerical computation |
| Leidenalg | Clustering |
| igraph | Graph analysis |

---

# Workflow

## 1. Install Required Libraries

```python
!pip install scanpy squidpy anndata matplotlib seaborn pooch
!pip install leidenalg igraph
```

---

## 2. Load and Explore Datasets

### PBMC3K Dataset

```python
adata = sc.datasets.pbmc3k_processed()
```

Used for:
- AnnData exploration
- UMAP visualization
- Metadata analysis
- Data subsetting

---

### Visium Fluorescence Dataset

```python
adata = sq.datasets.visium_fluo_adata()
```

Used for:
- Spatial plotting
- PCA
- UMAP
- Clustering
- Spatial visualization

---

### Visium H&E Dataset

```python
adata = sq.datasets.visium_hne_adata()
```

Used for:
- Tissue-based spatial analysis
- Cluster visualization
- Spatial transcriptomics workflows

---

### Xenium Human Ovary Tiny Dataset

```python
adata = sc.read_10x_h5(
    "/content/xenium_data/cell_feature_matrix.h5"
)
```

Used for:
- High-resolution spatial analysis
- PCA and UMAP
- Leiden clustering
- Gene expression visualization

---

# Preprocessing Pipeline

```python
sc.pp.normalize_total(adata)
sc.pp.log1p(adata)
sc.pp.pca(adata)
sc.pp.neighbors(adata)
sc.tl.umap(adata)
sc.tl.leiden(adata)
```

---

# Generated Visualizations

The notebook generates:
- UMAP embeddings
- Spatial tissue plots
- Leiden clustering maps
- Gene expression visualizations

Example:

```python
sc.pl.umap(adata, color="leiden")
sc.pl.spatial(adata, color="leiden")
```

---

# Technology Comparison

<img width="640" height="328" alt="technology_comparison" src="https://github.com/user-attachments/assets/760615ce-da6d-4105-a90c-ad552507778d" />

---

# Xenium Dataset Setup

## Upload Dataset to Colab

Upload:

```text
Xenium_V1_Human_Ovary_tiny_outs.zip
```

---

## Extract Dataset

```python
import zipfile

with zipfile.ZipFile(
    "/content/Xenium_V1_Human_Ovary_tiny_outs.zip",
    "r"
) as zip_ref:
    zip_ref.extractall("/content/xenium_data")
```

---

# Repository Structure

```text
10x-genomics-spatial-methods/
│
├── README.md
├── Fatima(Genomics_Spatial_Methods)(2).ipynb
├── requirements.txt
│
├── github_readme_assets/
│   ├── workflow_pipeline.png
│   └── technology_comparison.png
│
├── data/
│
└── figures/
```

---

# Requirements

Create a `requirements.txt` file containing:

```text
scanpy
squidpy
anndata
matplotlib
seaborn
pooch
leidenalg
igraph
numpy
```

---

# Running the Notebook

## Google Colab

1. Open Google Colab
2. Upload the notebook
3. Run installation cells
4. Upload Xenium dataset ZIP
5. Execute notebook cells sequentially

---

# Notes

- The notebook was successfully executed in Google Colab.
- Spatial transcriptomics analysis was performed using Scanpy and Squidpy.
- Xenium analysis was demonstrated using a lightweight Xenium Human Ovary tiny dataset.
- The workflow includes preprocessing, clustering, dimensionality reduction, and visualization.

---
# Notebook

```text
https://colab.research.google.com/drive/1W7euGLRboVdPENGzFcxCnLvwxAAbVVh-?usp=sharing
```


# Conclusion

This notebook demonstrates a complete introductory workflow for **10x Genomics spatial transcriptomics analysis** using modern Python bioinformatics tools. The repository combines traditional single-cell analysis with spatial genomics workflows and introduces high-resolution Xenium-based analysis in a Colab-compatible environment.

---

# References

- Scanpy Documentation  
  https://scanpy.readthedocs.io/

- Squidpy Documentation  
  https://squidpy.readthedocs.io/

- 10x Genomics Xenium  
  https://www.10xgenomics.com/platforms/xenium

- Google Colab  
  https://colab.research.google.com/
