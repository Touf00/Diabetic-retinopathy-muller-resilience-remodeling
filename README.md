# Early Müller resilience and state-dependent remodeling in diabetic retinopathy

This repository contains the finalized computational analysis for a cross-system study testing whether an experimentally defined **early Müller resilience-associated transcriptional program** persists as a conserved state during diabetic retinal progression.

## Central question

A 5-day diabetic mouse retina dataset (GSE328966) was used to define and lock an early Müller response before validation. The locked program was then stress-tested across independent mouse progression data, human Müller cells, human bulk retina, human retinal organoids, and an independent longitudinal rat Müller dataset.

The analysis does **not** redefine the discovery signature after seeing validation results. Negative and partial validations are retained.

## Main result

The early Müller program is transient rather than stably conserved. Chronic whole-retina remodeling becomes internally coherent across time, whereas chronic Müller-cell gene ordering diverges from the surrounding retinal response. Human Müller cells and retinal organoids do not reproduce the original early mouse gene ordering as a coherent state. The data therefore support **state-dependent remodeling** rather than persistence of a universal protective/reactive Müller signature.

## Repository structure

- `notebooks/01_02_04_Core_Discovery_Mouse_Human_Muller_CLEAN.ipynb` — GSE328966 discovery, GSE313176 mouse progression, and human Müller atlas analysis.
- `notebooks/03_GSE160306_Human_Bulk_Validation_CLEAN.ipynb` — stage- and region-aware human bulk-retina validation.
- `notebooks/05_GSE290024_Human_Organoid_Validation_CLEAN.ipynb` — replicated human retinal organoid validation.
- `notebooks/06_CrossSpecies_Trajectory_Integration_CLEAN.ipynb` — matched-null and gene-level cross-system integration.
- `notebooks/07_Lin2025_Rat_Muller_Validation_CLEAN.ipynb` — threshold-aware independent rat Müller validation.
- `notebooks/08_Final_Figures_and_Paper_Assembly.ipynb` — reads frozen result tables only and generates manuscript figures.
- `frozen_results/` — compact source tables required to reproduce the final summary figures without the full Google Drive project.
- `figures/` — validated PDF/SVG/PNG figure exports.

## Locked discovery programs

- `Early184`: 184 early-up transient mouse Müller genes.
- `IFN6`: Ifit3, Irf9, Samhd1, Stat1, Stat2, Usp18.
- `Retinoid5`: Bco2, Gpc1, Gpc2, Gpc3, Rimbp2.
- `ECM13`: Adamts5, Capn5, Col15a1, Col27a1, Col9a2, Gpc1, Gpc2, Gpc3, Itgav, Itgb8, Naglu, P3h2, Tll1.

These definitions were frozen before independent validation.

## Data sources

| Dataset | Species/system | Role |
|---|---|---|
| GSE328966 | Mouse retinal scRNA-seq, 5D/15D diabetes | Discovery |
| GSE313176 | Mouse whole-retina bulk RNA-seq at 1/3/6 months + 3-month scRNA-seq | Longitudinal validation |
| Human 2026 retinal scRNA atlas | 20 eyes / 13 donors, NON/DM/DR | Human Müller translation |
| GSE160306 | Human post-mortem bulk retina, macula/periphery across DR stages | Human stage/region validation |
| GSE290024 | Human retinal organoids, 25 mM vs 17-17.5 mM glucose | Controlled human perturbation |
| Lin et al. 2025 Supplementary Table S2 | Rat Müller cells, 1/2/3 months | Independent external validation |

## Statistical interpretation

Important design constraints are carried through the analysis:

- GSE328966 discovery libraries are pooled at the condition/timepoint level. Depth-standardization and repeated downsampling address technical imbalance but **do not create biological replication**. Discovery results are therefore hypothesis-generating/descriptive.
- GSE313176 whole-retina bulk has independent biological replicates and supports inferential testing; its 3-month scRNA arm has one Sham and one STZ library and is treated descriptively.
- Human Müller analyses use donor-level pseudobulk/score summaries; the DM group contains only three donors, so donor sensitivity is explicitly reported.
- GSE160306 is modeled with stage × retinal site and donor blocking. No locked signature contrast survives the prespecified 40-test FDR family.
- GSE290024 compares 25 mM with a 17-17.5 mM glucose baseline; it is not a physiological normoglycemia-versus-diabetes contrast.
- Lin et al. Supplementary Table S2 is censored at approximately |avg_log2FC| >= 0.25; absent genes are not treated as unchanged.
- Cross-platform effect sizes are not directly compared numerically. Integrated figures use within-system effects, direction, rank correlation, or matched-background tests as appropriate.

## Reproducibility

The GitHub notebooks are cleaned repository versions: execution outputs and known failed exploratory cells were removed. Large public-data downloads and intermediate objects are not committed. During the final packaging audit, the frozen project outputs were independently checked with 166/166 quantitative/file-generation checks passing, and the figure-assembly notebook was executed end-to-end after correcting two runtime-order/schema issues. See `REPRODUCIBILITY_AUDIT.md` and `REPRODUCIBILITY_CHECKS.csv`.

The full analysis notebooks can be run in order against the original project root:

`/content/drive/MyDrive/DR_Muller_AdaptiveReactive`

The final figure notebook is additionally self-contained for repository use: it first looks for `frozen_results/` and only falls back to Google Drive if that bundle is absent.

The notebooks use Python plus R/Bioconductor (`edgeR`, `limma`, `DESeq2` where indicated). See `requirements.txt` and `ENVIRONMENT_NOTES.md`.

## Citation / status

Manuscript in preparation. Add the final manuscript DOI/preprint citation here after release.

## License

No software/content license has been selected yet. Add one before public release if reuse permissions are intended.
