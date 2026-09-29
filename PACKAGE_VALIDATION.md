# Package validation

Final release-package validation performed after reproducibility fixes.

- Frozen-data reproducibility checks: **166/166 passed**.
- Corrected final figure notebook executed end-to-end, including a self-contained run from the GitHub `frozen_results/` bundle that generated all 21 expected figure files.
- All cleaned GitHub notebooks: zero stored outputs and zero coarse Python syntax errors.
- All packaged CSV result tables parse successfully.
- Final manuscript figure exports are present in PDF, SVG, and PNG.
- Manuscript DOCX integrity verified; the DOCX was also rendered and visually inspected during the packaging audit.

## Release caveat

This validates the frozen project analysis and manuscript package. It is not a literal re-download/reclustering of every public raw dataset from the internet; that separate release-engineering exercise requires the external repositories and a Colab/R/Bioconductor/Scanpy environment.

## Validation details
- Reproducibility checks: 166/166 passed
- Table Early184_GeneLevel_Correlations.csv: (21, 6)
- Table Early184_MatchedDirection.csv: (5, 6)
- Table Early184_MatchedNull.csv: (5, 6)
- Table GSE160306_HumanBulk_All40.csv: (40, 5)
- Table GSE290024_Organoid_SignatureTests.csv: (4, 4)
- Table HumanMuller_Bridge_Correlations.csv: (6, 6)
- Table Lin2025_Rat_AllLocked.csv: (12, 11)
- Table MASTER_RESULTS_SUMMARY.csv: (20, 9)
- Notebook 01_02_04_Core_Discovery_Mouse_Human_Muller_CLEAN.ipynb: outputs=0, coarse Python syntax errors=0
- Notebook 03_GSE160306_Human_Bulk_Validation_CLEAN.ipynb: outputs=0, coarse Python syntax errors=0
- Notebook 05_GSE290024_Human_Organoid_Validation_CLEAN.ipynb: outputs=0, coarse Python syntax errors=0
- Notebook 06_CrossSpecies_Trajectory_Integration_CLEAN.ipynb: outputs=0, coarse Python syntax errors=0
- Notebook 07_Lin2025_Rat_Muller_Validation_CLEAN.ipynb: outputs=0, coarse Python syntax errors=0
- Notebook 08_Final_Figures_and_Paper_Assembly.ipynb: outputs=0, coarse Python syntax errors=0
- Final figure exports: 21/21 present
- GitHub frozen-results bundle: 13 files

**No package-integrity issues detected.**
