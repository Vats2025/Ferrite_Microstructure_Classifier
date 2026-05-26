

---

```
# Ferrite Microstructure Classifier (FerriteScope)

A machine learning pipeline for automated classification of ferrite microstructures into three recrystallisation states — **Recrystallised**, **Partially Recrystallised**, and **Deformed** — using HOG features, ensemble ML models, and CNN-based Grad-CAM visualization.

---

## Project Overview

This project combines classical computer vision (HOG + CLAHE) with ensemble machine learning (RF + SVM + Gradient Boosting) to classify metallographic microstructure images. A parallel CNN provides Grad-CAM attention heatmaps for interpretability. A grain quantification pipeline extracts quantitative microstructural metrics (ASTM grain size, aspect ratio, circularity) alongside the classification output.

**Best accuracy: 90%+ (Ensemble: RF + SVM + GB)**

---

## Pipeline

```
Raw Image → CLAHE Preprocessing → HOG Feature Extraction
         → RF + SVM + GB Ensemble → Predicted Class + Confidence

         → CNN (parallel) → Grad-CAM Heatmap (visualization)
         → Adaptive Thresholding → Grain Segmentation → ASTM G, Aspect Ratio, Circularity
```

---

## Classes

| Label | Description |
|-------|-------------|
| Recrystallised | Equiaxed grains, uniform HOG, high circularity |
| Partially Recrystallised | Mixed grain morphology |
| Deformed | Elongated grains, peaked HOG, low circularity |

---

## Models Used

| Model | Input | Role |
|-------|-------|------|
| Random Forest | HOG features | Primary classifier |
| SVM (RBF kernel) | HOG features | Ensemble member |
| Gradient Boosting | HOG features | Ensemble member |
| Simple CNN (VGG-style) | Raw image | Grad-CAM visualization |

---

## Outputs

- Predicted class + confidence score
- Per-class probability bar chart
- Grad-CAM attention heatmap
- Grain segmentation map
- Histograms: grain diameter, aspect ratio, circularity
- Summary table: ASTM G, Rex fraction, GB density, morphology

---

## Tech Stack

Python, scikit-learn, OpenCV, scikit-image, TensorFlow/Keras, NumPy, Pandas, Matplotlib, Seaborn, joblib

---

## Dataset

300 synthetic Voronoi-tessellated microstructure images (100 per class), split into train/test sets.  
Files required:
- `ferrite_300_dataset.zip`
- `ferrite_dataset_300_COMPLETE.csv`

---

## Usage (Google Colab)

1. Upload `ferrite_300_dataset.zip` and `ferrite_dataset_300_COMPLETE.csv` when prompted
2. Run all cells in order
3. Models are saved as `ferrite_rf.pkl` and `ferrite_cnn.keras`
4. Upload your own microstructure image in the last cell for inference

---

## Author

**Khushboo Vats**  
B.Tech Metallurgical & Materials Engineering, VNIT Nagpur  
[LinkedIn](https://www.linkedin.com/in/khushboo-vats-593882249/) · [GitHub](https://github.com/Vats2025)
```

---

