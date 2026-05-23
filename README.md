# Reproducibility Package

This repository contains the reproducibility materials for the manuscript. The main file is a Google Colab notebook that reproduces the preprocessing, feature construction, model training, evaluation, and figure/table generation steps used in the paper.

## Repository contents

```text
.
├── notebook.ipynb
├── requirements.txt
├── data_sample/
│   ├── sample_file1.csv
│   ├── sample_file2.csv
│   └── sample_file3.csv
└── outputs/
    ├── tables/
    └── figures/
```

## Input files

The notebook expects the following CSV input files in the working directory or in the `data_sample/` folder:

- `sample_file1.csv` — meteorological/weather input data. In the original experiment this corresponds to the file formerly named `MotiPanel.csv`.
- `sample_file2.csv` — photovoltaic generation data. In the original experiment this corresponds to the file formerly named `Generated.csv`.
- `sample_file3.csv` — Open-Meteo historical forecast data used for the additional NWP-source sensitivity experiment. The notebook also accepts `sample_test3.csv` as an alternative filename for this third file.

The sample files document the expected input structure. The full CSV files are not publicly released in this repository because they are part of an ongoing multi-study research program and may be subject to data-use or redistribution constraints. The full input files can be made available confidentially to the editor or reviewers upon reasonable request, where permitted.

## How to run the notebook in Google Colab

1. Open `notebook.ipynb` in Google Colab.
2. Upload `sample_file1.csv`, `sample_file2.csv`, and `sample_file3.csv` to the Colab working directory, or place them in `data_sample/`.
3. Run all notebook cells sequentially from top to bottom.
4. The notebook generates the intermediate datasets, trains the models, evaluates the reported metrics, and creates the output tables and figures used in the manuscript.

## Main workflow reproduced by the notebook

The notebook performs the following steps:

1. Loads and merges the weather and PV generation CSV files.
2. Builds the filtered PV forecasting dataset.
3. Constructs temporal input sequences.
4. Trains the shared CNN-BiLSTM-Attn baseline and the physics-injection variants.
5. Evaluates MAIN TEST and PRED TEST performance.
6. Computes computational-cost summaries.
7. Generates the NWP-source sensitivity analysis using `sample_file3.csv`.
8. Generates seasonal and winter-specific diagnostic outputs.
9. Exports the tables and figures used in the manuscript.

## Expected generated files

During execution, the notebook creates intermediate and output files such as:

- `Dataset_PINN_Input.csv`
- `Dataset_PINN_Input_filtered.csv`
- `table_ii_computational_cost.csv`
- `table_ii_computational_cost_paper.csv`
- `table_nwp_source_sensitivity.csv`
- `table_iv_nwp_source_sensitivity.csv`
- `table_iii_seasonal_rmse.csv`
- `table_iii_b_winter_delta_rmse.csv`
- `fig_1_physics_injection_points.png`
- `fig_1_physics_injection_points.pdf`
- `fig_nwp_source_sensitivity.png`
- `fig_nwp_source_sensitivity.pdf`
- `fig_seasonal_rmse_breakdown.pdf`
- `fig_winter_delta_rmse.pdf`
- `pred_test_onefigure_pure_vs_latent_vs_anchor_residual.png`
- `pred_test_onefigure_pure_vs_latent_vs_anchor_residual.pdf`

Some files may also be copied into the `outputs/` folder by the corresponding export cells.

## NWP-source sensitivity note

The additional Open-Meteo experiment is a forecast-source shift sensitivity test. The models are not retrained or recalibrated on Open-Meteo data. Instead, the Open-Meteo forecast variables are mapped to the same core daily feature schema and used only at evaluation time for the PRED TEST regime. This analysis is intended to assess sensitivity to a change in forecast-weather source, not to provide a full multi-provider NWP benchmark.

## Reproducibility notes

- Fixed random seeds are set where applicable.
- The notebook is designed to be executed sequentially.
- The code uses one-hot encoding for categorical weather-condition variables where applicable.
- The input file names used in this repository are anonymized/generalized as `sample_file1.csv`, `sample_file2.csv`, and `sample_file3.csv`.
- Results may show small numerical differences across CPU/GPU environments and package versions, especially for neural-network training.

## Python environment

The notebook was prepared for Google Colab. To reproduce the environment locally, install the packages listed in `requirements.txt`:

```bash
pip install -r requirements.txt
```

## Data availability statement

The repository includes the Colab notebook, execution instructions, package requirements, generated-output structure, and sample CSV files documenting the expected input schema. The full CSV files are not publicly released at this stage because they are part of an ongoing multi-study research program and may also be subject to data-use or redistribution constraints. They can be made available confidentially to the editor or reviewers upon reasonable request, where permitted.
