# Data Source

## Dataset Name

**PBMC 3k (Peripheral Blood Mononuclear Cells)**

## Original Data Source

**10x Genomics — 3k PBMCs from a Healthy Donor**  
https://www.10xgenomics.com/datasets/3-k-pbm-cs-from-a-healthy-donor-1-standard-1-1-0

## Access Method Used in This Project

The dataset is accessed programmatically using the Scanpy built-in dataset loader:

```python
sc.datasets.pbmc3k()
```
**Scanpy Documentation**
https://scanpy.readthedocs.io/en/stable/generated/scanpy.datasets.pbmc3k.html

## Notes

The dataset is downloaded automatically by Scanpy at runtime.
No raw data files are stored in this repository.
