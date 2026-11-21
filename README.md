# Predicting Familial vs. Sporadic NF1 Cases

**NJIT DS675 Machine Learning project** | Python, scikit-learn, Linear Regression, Linear SVM

This project tests whether clinical symptom and age variables can help distinguish **familial** from **sporadic** neurofibromatosis type 1 (NF1) cases. It evaluates **Linear Regression** and **Linear Support Vector Machine** with stratified cross-validation and balanced accuracy.

**Research and educational use only. The models are not suitable for medical diagnosis.**

## Research question

Can simple linear models classify familial versus sporadic NF1 using clinical features? Does removing three age-related variables improve performance?

## Dataset and provenance

This repository includes **the exact `dataset-uci.xlsx` spreadsheet used in the original experiment**, at [`data/dataset-uci.xlsx`](data/dataset-uci.xlsx). It was obtained from the [UCI Machine Learning Repository, dataset 1162](https://archive.ics.uci.edu/dataset/1162/neurofibromatosis+type+1+clinical+symptoms+of+familial+and+sporadic+cases) and is redistributed with attribution under **CC BY 4.0**.

- 296 records (161 sporadic and 135 familial)
- 18 predictors and the `Case Type` target (0 = sporadic, 1 = familial)
- 3 age features and 15 other clinical features
- Original spreadsheet SHA256: `36408ef8d81f56bcc204966ff8110ff4bea28b1e3ae41d8bfe92877228716005`

**Why UCI says 331:** The UCI webpage advertises 331 instances, but this downloaded Excel workbook contains 296 rows, and the original Colab analysis used these 296. The reason for the catalog discrepancy is unknown. The repository preserves the exact input spreadsheet so the experiment can be reproduced without guessing what happened to the other 35 records. See [data documentation](data/README.md).

## Method

1. Load the source Excel file and separate predictors (`X`) from labels (`y`).
2. Fit median imputation and standard scaling within each training fold.
3. Evaluate `LinearRegression()`, using a 0.5 threshold to obtain class predictions.
4. Evaluate `LinearSVC()` with `C` = 100, 10, 1, 0.1 and 0.01.
5. Use stratified five-fold cross-validation with `shuffle=True` and `random_state=42`.
6. Report mean balanced accuracy. Repeat with 15 predictors after excluding the three age variables.

The workflow was written and evaluated in Google Colab, then adapted to run locally without Drive mounting or ZIP extraction.

## Experimental results

| Model | C | With ages | Without ages |
|---|---:|---:|---:|
| Linear Regression | N/A | 51.82% | 52.95% |
| Linear SVM | 100 | 51.82% | 52.95% |
| Linear SVM | 10 | 51.82% | 52.95% |
| Linear SVM | 1 | 51.82% | 52.95% |
| Linear SVM | 0.1 | 51.82% | 52.95% |
| Linear SVM | 0.01 | 50.41% | **53.56%** |

The highest mean balanced accuracy observed was **53.56%**, achieved by Linear SVM with `C=0.01` after excluding the age variables.

![Comparison of mean balanced accuracy with and without age variables](figures/age_feature_comparison.svg)

**Interpretation:** Model performance remained close to the 50% chance-level benchmark for this binary balanced-accuracy metric. Age removal produced a small improvement, but this does not prove that age is medically irrelevant. Additional experiments would be needed to identify the precise causes of the weak performance.

## Reproduce the experiment

The complete notebook **was rerun successfully** on the original Excel spreadsheet on November 21, 2026. Its reported balanced accuracy values matched the original Colab experiment.

**Tested environment:** Python 3.13.5 with the Python package versions pinned in [requirements.txt](requirements.txt).

1. Clone this repository, or download its ZIP using GitHub's **Code → Download ZIP** menu.
2. Open a terminal inside the downloaded repository folder.
3. Run `pip install -r requirements.txt`.
4. Run `jupyter lab`. Open [`notebooks/nf1_analysis.ipynb`](notebooks/nf1_analysis.ipynb).
5. Select **Restart Kernel and Run All Cells**. The notebook reads the included file from `data/dataset-uci.xlsx`.
6. The final cell validates the source file's SHA256 and three benchmark balanced accuracy scores. A successful run prints **"Reproduction check passed"**.

Generated charts are saved under `figures/`.

## Files

- [`notebooks/nf1_analysis.ipynb`](notebooks/nf1_analysis.ipynb): adapted original experiment, all core code, and reproducibility checks
- [`data/dataset-uci.xlsx`](data/dataset-uci.xlsx): exact source workbook used for the results
- [`data/README.md`](data/README.md): provenance and CC BY 4.0 attribution
- [`figures/age_feature_comparison.svg`](figures/age_feature_comparison.svg): summary visualization
- [`requirements.txt`](requirements.txt): tested Python dependencies
- [`.gitignore`](.gitignore): temporary file exclusions

## Limitations and responsible use

- Small clinical dataset with possible substantial class overlap
- Only linear classifiers / linear prediction baselines were evaluated
- The analysis used the same cross-validation results to compare parameter and feature choices; it did **not** reserve a final untouched test set
- Outcomes are not suitable for clinical decisions or diagnosis
- The discrepancy between the UCI website's instance count and the actual spreadsheet is documented, not explained

## Source and credit

Dataset: Sharafi, P., Arslan, H., Ersoy, S., Varan, A., and Ayter, Ş. (2025). *Neurofibromatosis Type 1; Clinical Symptoms of Familial and Sporadic Cases*. UCI Machine Learning Repository. [UCI dataset page](https://archive.ics.uci.edu/dataset/1162/neurofibromatosis+type+1+clinical+symptoms+of+familial+and+sporadic+cases). [Associated research DOI](https://doi.org/10.5505/TurkHijyen.2025.06337).

Dataset license: [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/).
