# Machine Learning for Early Dengue Diagnosis — Munshiganj, Bangladesh

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.12](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20780239.svg)](https://doi.org/10.5281/zenodo.20780239)

## Overview

This repository contains the complete analysis code, results, and figures for the study:

> **Rahman MR, Rose JI, Rahman MR. Machine learning for early dengue diagnosis using routine clinical and haematological parameters: evidence from a prospective outbreak cohort in Munshiganj, Bangladesh. *PLOS Neglected Tropical Diseases*. 2026. (Under review)**

The study trains and compares six supervised machine learning classifiers (Logistic Regression, KNN, SVM, Random Forest, XGBoost, LightGBM) on a publicly available dataset of 1,018 patients from Munshiganj, Dhaka, Bangladesh, collected during confirmed dengue outbreak periods. SHAP-based interpretability is used to identify which features drive predictions and by how much.

## Key Results

| Model | Accuracy (%) | F1-Score (%) | AUC-ROC |
|---|---|---|---|
| Random Forest | 99.02 | 98.92 | 0.9934 |
| XGBoost | 99.02 | 98.92 | 0.9950 |
| LightGBM | 98.53 | 98.25 | 0.9908 |

**CBC-only (platelet + WBC): XGBoost 99.02%, AUC-ROC 0.9925**

**10-fold CV XGBoost: Accuracy 98.72% ± 0.63%, F1 99.07% ± 0.46%**

**Top SHAP predictors:** Platelet Count (3.657) and WBC Count (3.656) — nearly tied and far ahead of all other features.

## Repository Structure

```
dengue-ml-diagnosis/
├── README.md
├── LICENSE
├── requirements.txt
├── CITATION.cff
├── .zenodo.json
├── dengue_ml_pipeline.py          # Complete reproducible pipeline script
├── data/
│   └── README_data.md             # Data dictionary and download instructions
├── models/
│   └── README_models.md           # Notes on saved model objects
└── results/
    ├── model_results_full.csv     # All 6 models, full feature set
    ├── model_results_cbc.csv      # All 6 models, CBC-only feature set
    ├── shap_importance.csv        # SHAP values ranked
    └── figures/
        ├── Fig1.png               # Class distribution
        ├── Fig2.png               # Box plots by outcome
        ├── Fig3.png               # Model comparison bar chart
        ├── Fig4.png               # Confusion matrix (XGBoost)
        ├── Fig5.png               # ROC curve (XGBoost)
        ├── Fig6.png               # SHAP feature importance
        └── Fig7.png               # Platelet vs WBC scatter plot
```

## Data Source

The dataset is publicly available on Mendeley Data:

**Mojumdar MU, et al. Structured clinical and haematological dataset for early dengue diagnosis in Bangladesh. Mendeley Data; 2024. V1.**
DOI: 10.17632/673swz9tb4.1
URL: https://data.mendeley.com/datasets/673swz9tb4/1

Download the dataset and place `Dengue_clinical_dataset.csv` in the `data/` directory. The dataset is not redistributed here.

## Quick Start

```bash
git clone https://github.com/RafinRahman/dengue-ml-diagnosis.git
cd dengue-ml-diagnosis

python3 -m venv venv
source venv/bin/activate

pip install -r requirements.txt

# Download dataset from Mendeley and place in data/
python3 dengue_ml_pipeline.py --data "data/Dengue_clinical_dataset.csv"
```

## Reproducibility

All analyses use a fixed random seed of 42 throughout. Python package versions are pinned in `requirements.txt`.

## Citation

```bibtex
@article{rahman2026dengue,
  title={Machine learning for early dengue diagnosis using routine clinical and haematological parameters: evidence from a prospective outbreak cohort in Munshiganj, Bangladesh},
  author={Rahman, Md Rafin and Rose, Jafren Iqbal and Rahman, Md Jubayar and Rahman, Md Rofiqur},
  journal={PLOS Neglected Tropical Diseases},
  year={2026},
  note={Under review}
}
```

For the Zenodo archive:
```
Rahman MR, Rose JI, Rahman MJ, Rahman MR. (2026). Analysis code for: Machine learning for early dengue diagnosis using routine clinical and haematological parameters. Zenodo. https://doi.org/10.5281/zenodo.20780239
```

## License

Code: MIT License. Data: Mendeley Data CC BY 4.0 (source dataset). Results and figures: CC-BY 4.0.

## Authors

- **Md Rafin Rahman** (Corresponding Author) — ideSHi, Dhaka, Bangladesh. mrahman@ideshi.org
- **Jafren Iqbal Rose** — Shaheed Monsur Ali Medical College and Hospital, Dhaka, Bangladesh
- **Md Jubayar Rahman** — Roboway Technologies, Dhaka, Bangladesh
- **Md Rofiqur Rahman** — ideSHi, Dhaka, Bangladesh
