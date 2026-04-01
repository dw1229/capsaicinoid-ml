# Capsaicinoid Compound Classification with PCA & PyTorch MLP

## Project Overview

A machine learning pipeline for classifying capsaicinoid-related compounds into 3 chemical families using molecular descriptors, PCA, and a PyTorch MLP classifier.

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


Planned notebooks (to be added):

- `02_EDA_and_PCA.ipynb` — Exploratory data analysis + PCA visualization
- `03_MLP_classifier.ipynb` — PyTorch MLP training & evaluation

## Tech Stack

- **Data Collection**: PubChem PUG REST API, RDKit
- **Data Processing**: pandas, NumPy

Additional tools (scikit-learn, PyTorch, Plotly, etc.) will be added as notebooks 02 and 03 are developed.
