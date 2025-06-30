Teledermatology Skin Lesion Classification — Capstone 3

Springboard Data Science Career Track – Final Project Author: Manuel Ramirez Chimarro Date: May 2025

1  Executive Summary

This capstone project addresses the challenge of early and accurate classification of skin lesion types through teledermatology. Using the HAM10000 dataset — which includes ~10,000 dermoscopic images and structured metadata — I evaluated a range of models, including logistic regression, random forest, CNNs, and fine-tuned EfficientNet architectures.

The final model, EfficientNetB3, achieved a 64% accuracy and showed a significant performance gain on minority lesion types compared to EfficientNetB0 (46%). These findings support the deployment of ML-assisted triage systems for skin conditions.

2  Problem Statement

Skin cancer and dermatological disorders require early detection for effective treatment. In underserved or remote areas, specialist access is limited. This project proposes an automated tool to classify skin lesions from both dermoscopic images and patient metadata, improving remote diagnostics via teledermatology.

3  Dataset Description

Source: HAM10000

Samples: ~10,000 dermoscopic images

Lesion Classes: nv, mel, bkl, bcc, akiec, vasc, df

Metadata: age, sex, lesion localization, diagnosis type

4  Methodology

Preprocessing

Images resized to 64x64 and normalized.

Metadata cleaned, encoded, and scaled.

Combined image paths and metadata labels for modeling.

Baseline Models (Metadata Only)

Model

Accuracy

Precision

Recall

F1-Score

Logistic Regression

0.71

0.65

0.71

0.66

Random Forest

0.72

0.68

0.72

0.69

CNN on Images

Simple CNN with 2 convolutional blocks.

Accuracy: 75%

EfficientNetB0

Transfer learning + data augmentation (rotation, flip, brightness).

Applied focal loss to handle class imbalance.

Accuracy: 78%

EfficientNetB3 (Final Model)

Combined image features with metadata in a multimodal architecture.

Applied extensive augmentation and tuned training.

Final Accuracy: 64% (on stratified validation set)

5  Final Evaluation Metrics (EfficientNetB3)

Class

Precision

Recall

F1-Score

Support

akiec

0.49

0.44

0.46

220

bcc

0.82

0.94

0.87

1341

bkl

0.36

0.17

0.24

23

df

0.32

0.25

0.28

223

mel

0.64

0.25

0.36

28

nv

0.30

0.17

0.22

103

vasc

0.30

0.09

0.14

65

Overall Accuracy





0.64

2003

6  Visualizations

Training vs. validation loss and accuracy curves

Confusion matrix for class-level performance

Validation grid (true vs. predicted labels)

7  Repository Structure

File

Description

01_data_wrangling.ipynb

Data cleaning and preprocessing

02_exploratory_data_analysis.ipynb

Visual EDA of lesion distribution and features

03_preprocessing_and_training.ipynb

Metadata-only model training

04_MODELING.ipynb

CNN, EfficientNet, and multimodal pipelines

model_metrics.md

Final model metrics summary

teledermatology_cnn_model.keras

Trained CNN model file

assets/

Static plots and confusion matrix images

8  Recommendations

Deploy EfficientNetB3 in a clinical triage tool for general practitioners.

Address underrepresented classes with synthetic oversampling or GANs.

Consider lightweight CNNs (e.g., MobileNet) for mobile applications.

9  Future Work

Refine multimodal architecture with hyperparameter tuning

Try ensemble methods to boost classification performance

Validate on external clinical datasets

Add Grad-CAM visualizations for interpretability

⚠️ Disclaimer: This model is a research prototype and not intended for clinical use without regulatory clearance.
