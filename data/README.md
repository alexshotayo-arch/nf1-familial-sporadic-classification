# Dataset instructions and source

The dataset is not included in this repository.

1. Visit the [UCI NF1 dataset page](https://archive.ics.uci.edu/dataset/1162/neurofibromatosis+type+1+clinical+symptoms+of+familial+and+sporadic+cases).
2. Download the archive and extract `dataset-uci.xlsx`.
3. Place the spreadsheet at `data/dataset-uci.xlsx` in the project.
4. Run the notebook and verify the shape and class counts.

**Important:** The saved Colab experiment used a working table with 296 rows (161 sporadic and 135 familial). The current UCI listing describes 331 instances. The reason for the difference is not confirmed, so results are not guaranteed to reproduce with a different version of the spreadsheet.

The dataset is attributed to Sharafi et al. (2025), UCI Machine Learning Repository. See the [UCI dataset listing](https://archive.ics.uci.edu/dataset/1162/neurofibromatosis+type+1+clinical+symptoms+of+familial+and+sporadic+cases) and [associated paper DOI](https://doi.org/10.5505/TurkHijyen.2025.06337). Check the UCI page for dataset licensing and attribution requirements.
