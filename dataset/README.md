# Dataset

This folder is used to store the raw dataset required to reproduce the experiments.

## Dataset Source

This project uses the **US-Accidents March 2023** dataset from Kaggle.

Expected raw file name:

```text
US_Accidents_March23.csv
```

The raw dataset is **not included** in this GitHub repository because it is large and may exceed GitHub file size limits. Please download the dataset from Kaggle and place it in this folder.

Expected path:

```text
data/US_Accidents_March23.csv
```

## Task Formulation

The original multi-class severity labels are converted into a binary classification problem:

```text
Severity 4      -> Critical accident
Severity 1/2/3  -> Non-critical accident
```

The final balanced dataset used in the study contains:

| Class | Number of records |
|---|---:|
| Non-critical accidents | 204,711 |
| Severity 4 accidents | 204,710 |
| Total | 409,421 |

## Feature Setting

Direct geographic coordinate features are removed to reduce location-memorisation effects:

```text
Start_Lat
Start_Lng
```

The final feature set uses contextual, non-coordinate features, including:

- accident distance
- temporal features
- meteorological features
- road-context features
- POI/infrastructure indicators
- one-hot encoded categorical variables

## Data Leakage Prevention

One-hot encoding is fitted exclusively on the training split to prevent information leakage into the validation and test sets.

## Important Note

Do not commit the raw dataset to GitHub. The repository `.gitignore` should exclude large data files such as:

```gitignore
data/*.csv
data/*.zip
data/*.parquet
data/*.pkl
data/*.joblib
```

This keeps the repository lightweight, reproducible, and easier to clone.
