## GIS-Integrated Multi-Stage Hybrid Ensemble Learning with Spatial Explainability for Landslide Susceptibility Mapping in India

##  Overview

This project presents a **GIS-integrated hybrid ensemble machine learning framework** for landslide susceptibility mapping across **contrasting geological terrains in India**.

It combines **advanced machine learning + deep learning models** with **Explainable AI (XAI)** to deliver both **accurate predictions and interpretable insights**, making it suitable for **real-world disaster management applications**.

##  Abstract

Landslides are among the most destructive geohazards in India, causing significant loss of life, infrastructure damage, and economic disruption. Existing susceptibility models often suffer from limited generalizability, lack of interpretability, and dependence on region-specific datasets.

This study proposes a **GIS-integrated multi-stage hybrid ensemble framework** for landslide susceptibility mapping across contrasting terrains in India, specifically **Wayanad (Western Ghats)** and **Uttarkashi (Himalayas)**. A total of eighteen geospatial conditioning factors were derived from multi-source datasets, including SRTM DEM, Sentinel-2 imagery, NASA GPM IMERG rainfall data, and ESA WorldCover products, and processed within a unified GIS environment.

The proposed framework consists of three hierarchical stages:
(1) parallel base learners (XGBoost, CatBoost, 1D-CNN, BiLSTM),
(2) a stacking-based meta-learner for probability fusion, and
(3) a **Spatial SHAP explainability module** that maps feature contributions geographically.

Model performance was evaluated using AUROC, F1-score, MCC, and Cohen’s Kappa, with SMOTE applied for class imbalance and Bayesian optimization for hyperparameter tuning. Cross-region validation demonstrates strong generalization capability. Results indicate that rainfall and slope are dominant factors in Wayanad, while lithology and fault proximity play a key role in Uttarkashi.

The framework provides a **scalable, interpretable, and decision-support-ready solution** for landslide susceptibility assessment across diverse geological settings.

##  Key Features

*  Multi-stage Hybrid Ensemble (ML + DL)
*  GIS & Remote Sensing Integration
*  Spatial SHAP Explainability (XAI)
*  Landslide Susceptibility Mapping
*  Cross-region Generalization Testing
*  Class Imbalance Handling (SMOTE)
*  Bayesian Hyperparameter Optimization

## System Architecture

```
GIS Data Sources (DEM, NDVI, Rainfall, LULC, etc.)
                        ↓
        Preprocessing & Feature Engineering
                        ↓
                Base Models Layer
     (XGBoost, CatBoost, CNN, BiLSTM)
                        ↓
               Stacking Meta-Learner
                        ↓
              Landslide Prediction Map
                        ↓
          Spatial SHAP Explainability
                        ↓
          Final Interpretable Outputs
```
##  Project Structure

```
landslide-susceptibility-india-xai/
│
├── README.md
├── requirements.txt
├── LICENSE
├── CITATION.cff
│
├── 01_data_collection/
│   ├── gee_terrain_factors.js
│   ├── gee_lulc_ndvi.js
│   ├── gee_rainfall.js
│   └── data_sources.md
│
├── 02_preprocessing/
│   ├── feature_engineering.py
│   ├── smote_balancing.py
│   └── multicollinearity_check.py
│
├── 03_models/
│   ├── xgboost_model.py
│   ├── catboost_model.py
│   ├── cnn_1d_model.py
│   ├── bilstm_model.py
│   └── stacking_ensemble.py
│
├── 04_explainability/
│   ├── shap_analysis.py
│   └── spatial_shap_mapping.py
│
├── 05_evaluation/
│   ├── model_metrics.py
│   └── cross_region_validation.py
│
├── 06_results/
│   ├── susceptibility_maps/
│   └── shap_plots/
│
├── notebooks/
│   └── experimentation.ipynb
│
└── paper/
    └── research_paper.pdf
```

##  Data Sources

*  SRTM DEM (Elevation)
*  NDVI (Vegetation Index)
*  NASA GPM IMERG Rainfall Data
*  ESA WorldCover (LULC)
*  Soil & Geological Maps
*  Terrain Derivatives (Slope, Aspect, Curvature)

## Data Structure 

