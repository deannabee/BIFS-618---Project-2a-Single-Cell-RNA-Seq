BIFS 618 — Project 2a: Single Cell RNA-Seq Analysis
Overview
This project reimplements the Scanpy legacy workflow on the 3k PBMC dataset as a single master pipeline script. The goal is to reproduce a standard scRNA-seq analysis, from raw count data through quality control, normalization, dimensionality reduction, clustering, and cell type annotation, in a reproducible and self-contained pipeline.
The dataset used is the 10x Genomics PBMC 3k dataset
Project Structure
```
BIFS-618---Project-2a-Single-Cell-RNA-Seq/
│
├── README.md
│
└── Pipeline/
    ├── README.md
    ├── scanpy_master_logs_seed_v3.py
    └── run_scanpy_pipeline.sh
```
Pipeline Summary
Step	Method	Input → Output
Quality Control	Scanpy QC metrics	Raw matrix → filtered matrix
Normalization	Total count normalization + log1p	Filtered → normalized
HVG Selection	Seurat-flavor dispersion	32,738 genes → 2,000 genes
Dimensionality Reduction	PCA	2,000 genes → 50 PCs
Neighbor Graph	k-nearest neighbors	50 PCs → connectivity graph
UMAP	Fuzzy set optimization	Graph → 2D embedding
Clustering	Leiden algorithm	Graph → cluster labels
Cell Type Annotation	Marker gene scoring	Clusters → cell type labels
Reproducibility
All stochastic steps are seeded with a shared class seed value (`SEED = 594`). The seed is applied to NumPy, Python's random module, Scrublet, PCA, neighbor graph construction, UMAP, and Leiden clustering. A `run_log.txt` is written to the output directory on each run documenting the environment, package versions, seed value, and matrix dimensions at each stage.
Group
Group 2 — BIFS 618
