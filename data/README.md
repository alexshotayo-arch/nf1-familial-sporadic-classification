# NF1 dataset snapshot

This folder contains `dataset-uci.xlsx`, the **exact source spreadsheet used by the original project**.

- **Rows:** 296 patient records
- **Columns:** 20 total, including a row identifier and `Case Type`
- **Modeling features:** 18
- **Labels:** 161 sporadic (0), 135 familial (1)
- **SHA256:** `36408ef8d81f56bcc204966ff8110ff4bea28b1e3ae41d8bfe92877228716005`
- **Source:** [UCI Machine Learning Repository, Dataset 1162](https://archive.ics.uci.edu/dataset/1162/neurofibromatosis+type+1+clinical+symptoms+of+familial+and+sporadic+cases)
- **License for dataset:** [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0). Attribution to the original dataset creators is required.

This is the original unmodified Excel workbook as saved for the project, including its metadata sheets.

**Important metadata discrepancy:** UCI currently displays **331 instances** on the dataset webpage, but this `dataset-uci.xlsx` workbook contains **296 data rows**. The notebook and results both used these 296 rows. We have not established why UCI's metadata count differs and do not claim 35 records were removed during analysis.

**Attribution:** Sharafi, P., Arslan, H., Ersoy, S., Varan, A., & Ayter, Ş. (2025). *Neurofibromatosis Type 1; Clinical Symptoms of Familial and Sporadic Cases* [Dataset]. UCI Machine Learning Repository. [Research article DOI](https://doi.org/10.5505/TurkHijyen.2025.06337).

No patient names, contact information, or individual identifiers other than numeric row indices appear in the modeled table.
