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

The workflow includes:
- Loading datasets into AnnData
- Quality inspection and filtering
- Normalization and log transformation
- PCA and UMAP dimensionality reduction
- Leiden clustering
  
Spatial visualization and interpretation
  
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

Used for:
- AnnData exploration
- UMAP visualization
- Metadata analysis
- Data subsetting

```python
adata = sc.datasets.pbmc3k_processed()
```
PBMC3K UMAP Visualization
<img width="739" height="431" alt="1" src="https://github.com/user-attachments/assets/953389ee-c02f-487c-9036-8363808b25ce" />

Interpretation
- Clear separation of immune cell populations
- Demonstrates successful dimensionality reduction
- Shows biologically meaningful clustering

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

Spatial Distribution of Total Counts

<img width="352" height="431" alt="2" src="https://github.com/user-attachments/assets/88fda3eb-4a30-45c2-82ba-7ff30db355b9" />

Interpretation
- Each spot represents a Visium capture location
- Brighter regions indicate higher transcript counts
- Spatial expression patterns align with tissue structure

---

UMAP Plot with Leiden Clusters
<img width="685" height="431" alt="3" src="https://github.com/user-attachments/assets/2fd0844d-52ba-45c7-b93a-5db804df6294" />

Interpretation
- Cells grouped into transcriptionally distinct clusters
- Demonstrates cellular heterogeneity
- Reveals functional regions within tissue

---

Spatial Plot with Leiden Clusters
<img width="431" height="431" alt="4" src="https://github.com/user-attachments/assets/68f79968-9414-4f6d-8498-fa40ea94b858" />
Interpretation
Spatial arrangement of clusters
Reveals tissue organization
Identifies spatially localized populations

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

H&E Spatial Total Counts
<img width="399" height="431" alt="5" src="https://github.com/user-attachments/assets/6809db3e-141c-43eb-ac08-aac72d2ab146" />

Interpretation
- Expression overlaid on histological image
- Highlights tissue morphology
- Connects molecular and structural information

---
UMAP Plot – H&E Leiden Clusters
<img width="478" height="431" alt="6" src="https://github.com/user-attachments/assets/da58eecf-5889-402c-b6f6-878553456c6f" />

Interpretation
- Distinct cell populations identified
- Demonstrates transcriptional heterogeneity
- Highlights functional tissue regions

---

Spatial Plot – H&E Leiden Clusters
<img width="694" height="431" alt="7" src="https://github.com/user-attachments/assets/9785a368-b253-4556-9fa3-380daaf16922" />

Interpretation
- Clusters align with histological structures
- Reveals biological organization within tissue

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



```python
sc.pl.umap(adata, color="leiden")

sc.pl.spatial(adata, color="leiden")

```
Xenium UMAP Clustering
<img width="601" height="431" alt="8" src="https://github.com/user-attachments/assets/aa9664af-60c8-42fe-9f42-fc31e9395c78" />

Gene Expression on UMAP
<img width="539" height="431" alt="9" src="https://github.com/user-attachments/assets/e8002e30-79d5-4440-88c6-9e02a9d252e5" />

```

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
Xenium UMAP Clustering
<img width="601" height="431" alt="8" src="https://github.com/user-attachments/assets/aa9664af-60c8-42fe-9f42-fc31e9395c78" />


Gene Expression on UMAP
<img width="539" height="431" alt="9" src="https://github.com/user-attachments/assets/e8002e30-79d5-4440-88c6-9e02a9d252e5" />

---


# Technology Comparison

<img width="640" height="328" alt="technology_comparison" src="https://github.com/user-attachments/assets/760615ce-da6d-4105-a90c-ad552507778d" />

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
