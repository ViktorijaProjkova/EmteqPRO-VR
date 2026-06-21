# EmteqPRO-VR: Valence and Arousal Analysis

This repository contains the analysis pipeline for the EmteqPRO-VR project, focused on analysing and predicting **valence** and **arousal** from EmteqPRO sensor data collected during VR-based empathy scenarios.

The project includes data understanding, feature extraction, exploratory analysis, statistical analysis, and machine learning models for valence and arousal prediction.

---

## Project Overview

The aim of this project is to investigate whether features extracted from EmteqPRO sensor recordings can be used to analyse and predict participants’ emotional responses during VR experiences.

The emotional response is represented through two target dimensions:

* **Valence** – how positive or negative the emotional response is
* **Arousal** – how calm or activated the emotional response is

The analysis is based on participant-level recordings from empathy-related VR scenes. The extracted features are used for both statistical exploration and machine learning classification.

---

## Repository Structure

```text
EmteqPRO-VR/
│
├── 01_data_understanding.ipynb
├── feature_extraction.ipynb
├── valence_arousal_analysis.ipynb
├── statistical_analysis.ipynb
├── ML_arousal_valence_prediction.ipynb
│
├── ml_results/
├── ml_global_figures/
│
├── .gitignore
└── README.md
```

---

## Notebooks

### `01_data_understanding.ipynb`

This notebook contains the initial exploration of the dataset.

It includes:

* inspection of the available participant data
* checking the file structure and available recordings
* understanding sensor columns and metadata
* identifying missing values and inconsistencies
* preparing the logic for later feature extraction

---

### `feature_extraction.ipynb`

This notebook performs feature extraction from the EmteqPRO recordings.

It creates the processed dataset used for later statistical analysis and machine learning. The feature extraction focuses on video-level segments related to the VR empathy scenes.

Main steps include:

* loading participant recordings
* identifying the relevant VR scenes
* extracting features from sensor signals
* keeping the selected minimum and maximum features
* preparing valence and arousal labels
* saving the processed feature dataset

The extracted dataset is later used as input for statistical analysis and machine learning.

---

### `valence_arousal_analysis.ipynb`

This notebook contains exploratory analysis of valence and arousal.

It focuses on understanding the distribution and behaviour of the target variables.

It includes:

* analysis of valence and arousal labels
* comparison between participants and scenarios
* visualisation of label distributions
* inspection of potential class imbalance
* preparation of binary valence and arousal targets

---

### `statistical_analysis.ipynb`

This notebook contains statistical analysis of the extracted features.

It investigates whether the extracted EmteqPRO features show meaningful differences across valence and arousal conditions.

It includes:

* descriptive statistics
* comparison of feature values across emotional states
* analysis of feature relevance
* visual exploration of patterns in the data

---

### `ML_arousal_valence_prediction.ipynb`

This notebook contains the machine learning pipeline for valence and arousal prediction.

The notebook trains and evaluates models for predicting binary valence and binary arousal classes.

The analysis includes:

* preprocessing of the extracted feature dataset
* creation of binary valence and arousal targets
* feature engineering from paired minimum and maximum columns
* handling class imbalance
* feature selection
* training multiple classification models
* participant-aware evaluation
* comparison of global models
* confusion matrices for the best-performing models
* participant-level result inspection

The evaluated models include classical machine learning classifiers such as:

* Logistic Regression
* Support Vector Machine
* Random Forest
* Gradient Boosting
* k-Nearest Neighbors
* Decision Tree
* Gaussian Naive Bayes
* SGD Classifier
* XGBoost, when available

---

## Output Folders

### `ml_results/`

This folder contains saved machine learning results, including model performance tables and prediction outputs.

### `ml_global_figures/`

This folder contains generated figures from the global model analysis, including performance plots and confusion matrices.

---

## General Pipeline

The full workflow follows these steps:

1. **Data understanding**
   The dataset, available files, sensor columns, and participant recordings are inspected.

2. **Feature extraction**
   Video-level EmteqPRO features are extracted from the relevant VR empathy scenes.

3. **Valence and arousal analysis**
   The target labels are explored and binary classification targets are prepared.

4. **Statistical analysis**
   Feature behaviour is analysed and patterns across emotional conditions are compared.

5. **Machine learning modelling**
   Models are trained and evaluated for valence and arousal prediction.

6. **Result visualisation**
   Model comparison plots, confusion matrices, and participant-level outputs are generated and saved.

---

## Machine Learning Evaluation

The machine learning analysis focuses on predicting:

* binary valence
* binary arousal

The evaluation is designed to account for participant-level differences. This is important because emotional responses can vary strongly between participants, especially in VR-based experiments.

The main evaluation outputs include:

* balanced accuracy
* macro F1-score
* confusion matrices
* model comparison plots
* participant-level prediction analysis

Balanced accuracy and macro F1-score are used because the target classes is imbalanced.

---

## Notes on Data

The raw participant data is not included in this repository.

The notebooks are intended to be run with the original EmteqPRO-VR dataset available locally in the expected project structure.

Large raw data files, generated outputs, and local system files should not be committed unless they are needed for reproducibility.

---

## Requirements

The project is implemented in Python using Jupyter notebooks.

Main Python libraries used across the analysis include:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
imbalanced-learn
xgboost
```

To install the required packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn xgboost
```

---

## How to Run

Run the notebooks in the following order:

```text
1. 01_data_understanding.ipynb
2. feature_extraction.ipynb
3. valence_arousal_analysis.ipynb
4. statistical_analysis.ipynb
5. ML_arousal_valence_prediction.ipynb
```

The machine learning notebook depends on the processed dataset created during feature extraction.

---

## Project Status

This repository contains the completed analysis workflow for the valence and arousal prediction task.

The current results focus on global machine learning models and participant-level inspection, with the possibility of further extending the work toward more personalised modelling strategies.

---

