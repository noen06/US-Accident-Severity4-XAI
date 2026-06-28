# US-Accident-Severity4-XAI
# Explainable Machine Learning for Severity 4 Traffic Accident Detection

This repository contains the code and experimental materials for our paper:

**Explainable Machine Learning for Severity 4 Traffic Accident Detection**

## Overview

This study formulates Severity 4 traffic accident detection as a binary classification task using the US-Accidents dataset. We compare Logistic Regression, Random Forest, XGBoost, LightGBM, and CatBoost. Random Forest achieves the best numerical performance, while LightGBM is selected for explainability analysis using SHAP and LIME.

## Dataset

The dataset used in this study is the US-Accidents March 2023 dataset from Kaggle.

Due to GitHub file size limitations, the raw dataset is not included in this repository. Please download it from Kaggle and place it in the `data/` directory.

Expected path: https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents

```text
data/US_Accidents_March23.csv
