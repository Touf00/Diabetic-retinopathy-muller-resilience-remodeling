# Reproducibility audit

A fresh validation pass was performed after packaging using the frozen project files retrieved from the project Google Drive.

## Scope

This was an **independent frozen-data reproducibility audit**, not merely a syntax check. The audit:

- recomputed locked-signature sizes and discovery medians;
- recomputed mouse longitudinal signature summaries;
- recomputed human Müller donor means and exact directional permutation tests from donor-level scores;
- verified all 40 human bulk-retina locked-signature tests and the absence of FDR-significant contrasts;
- independently recounted organoid transcriptome-wide DE genes (2,275 total at FDR < 0.05; 919 up, 1,356 down);
- recomputed all 21 Early184 pairwise Spearman correlations from the cross-system master gene-effect matrix and independently reproduced their BH FDR values;
- rebuilt donor-level human Müller gene effects from the frozen donor pseudobulk count matrix and reproduced the six mouse-human bridge correlations;
- reparsed Lin et al. Supplementary Table S2 and reproduced the Early184 reported-gene trajectory;
- executed the final figure-assembly notebook end-to-end in a clean local Jupyter runtime against the frozen result files;
- bundled the compact `frozen_results/` tables required by the figure notebook and independently executed the public GitHub version without Google Drive, generating all 21 expected figure files.

## Result

**166 / 166 quantitative and file-generation checks passed.** No headline statistical result changed.

The complete machine-readable check table is `REPRODUCIBILITY_CHECKS.csv`.

## Issues found and fixed during the audit

1. `07_Lin2025_Rat_Muller_Validation_CLEAN.ipynb` had the `gprofiler` import and locked-signature load after the first cell that used them. The cells were reordered so the notebook is runnable sequentially in Colab.
2. `08_Final_Figures_and_Paper_Assembly.ipynb` attempted to read a non-existent `trajectory_class` column from the discovery trajectory file. The panel now derives the three locked discovery-class counts directly from the frozen signature JSON. The corrected figure notebook was executed successfully end-to-end.
3. The earlier rat table labeled all 184 Early184 queries as mapped even when some returned rat identifiers were missing or not symbol-form identifiers usable against Supplementary Table S2. The manuscript no longer claims that all 184 mapped, and the packaged rat table reports the usable symbol-compatible mapping count (173) while leaving the reported-gene results unchanged.
4. Two packaged CSV summaries (`Lin2025_Rat_AllLocked.csv` and `Early184_MatchedDirection.csv`) had been malformed during packaging. They were replaced with valid source-derived CSV files.

## What this audit establishes

The frozen analysis outputs, manuscript numbers, integration statistics, and final figure-generation workflow are internally reproducible from the saved project data. The user does **not** need to rerun the notebooks manually for this paper package.

A literal from-public-raw-data re-download/reclustering run is a separate release-engineering exercise because it depends on Colab/R/Bioconductor/Scanpy and external repositories. It is not required to use the validated frozen results in the manuscript. The cleaned notebooks retain the raw-data analysis logic for public release.
