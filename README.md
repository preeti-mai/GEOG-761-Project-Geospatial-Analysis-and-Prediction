# GEOG-761 · Geospatial Analysis & Prediction (Seagrass)

Predicting and mapping seagrass habitat using satellite-derived predictors and machine-learning models.  
This repository contains reproducible Jupyter notebooks for classical ML (Random Forest, XGBoost) and a neural-network ensemble, developed for GEOG-761 (University of Auckland).

> **Status:** coursework project for geography.


## Repository structure

```
.
├── 761_Seagrass_Analysis.ipynb              # End-to-end data prep & EDA
├── RandomForest.ipynb                       # Random Forest training & evaluation
├── seagrass_xgboost.ipynb                   # XGBoost training & evaluation
├── Neural_network_combined_3_models.ipynb   # Neural-network ensemble workflow
└── NN models/                               # Supporting NN experiments/utilities
```


## Quick start

### 1) Clone
```bash
git clone https://github.com/preeti-mai/GEOG-761-Project-Geospatial-Analysis-and-Prediction.git
cd GEOG-761-Project-Geospatial-Analysis-and-Prediction
```

### 2) Create an environment (choose one)

**Conda (recommended for geospatial libs)**
```bash
conda env create -f environment.yml
conda activate geog761
```

**Or: pip / venv**
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -U pip
pip install -r requirements.txt
```

> If you plan to run the neural-network notebook, install a deep-learning framework matching the imports in that notebook (e.g., `tensorflow` or `torch`/`torchvision`).

### 3) Launch notebooks
```bash
jupyter lab
```

Recommended run order:
1. `761_Seagrass_Analysis.ipynb`
2. `RandomForest.ipynb`
3. `seagrass_xgboost.ipynb`
4. `Neural_network_combined_3_models.ipynb`

  

## Data
This project expects:
- **Seagrass observations** (points/polygons; presence/absence or density).
- **Environmental predictors** (rasters; e.g., bathymetry, slope, turbidity, chlorophyll, SST, distance-to-shore).

> Place raw data under a local `data/` directory (not committed).  
> Update paths at the top of each notebook. If data are restricted, add `data/README.md` with access instructions.

  

## Outputs
Each notebook saves metrics/figures and (optionally) raster predictions. Typical artifacts:
- Classification metrics (Precision/Recall/F1/IoU, ROC/AUC).
- Confusion matrices and feature importance (RF/XGB).
- Habitat probability maps (GeoTIFF/COG) and preview plots.

Create an `outputs/` folder locally if it doesn’t exist.

  

## Reproducibility
- Set seeds in notebooks where applicable.
- Keep environment pinned (see `environment.yml` / `requirements.txt`).
- Log model configs (hyperparameters, feature lists, CRS, and training windows).

  

## Troubleshooting
- **GDAL/PROJ errors:** prefer conda-forge builds (`conda install -c conda-forge gdal rasterio geopandas`).
- **CRS mismatch:** reproject all vectors/rasters to a common CRS before sampling.
- **Memory limits:** use windowed raster reads, tiling, or downsampling for predictions.

  

## Roadmap

- [ ] Add paths config via `.env` (e.g., `DATA_DIR`, `OUTPUT_DIR`) and read with `os.environ`.
- [ ] Pin random seeds and log training configs.
- [ ] Script notebook steps into a lightweight CLI under `src/`.
- [ ] Add tests for data loaders and predictors.
- [ ] Publish sample tiles for quick runs.

  

## How to cite

```
@misc{geog761_seagrass_2025,
  title  = {GEOG-761 Project: Geospatial Analysis and Prediction (Seagrass)},
  author = {Project contributors},
  year   = {2025},
  url    = {https://github.com/preeti-mai/GEOG-761-Project-Geospatial-Analysis-and-Prediction}
}
```
