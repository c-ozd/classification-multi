# Forest Cover Type Prediction
---

## Introduction

This project focuses on predicting the forest cover type from cartographic variables only. It is a multi-class classification problem where the goal is to determine the cover type for 30x30 meter cells obtained from US Geological Survey (USGS) and US Forest Service (USFS) data.

## Dataset

The dataset comes from [Kaggle: Forest Cover Type Dataset](https://www.kaggle.com/datasets/uciml/forest-cover-type-dataset), **containing 581k entries** and **55 columns** describing forest cover types.

## Methodology

**<u>Data Investigation</u>**
    - A mid-to-big sized imbalanced dataset $\longrightarrow$ Holdout CV with Stratification 
    - Conversion of One Hot Encoded Soil_Type columns to One Single Soil_Type_Cat column (saving 40 columns $\longrightarrow$ reduced complexity)
    - Soil Types, Wilderness Area and Elevation are determined to be the most important features as per Feature Importance graph of XGBoost which validates also early EDA work
    
**<u>Hyperparameter Tuning</u>**
    - Optuna is used to find the optimal hyperparameters yielding the highest F1 Macro Scores
    - Hyperparameter Tuning is performed on subsampled dataset (5% of the whole) to speed up the process

**<u>Model Training and Evaluation</u>**
    - Models are scored based on **F1 Macro Averages**


**Models Trained and Evaluated**

* Random Forest Classifier
* XGBoost Classifier
* LightGBM Classifier

## Results

The best performing model (XGBoost Classifier) achieved **0.9489 F1-Macro Average**

                precision    recall  f1-score   support

           0       0.97      0.97      0.97     42368
           1       0.97      0.98      0.98     56661
           2       0.97      0.97      0.97      7151
           3       0.90      0.88      0.89       549
           4       0.94      0.90      0.92      1899
           5       0.95      0.94      0.95      3473
           6       0.97      0.97      0.97      4102

    accuracy                           0.97    116203
    macro avg      0.95      0.94      0.95    116203
    weighted avg   0.97      0.97      0.97    116203
