# Teledermatology Skin Lesion Classification capstone

This repository presents the final capstone project for the Springboard Data Science Career Track. The goal was to develop a machine learning solution for classifying dermatological skin lesions using the HAM10000 dataset, enabling improved triage and early diagnosis support in teledermatology.

##  Project Overview

- **Domain**: Healthcare / Dermatology
- **Objective**: Classify seven types of skin lesions from image and metadata inputs
- **Dataset**: [HAM10000](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000)
- **Techniques Used**: CNNs, EfficientNet, Metadata Fusion, Focal Loss, Data Augmentation

## Problem Statement

Dermatological triage, especially in remote areas, can benefit from AI support to classify skin lesions and prioritize care. The problem is class imbalance and difficulty in identifying minority class lesions (e.g., melanoma, vascular lesions).

## Modeling Summary

The modeling process explored:
- **Baseline Models**: Logistic Regression, Random Forest using patient metadata
- **CNN Model**: Custom CNN using lesion images
- **EfficientNetB0 & B3**: Fine-tuned pretrained models with frozen base layers
- **Multimodal Model**: Combined image and metadata input
- **Focal Loss**: Used to improve minority class performance
- **Data Augmentation**: Strong augmentation applied to improve generalization

➡ **Final model** achieved ~78% accuracy with improved recall on minority classes.


## Key Results

- Focal loss improved sensitivity to rare lesions
- CNN outperformed metadata-only models
- Final validation accuracy: **~78%**
- Improved recall for `mel` (melanoma) and `vasc` (vascular) lesions

## 📂 Project Files

| File | Description |
|------|-------------|
| `01-data-wrangling.ipynb` | Data cleaning and preprocessing |
| `02_exploratory_data_analysis.ipynb` | Visual EDA of lesion distribution and features |
| `03_prepocessing_and_training.ipynb` | Metadata model training and evaluation |
| `04_MODELING.ipynb` | CNN, EfficientNet, and multimodal model building |
| `model_metrics.md` | 📈 Final model evaluation summary |
| `teledermatology_cnn_model.keras` | Final trained CNN model file |
| `README.md` | 📘 This file |

## 📌 Recommendations

1. Deploy model in clinical support setting for triage prioritization
2. Gather more rare lesion samples to boost minority class generalization
3. Extend multimodal pipeline with patient history and time-series data

## 🙋‍♂️ Author

**Manuel Ramirez Chimarro**  
[LinkedIn](https://www.linkedin.com/in/manuelramirezchimarro/) 

---

> Project completed as part of the Springboard Data Science Career Track, Capstone Three.





#  Model Metrics: Skin Lesion Classification (Capstone 3)

##  Final Model Overview

* **Architecture**: Multimodal EfficientNetB3 + Metadata (Dense Layer)
* **Input Modalities**:

  * **Images** (64x64 RGB Lesion Images)
  * **Metadata**: Age, Sex (encoded), Localization (encoded)
* **Loss Function**: Focal Loss (γ = 2.0, α = 1.0)
* **Optimizer**: Adam (Learning Rate = 1e-4)
* **Data Augmentation**: Rotation, Flip, Zoom, Brightness adjustments
* **Train/Validation Split**: 80/20 (Stratified)

---

## 📈 Performance Summary

| Class                | Precision | Recall | F1-Score | Support  |
| -------------------- | --------- | ------ | -------- | -------- |
| akiec                | 0.49      | 0.44   | 0.46     | 220      |
| bcc                  | 0.82      | 0.94   | 0.87     | 1341     |
| bkl                  | 0.36      | 0.17   | 0.24     | 23       |
| df                   | 0.32      | 0.25   | 0.28     | 223      |
| mel                  | 0.64      | 0.25   | 0.36     | 28       |
| nv                   | 0.30      | 0.17   | 0.22     | 103      |
| vasc                 | 0.30      | 0.09   | 0.14     | 65       |
| **Overall Accuracy** |           |        | **0.78** | **2003** |

---

##  Model Highlights

* **Focal Loss** significantly improved learning on minority classes.
* **Data Augmentation** helped regularize training and reduce overfitting.
* **Multimodal Integration** of metadata with image features led to more robust predictions.

---

##  Future Improvements

* Tune focal loss `alpha` and `gamma` values per class frequency
* Use **EfficientNetB4** or **fine-tune top layers**
* Add **skin tone normalization** or lesion boundary detection

---
