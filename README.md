# Breast Cancer Survival Prediction with Clinical and Multi-Omics Data 

This repository contains R/Quarto code for survival modelling using Cox based machine learning method to evaluate the impact of integrating multi-omics data on breast cancer survival prediction. 

## Overview
This project investigates breast cancer overall survival using clinical variables and multi omics data (mRNA expression, methylation, and mutation). Survival outcomes are modeled using extreme gradient boosting with a Cox partial likelihood objective. (Cox-XGBoost). 
Models are trained using :
  1. clinical variables only
  2. clinical variables combined with a single omics layer
  3. clinical variables combined with all omics layer

Predictive performance is evaluated using the concordance index (c-index) and risk stratification divided by quantile is visaulized by Kaplan-Meier Curves. 

## Data Source
Clinical and omics data were obtained from cBioPortal. 
Processed data files are generated and saved under the 'clean_common' directory.  

## Methods 
  Cox XGBoost model with 5 fold cross-validation and grid search for hyperparameter tuning 
  - Evaluation metrics: concordance index 
  - Visualization: Kaplan-Meier Survival Curves and risk tables 

## Repository Structure 
Stage 1: Data cleaning & feature engineering (`datacleaning_pca.qmd`)
1. `input/` — raw tab-delimited files from cBioPortal (clinical + omics).
2. `output/clean_full/` — intermediate cleaned outputs (e.g., `clinical_master.csv`).
3. `output/splits/` — train/test identifiers (e.g., `idx_train.rds`, `train_ids.csv`, `test_ids.csv`).
4. `output/clean_common/` — final modeling datasets (train/test CSVs for each feature set):
   1. `train_clinical.csv`, `test_clinical.csv`
   2. `train_mrna.csv`, `test_mrna.csv`
   3. `train_meth.csv`, `test_meth.csv`
   4. `train_mut.csv`, `test_mut.csv`
   5. `train_all_omics.csv`, `test_all_omics.csv`

Stage 2: Cox-XGBoost modeling & evaluation (`cox_xgboost.qmd`)
1. Input: train/test CSVs from `output/clean_common/`.
2. Output:
   1. `single_models/` — trained models (`xgb_cox_*.json`) and selected hyperparameters (`best_params_*.csv`).
   2. `single_predictions/` — test-set risk predictions (`test_risk_*.csv`).
   3. Figures (repo root): `Kaplan Meier Curve.png`, `Risk Tables.png`.

### How to Run 
1. Clone this repository
2. Open the datacleaning_pca.qmd file in RStudio first.
3. Update the 'base_dir' path to match your local environment from the datacleaning_pca.qmd.
4. Run the datacleaning_pca.qmd
5. After running datacleaning_pca.qmd, run 'cox_xgboost.qmd' file with a desired train and test files from the 'clean_common' folder. 

## Results Summary 

The clinical only model achieved a concordance index of 0.699, while models incorporating a single omics layer - methylation, mutation, and mRNA) showed concordance indices ranging from 0.707 to 0.709. 
The model integrating all omics layers achieved the highest performance with a concordance index of 0.715.
Kaplan-Meier curves and risk table demonstrate clear separation between predicted risk groups. 

## Authors 
Chaewon Oh (Brown University), Ching-Wen Mai (Case Western Reserve University) 


