````markdown
# BIFS 618 — Project 2a: Single Cell RNA-Seq Analysis

## Overview

This project reimplements the legacy Scanpy workflow on the 10x Genomics PBMC 3k dataset as a single, reproducible master pipeline script. The objective is to reproduce a complete single-cell RNA-seq (scRNA-seq) analysis workflow, from raw count data through quality control, normalization, dimensionality reduction, clustering, and cell type annotation, using a self-contained and reproducible pipeline.

The analysis follows Scanpy best practices while enforcing deterministic behavior through a fixed random seed.

---

## Dataset

- **10x Genomics PBMC 3k dataset**
- Peripheral Blood Mononuclear Cells (PBMCs)
- Approximately 3,000 cells profiled using 10x Genomics Chromium technology

---

## Project Structure

```text
BIFS-618---Project-2a-Single-Cell-RNA-Seq/
│
├── README.md
│
└── Pipeline/
    ├── README.md
    ├── scanpy_master_logs_seed_v3.py
    └── run_scanpy_pipeline.sh
````

***

## Pipeline Summary

| Step                     | Method                            | Input → Output                        |
| ------------------------ | --------------------------------- | ------------------------------------- |
| Quality Control          | Scanpy QC metrics                 | Raw matrix → filtered matrix          |
| Normalization            | Total count normalization + log1p | Filtered → normalized                 |
| HVG Selection            | Seurat-flavor dispersion          | 32,738 genes → 2,000 genes            |
| Dimensionality Reduction | PCA                               | 2,000 genes → 50 principal components |
| Neighbor Graph           | k-nearest neighbors               | 50 PCs → connectivity graph           |
| UMAP                     | Fuzzy set optimization            | Graph → 2D embedding                  |
| Clustering               | Leiden algorithm                  | Graph → cluster labels                |
| Cell Type Annotation     | Marker gene scoring               | Clusters → cell type labels           |

***

## Reproducibility

All stochastic steps in the pipeline are controlled using a shared seed value:

```python
SEED = 594
```

This seed is applied to:

*   NumPy
*   Python `random` module
*   Scrublet
*   PCA
*   Neighbor graph construction
*   UMAP
*   Leiden clustering

Each execution produces a `run_log.txt` file documenting execution metadata, package versions, seed value, and matrix dimensions at every stage of the pipeline, ensuring reproducibility and auditability.

***

## Group

**Group 2 — BIFS 618**
