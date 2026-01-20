# Breast Cancer Survival Prediction with Clinical and Multi-Omics Data 

This repository contains R/Quarto code for survival modelling using Cox based machine learning method to evalute the impact of integrating multi-omics data on breast cancer survival prediction. 

## Overview
This project investigates breast cancer overall survival using clinical variables and multi omics data(mRNA expression, methylation, and mutation). Survival outcomes are modeled using extreme gradient boosting with a Cox partial likelihood objective. (Cox-XGBoost). 
Models are trained using :
  1. clinical variables only
  2. clinical variables combined with a single omics layer
  3. clinical variables combined with all omics layer

Predictive perforamnce is evaluated using the concordance index (c-index) and risk stratification divided by quantile is visaulized by Kaplan-Meier Curves. 

## Data Source
Clinical and omics data were obtained from cBioPortal. 
Processed data files are generated and saved under the 'clean_common' directory.  

## Repository Structure 
'Old Code' folder contains old code used to generate the cox_xgboost.qmd and datacleaning_pca.qmd 
'clean_common' folder ...
'clean_full' folder ...
'splits' folder ...
cox_xgboost.html and cox_xgboost.qmd has the model pipeline and contains concordance index, risk tables, and Kaplan-Meier Curves. 
...

### How to Run 
1. Clone this repository
2. Open the datacleaning_pca.qmd file ('.qmd') in RStudio first.
3. Update the 'base_dir' path to match your local environment from the datacleaning_pca.qmd.
4. Run the datacleaning_pca.qmd
5. After running datacleaning_pca.qmd, run 'cox_xgboost.qmd.'

## Results Summary 

The clinical only model achieved a concordance index of 0.699, while models incorporating a single omics layer - methylation, mutation, and mRNA) showed concordance indices ranging from 0.707 to 0.709. 
The model integrating all omics layers achieved the highest performance with a concordance index of 0.715.
Kaplan-Meier curves and risk table demonstrate clear separation between predicted risk groups. 

## Authors 
Chaewon Oh (Brown University), Chingwen Mai ( please double check! I might have spelled your name wrong ) 


