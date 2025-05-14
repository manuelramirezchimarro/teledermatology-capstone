# teledermatology-capstone

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


