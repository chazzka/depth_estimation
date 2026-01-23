# Statistical Parameter–Based Normalization for ROC Analysis

This repository contains experimental results and supporting data for the evaluation of different
statistical normalization strategies in anomaly/outlier detection, with a focus on ROC curve analysis
and AUC comparison across multiple benchmark datasets.

The repository is structured to clearly separate raw ROC outputs, per-feature parameter statistics,
and derived statistical summaries used in the analysis.

---

## Repository Structure

```
.
├── params_per_feature/
├── roc/
├── stat_parameters/
```

### `params_per_feature/`
Contains per-feature statistical parameters computed for each dataset(ALOI,...),method (adjusted,mad,zscore) and feature.

- dataset - name of ADBench dataset
- param_opt - optimal chosen parameter (if 0, then the dataset was not continuos, hence fallback was used)
- final_auc - final maximized AUC value (should be the same for all features, since we optimize one global AUC for the whole dataset)
- grid - grid search parameters or information that dataset was discrete; hence we used minmax

---

### `roc/`
Contains ROC-related outputs for all evaluated datasets and normalization methods.

Expected substructure:
```
roc/
├── adjusted/
├── mad/
└── zscore/
```

Each subdirectory corresponds to a different normalization strategy:
- **adjusted** – adjusted statistical normalization
- **mad** – median absolute deviation–based normalization
- **zscore** – standard z-score normalization

Each CSV file stores ROC curve data:
- **x-axis**: False Positive Rate (FPR)
- **y-axis**: True Positive Rate (TPR)

Filename convention:
```
<ID>_<dataset>_t<param>_<seed>_auc<XpYYYYYY>.csv
```

Example:
```
6_cardio_t100_0_auc0p753448.csv
```

Where:
- `auc0p753448` corresponds to an AUC of `0.753448`.

These files are intended for:
- direct plotting of ROC curves,
- cross-method AUC comparison,
- statistical aggregation across datasets.

---

### `stat_parameters/`
Contains precomputed statistics for training datasets with significance tests for medcouple averaged calculation.

This directory includes:
- METHOD_parameters - contains statistical properties of each dataset used in the context of the specified METHOD
- significance - significance tests outputs for medcouple averaged calculation


---

## Citation

If you use this repository or its results in academic work, please cite it using the provided
`CITATION.cff` file.

GitHub will automatically generate citation formats (BibTeX, APA, etc.) based on this file.

---

## License

This project is released under the license specified in the `LICENSE` file.
Please review it before reusing or redistributing any part of the repository.

---

## Notes

- This repository primarily contains **experimental data**, not a runnable end-to-end pipeline.
- Scripts used for analysis and plotting are assumed to be maintained separately or generated ad hoc.
- The structure is designed to be machine-readable and suitable for large-scale comparative studies.
---

## Contact

For questions, clarifications, or collaboration inquiries, please open an issue in the repository.
