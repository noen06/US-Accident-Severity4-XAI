# Explainable Machine Learning for Severity 4 Traffic Accident Detection

This repository contains the code and experimental materials for the study:

**Explainable Machine Learning for Severity 4 Traffic Accident Detection**

## Overview

This project detects **Severity 4 traffic accidents** using the US-Accidents dataset. The task is formulated as a binary classification problem:

```text
Severity 4      -> Critical accident
Severity 1/2/3  -> Non-critical accident
```

The study compares six machine learning models and applies explainable AI methods to interpret high-severity predictions.

## Models

The following models are evaluated:

- Logistic Regression
- Multi-Layer Perceptron (MLP)
- CatBoost
- XGBoost
- LightGBM
- Random Forest

Random Forest achieves the best numerical performance, while LightGBM is selected for SHAP and LIME explainability analysis because it provides competitive performance and strong compatibility with tree-based explanation methods.

## Dataset

The project uses the **US-Accidents March 2023** dataset from Kaggle.

The raw dataset is not uploaded to this repository due to file size limitations. Please download the dataset manually and place it at:

```text
data/US_Accidents_March23.csv
```

More details are available in:

```text
data/README.md
```

## Experimental Setting

The final balanced binary dataset contains:

| Class | Number of records |
|---|---:|
| Non-critical accidents | 204,711 |
| Severity 4 accidents | 204,710 |
| Total | 409,421 |

Direct geographic coordinates are removed to reduce location-memorisation effects:

```text
Start_Lat
Start_Lng
```

After preprocessing and one-hot encoding, the final feature set contains **73 features**.

The dataset is split using stratified sampling:

| Split | Records | Approx. Ratio |
|---|---:|---:|
| Training | 295,805 | 72% |
| Validation | 52,202 | 13% |
| Test | 61,414 | 15% |

## Results

| Model | Accuracy | Weighted F1 | F1 Severity 4 | AUC-ROC |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.6635 | 0.6634 | 0.6597 | 0.7170 |
| MLP | 0.7687 | 0.7684 | 0.7760 | 0.8367 |
| CatBoost | 0.7883 | 0.7865 | 0.8059 | 0.8573 |
| XGBoost | 0.7950 | 0.7938 | 0.8093 | 0.8646 |
| LightGBM | 0.7964 | 0.7952 | 0.8108 | 0.8673 |
| Random Forest | 0.8022 | 0.8010 | 0.8164 | 0.8756 |

LightGBM is additionally evaluated using 5-fold stratified cross-validation to assess model stability across different data partitions.

## Explainability

The study uses:

- **SHAP** for global feature attribution
- **LIME** for instance-level prediction explanation

The explanation analysis identifies features such as `Distance(mi)`, temporal patterns, visibility, weather conditions, and road-context indicators as important predictors associated with Severity 4 predictions.

Note: These explanations describe model prediction behavior and should not be interpreted as causal claims.

## Repository Structure

```text
.
├── data/
│   └── README.md
├── notebooks/
│   └── Us_sev4_fina.ipynb
├── paper/
│   └── US_Accident_sev4.pdf
├── figures/
├── README.md
├── requirements.txt
└── .gitignore
```

## How to Run

Install the required packages:

```bash
pip install -r requirements.txt
```

Then open the notebook:

```bash
jupyter notebook notebooks/Us_sev4_fina.ipynb
```

Make sure the dataset is placed at:

```text
data/US_Accidents_March23.csv
```

## Citation

If you use this repository, please cite the original US-Accidents dataset paper:

Moosavi, S., Samavatian, M. H., Parthasarathy, S., and Ramnath, R.  
**A Countrywide Traffic Accident Dataset.**  
arXiv preprint arXiv:1906.05409, 2019.
