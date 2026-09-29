# Environment notes

The workflow was developed in Google Colab and uses both Python and R/Bioconductor.

## Python

See `requirements.txt`. Core packages include pandas, NumPy, SciPy, Scanpy/AnnData, matplotlib, scikit-learn, statsmodels, GEOparse, GSEApy, gprofiler-official, mygene, and rpy2.

## R / Bioconductor

Install as needed:

- edgeR
- limma
- DESeq2

The organoid analysis uses edgeR/limma as the final inferential route; an attempted PyDESeq2 path in the exploratory notebook failed because of a pandas/anndata compatibility issue and is not part of the finalized workflow.

## Reproducibility status

A fresh frozen-data validation pass was performed against the project Google Drive outputs: **166/166 quantitative and file-generation checks passed**, and the corrected final figure-assembly notebook was executed end-to-end in a clean local Jupyter runtime. See `REPRODUCIBILITY_AUDIT.md` and `REPRODUCIBILITY_CHECKS.csv`.

The cleaned analysis notebooks retain the complete finalized workflow and have zero stored outputs/known failed cells. A literal from-public-raw-data re-download/reclustering run is optional release engineering and requires the external repositories plus a Colab/R/Bioconductor/Scanpy environment; it is distinct from the validated frozen-analysis package.
