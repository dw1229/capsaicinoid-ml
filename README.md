# Capsaicinoid Compound Classification

**Author:** Dongwan Kim

## Project Overview

A machine learning pipeline for classifying capsaicinoid-related compounds into 3 chemical families using molecular descriptors and Elastic Net feature selection.

### Compound Classes

- **Class 0 — Capsaicinoids** (12): Capsaicin, Dihydrocapsaicin, Nonivamide, Resiniferatoxin, ...
- **Class 1 — Vanilloids / Gingerols** (12): 6-Gingerol, 6-Shogaol, Zingerone, Vanillin, Eugenol, ...
- **Class 2 — Spice Alkaloids** (12): Piperine, Piperlongumine, Chavicine, Capsazepine, ...

## Current Progress

### 01 — Data Collection (`01_data_collection.ipynb`)

- Fetches SMILES for 36 compounds from the PubChem PUG REST API
- Converts SMILES to RDKit Mol objects and computes ~200 molecular descriptors
- Preprocesses features (drops zero-variance columns, handles NaN/inf)
- Saves the final dataset to `data/molecules.csv` (36 compounds × 152 features)

### 02 — EDA & Feature Selection (`02_EDA_and_PCA.ipynb`)

- Class distribution bar chart (balanced: 12 per class)
- Feature correlation heatmap (top 20 by variance) — high redundancy among molecular weight-related features
- Boxplots of top 5 features by variance — only Ipc effectively separates classes
- 70/30 stratified train/test split (split before any preprocessing to prevent data leakage)
- Elastic Net feature selection: grid search over L1_ratio and C, reduces 165 features → 30
- StandardScaler fit on train only
- 2D PCA scatter plot for visualization

Planned:

- `03_classifier.ipynb` — PyTorch deep learning classifier (practice exercise)
- Possible additional data analysis

## Tech Stack

- **Data Collection**: PubChem PUG REST API, RDKit
- **Data Processing / EDA**: pandas, NumPy, matplotlib, seaborn
- **Feature Selection**: scikit-learn (Elastic Net LogisticRegression, StandardScaler, PCA)
