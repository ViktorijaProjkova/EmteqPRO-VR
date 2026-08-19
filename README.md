# EmteqPRO-VR: Valence and Arousal Prediction

This repository contains the analysis pipeline for predicting valence and arousal from multimodal EmteqPRO sensor data collected during VR-based empathy scenarios.

The project includes exploratory data analysis, statistical analysis, feature extraction, and participant-independent machine learning evaluation. The final modelling approach uses modality-level stacking to combine information from facial activation, EMG activation, expression intensity, breathing, and heart-rate-variability-related features.

## Project Overview

Virtual reality provides a controlled environment for eliciting emotional responses, while wearable sensors enable continuous tracking of physiological and facial activity. This project investigates whether multimodal EmteqPRO features can be used to analyse and predict self-reported valence and arousal during empathy-inducing VR scenes.

The analysis focuses on scene-level affective responses, statistical differences between empathy scenes, and low-versus-high valence and arousal prediction using participant-independent evaluation.

## Repository Structure

```text
EmteqPRO-VR/
│
├── 01_data_understanding.ipynb
├── feature_extraction.ipynb
├── valence_arousal_analysis.ipynb
├── statistical_analysis.ipynb
├── ML_arousal_valence_prediction.ipynb
├── modality_stacking_models.ipynb
│
├── ml_results/
├── ml_global_figures/
│
├── .gitignore
└── README.md
```

## Notebooks

### 01_data_understanding.ipynb

Performs the initial inspection of the dataset, participant recordings, metadata, available sensor files, missing values, and inconsistencies.

### feature_extraction.ipynb

Extracts scene-level features from the EmteqPRO recordings. The extracted features represent facial activation, EMG activation, expression intensity, breathing, and heart-rate-variability-related signals.

### valence_arousal_analysis.ipynb

Explores the self-reported valence and arousal targets, their distributions across scenes and participants, and the preparation of binary low-versus-high classification targets.

### statistical_analysis.ipynb

Performs statistical analysis of self-reported valence and arousal across the empathy scenes. Friedman and Wilcoxon signed-rank tests are used to identify significant scene-dependent differences.

### ML_arousal_valence_prediction.ipynb

Contains the global machine learning analysis for binary valence and arousal prediction, including preprocessing, model comparison, and Leave-One-Participant-Out evaluation.

### modality_stacking_models.ipynb

Contains the final modality-level stacking approach. Separate first-layer models are trained on modality-specific feature groups, and their predicted probabilities are combined using a second-layer meta-classifier.

## Machine Learning Evaluation

The final prediction task was formulated as binary classification for both valence and arousal. Medium responses were excluded in order to focus on clearer low-versus-high affective contrasts.

Model evaluation was performed using Leave-One-Participant-Out cross-validation. In each fold, all samples from one participant were held out for testing, while training was performed using the remaining participants. This strategy evaluates generalization to unseen participants and reduces participant-level data leakage.

The main evaluation metrics were accuracy, balanced accuracy, macro F1-score, and weighted F1-score. Due to class imbalance, balanced accuracy and macro F1-score were used as the main comparison metrics.

## Final Modelling Approach

The final modelling approach is based on modality-level stacking. In the first layer, separate models are trained on modality-specific feature groups:

- facial activation
- EMG activation
- expression intensity
- breathing-related features
- heart-rate-variability-related features

Each modality-specific model outputs a predicted probability for the high class. These probabilities are then used as input to a second-layer meta-classifier, which produces the final low-versus-high prediction.

## Results Summary

The best valence stacking configuration achieved a balanced accuracy of approximately 0.705 and a macro F1-score of approximately 0.683.

The best arousal stacking configuration achieved approximately 0.462 for both balanced accuracy and macro F1-score.

These results indicate that valence was predicted more reliably across unseen participants, while arousal remained more challenging to generalize from the extracted scene-level features.

## Notes on Data

The raw participant data is not included in this repository.

The notebooks are intended to be run with the original EmteqPRO-VR dataset available locally in the expected project structure. Large raw data files, generated outputs, and local system files should not be committed unless required for reproducibility.

## Requirements

The project is implemented in Python using Jupyter notebooks.

Main libraries used:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
imbalanced-learn
xgboost
```

Install the required packages using:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn xgboost
```

## How to Run

Run the notebooks in the following order:

```text
1. 01_data_understanding.ipynb
2. feature_extraction.ipynb
3. valence_arousal_analysis.ipynb
4. statistical_analysis.ipynb
5. ML_arousal_valence_prediction.ipynb
6. modality_stacking_models.ipynb
```

The machine learning notebooks depend on the processed feature dataset created during feature extraction.

## Project Status

This repository contains the completed analysis workflow for valence and arousal prediction from EmteqPRO sensor data collected during VR-based empathy scenarios.

The final analysis focuses on participant-independent prediction using modality-level stacking and Leave-One-Participant-Out cross-validation.