# Reproducibility Package

This repository contains the reproducibility materials for the manuscript. The main file is a Google Colab notebook that reproduces the preprocessing, feature construction, model training, evaluation, and figure/table generation steps used in the paper.

## Repository contents

```text
.
├── notebook.ipynb
├── requirements.txt
├── data_sample/
│   ├── sample_file1.csv
│   └── sample_file2.csv
└── outputs/
    ├── tables/
    └── figures/
```

## Input files

The notebook expects two CSV input files in the working directory:

- `sample_file1.csv` — meteorological/weather input data. In the original experiment this corresponds to the file formerly named `MotiPanel.csv`.
- `sample_file2.csv` — photovoltaic generation data. In the original experiment this corresponds to the file formerly named `Generated.csv`.

The sample files document the expected input structure. The full CSV files are not publicly released in this repository because they are part of an ongoing multi-study research program and may be subject to data-use or redistribution constraints. The full input files can be made available confidentially to the editor or reviewers upon reasonable request, where permitted.

## How to run the notebook in Google Colab

1. Open `notebook.ipynb` in Google Colab.
2. Upload `sample_file1.csv` and `sample_file2.csv` to the Colab working directory, or replace them with the full input files using the same filenames.
3. Run all notebook cells sequentially from top to bottom.
4. The notebook generates the intermediate datasets, trains the models, evaluates the reported metrics, and creates the output tables and figures used in the manuscript.

## Expected generated files

During execution, the notebook creates intermediate and output files such as:

- `Dataset_PINN_Input.csv`
- `Dataset_PINN_Input_filtered.csv`
- model-comparison result tables
- publication figures saved by the plotting cells

Exact output filenames may depend on the final plotting/export cells retained in the notebook.

## Reproducibility notes

- Fixed random seeds are set where applicable.
- The notebook is designed to be executed sequentially.
- The code uses one-hot encoding for categorical weather-condition variables where applicable.
- The input file names used in this repository are anonymized/generalized as `sample_file1.csv` and `sample_file2.csv`.
- Results may show small numerical differences across CPU/GPU environments and package versions, especially for neural-network training.

## Python environment

The notebook was prepared for Google Colab. To reproduce the environment locally, install the packages listed in `requirements.txt`:

```bash
pip install -r requirements.txt
```

## Data availability statement

The repository includes the Colab notebook, execution instructions, package requirements, generated-output structure, and sample CSV files documenting the expected input schema. The full CSV files are not publicly released at this stage because they are part of an ongoing multi-study research program and may also be subject to data-use or redistribution constraints. They can be made available confidentially to the editor or reviewers upon reasonable request, where permitted.