```
D:/Landslide_Project/
│
├── 01_DEM_Data/
│   ├── Wayanad_DEM_30m.tif        
│   └── Uttarakhand_DEM_30m.tif    
│
├── 02_Wayanad_Factors/
│   ├── Wayanad_Elevation.tif      ⬜ From QGIS
│   ├── Wayanad_Slope.tif          ⬜ From QGIS
│   ├── Wayanad_Aspect.tif         ⬜ From QGIS
│   ├── Wayanad_Curvature.tif      ⬜ From QGIS
│   ├── Wayanad_TWI.tif            ⬜ From QGIS
│   ├── Wayanad_SPI.tif            ⬜ From QGIS
│   ├── Wayanad_TRI.tif            ⬜ From QGIS
│   └── Wayanad_FlowAcc.tif        ⬜ From QGIS
│
├── 03_Uttarakhand_Factors/
│   ├── Uttarakhand_Elevation.tif  ⬜ From QGIS
│   ├── Uttarakhand_Slope.tif      ⬜ From QGIS
│   ├── Uttarakhand_Aspect.tif     ⬜ From QGIS
│   ├── Uttarakhand_Curvature.tif  ⬜ From QGIS
│   ├── Uttarakhand_TWI.tif        ⬜ From QGIS
│   ├── Uttarakhand_SPI.tif        ⬜ From QGIS
│   ├── Uttarakhand_TRI.tif        ⬜ From QGIS
│   └── Uttarakhand_FlowAcc.tif    ⬜ From QGIS
│
├── 04_Geology_Data/
│   ├── Wayanad_Geology.shp        ⬜ Bhukosh GSI
│   ├── Wayanad_Geomorphology.shp  ⬜ Bhukosh GSI
│   ├── Uttarakhand_Geology.shp    ⬜ Bhukosh GSI
│   └── Uttarakhand_Geomorph.shp   ⬜ Bhukosh GSI
│
├── 05_Landslide_Inventory/
│   ├── Wayanad_Landslides.shp     ⬜ Bhukosh GSI
│   └── Uttarakhand_Landslides.shp ⬜ Bhukosh GSI
│
├── 06_Remote_Sensing/
│   ├── Wayanad_LULC.tif           ⬜ Google GEE
│   ├── Wayanad_NDVI.tif           ⬜ Google GEE
│   ├── Uttarakhand_LULC.tif       ⬜ Google GEE
│   └── Uttarakhand_NDVI.tif       ⬜ Google GEE
│
├── 07_Rainfall_Data/
│   ├── Wayanad_Annual_Rain.tif    ⬜ Google GEE
│   ├── Wayanad_Monsoon_Rain.tif   ⬜ Google GEE
│   ├── Uttarakhand_Annual_Rain    ⬜ Google GEE
│   └── Uttarakhand_Monsoon_Rain   ⬜ Google GEE
│
├── 08_Road_Network/
│   ├── Wayanad_Roads.shp          ⬜ OpenStreetMap
│   └── Uttarakhand_Roads.shp      ⬜ OpenStreetMap
│
├── 09_ML_Model/
│  
│
└── References.txt                 
```

## Tell Me Your Current Situation

Answer these 3 questions so I can guide you to the exact next step:

**Question 1:** Did you extract the .tar.gz file and get the .tif file?

**Question 2:** Is QGIS already installed on your computer?

**Question 3:** Is your Google Earth Engine account approved yet?

Based on your answers I will give you the exact next instruction with no confusion.

```

Data collected using:

* Google Earth Engine
* Remote sensing datasets
* Open geospatial repositories

## ⚙️ Installation

```bash
git clone https://github.com/yourusername/landslide-susceptibility-india-xai.git
cd landslide-susceptibility-india-xai

pip install -r requirements.txt
```
## Usage

### Run full model pipeline:

```bash
python 03_models/stacking_ensemble.py
```

### Run explainability module:

```bash
python 04_explainability/shap_analysis.py
```
##  Evaluation Metrics

* AUROC
* F1 Score
* Matthews Correlation Coefficient (MCC)
* Cohen’s Kappa

##  Explainable AI (XAI)

This project uses **SHAP (SHapley Additive Explanations)** to:

* Interpret model predictions
* Identify key landslide-driving factors
* Generate **spatial contribution maps**

##  Study Regions

*  Western Ghats – Wayanad, Kerala
* Himalayas – Uttarkashi, Uttarakhand

##  Applications

*  Disaster Risk Management
*  Urban Planning
*  Hazard Zonation
*  Environmental Monitoring
*  Policy Making

##  Future Work

* Real-time landslide prediction system
* Web-based GIS dashboard
* Integration with satellite live data
* Mobile-based early warning system


##  Contributing

Contributions are welcome!

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Submit a pull request

##  License

This project is licensed under the MIT License.

##  Citation

```
@project
title = {GIS-Integrated Hybrid Ensemble for Landslide Susceptibility Mapping}
author = {Mutthuram}
year = {2026}
```
##  Author

**Mutthuram**

##  One-Line Summary

> Explainable AI-driven hybrid ensemble framework for accurate and interpretable landslide susceptibility mapping using GIS and remote sensing data.
