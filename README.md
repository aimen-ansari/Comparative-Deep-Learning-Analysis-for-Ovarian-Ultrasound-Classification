# Comparative Deep Learning Analysis for Ovarian Ultrasound Classification

This project presents a comparative deep learning study for **multiclass ovarian ultrasound image classification**. The objective is to classify ovarian ultrasound images into five clinical categories using baseline neural networks, custom CNN models, classic CNN architecture, transfer learning models, a hybrid CNN-Transformer model, and Grad-CAM explainability.

The project is designed as a research-oriented medical imaging workflow and includes model training, evaluation, comparison, visualization, and explainability.

---

## Project Overview

Ovarian ultrasound imaging is widely used in gynecology for evaluating ovarian health and identifying cystic or follicular abnormalities. Manual interpretation may be time-consuming and can vary depending on clinical expertise. Deep learning can support automated image-based classification by learning visual patterns from ultrasound scans.

This study compares multiple deep learning architectures to evaluate their performance on a five-class ovarian ultrasound dataset.

---

## Dataset

The dataset contains ovarian ultrasound images organized into five classes:

| Class | Description |
|---|---|
| `complex_cyst` | Complex ovarian cyst |
| `dominant_follicle` | Dominant follicle |
| `healthy` | Normal/healthy ovary |
| `poly_cyst` | Polycystic ovary |
| `simple_cyst` | Simple ovarian cyst |

Dataset summary:

| Item | Details |
|---|---|
| Total Images | 6,876 images |
| Number of Classes | 5 |
| Task Type | Multiclass Image Classification |
| Image Type | Ovarian Ultrasound Images |
| Split Strategy | Stratified split |
| Train / Validation / Test | 70% / 15% / 15% |

---

## Models Implemented

The following models were trained and compared:

| Model | Category |
|---|---|
| ANN Baseline | Fully connected baseline model |
| CNN Baseline | Custom CNN |
| CNN Deeper | Deeper custom CNN |
| LeNet | Classic CNN architecture |
| VGG16 | Transfer learning CNN |
| ResNet50 | Transfer learning CNN |
| EfficientNet-B3 | Transfer learning CNN |
| Hybrid EfficientNet-B3 + Transformer | Hybrid CNN-Transformer architecture |

---

## Methodology

The overall workflow includes:

1. Dataset loading and class analysis  
2. Stratified train-validation-test splitting  
3. Image preprocessing and augmentation  
4. Model training using PyTorch  
5. Evaluation using accuracy, precision, recall, F1-score, and confusion matrix  
6. Model complexity comparison using total and trainable parameters  
7. Grad-CAM explainability for visual interpretation  
8. Final comparative analysis of all models  

---

## Experimental Setup

| Setting | Value |
|---|---|
| Framework | PyTorch |
| Platform | Google Colab |
| Image Size | 224 × 224 for CNN/transfer learning models |
| ANN Image Size | 128 × 128 |
| Batch Size | 32 |
| Optimizer | Adam |
| Loss Function | CrossEntropyLoss |
| Evaluation Metrics | Accuracy, Precision, Recall, F1-score, Confusion Matrix |
| Explainability Method | Grad-CAM |

---

## Final Model Comparison

| Rank | Model | Test Accuracy | Precision | Recall | F1-score | Total Parameters |
|---:|---|---:|---:|---:|---:|---:|
| 1 | VGG16 | 100.00% | 100.00% | 100.00% | 100.00% | 134,281,029 |
| 2 | CNN Deeper | 99.90% | 99.90% | 99.90% | 99.90% | 6,682,789 |
| 3 | EfficientNet-B3 | 99.81% | 99.81% | 99.81% | 99.81% | 10,703,917 |
| 4 | Hybrid EfficientNet-B3 + Transformer | 99.61% | 99.61% | 99.61% | 99.61% | 12,177,965 |
| 5 | CNN Baseline | 96.32% | 96.44% | 96.32% | 96.31% | 1,733,125 |
| 6 | ResNet50 | 95.45% | 95.55% | 95.45% | 95.43% | 23,518,277 |
| 7 | ANN Baseline | 90.50% | 90.39% | 90.50% | 90.44% | 25,331,205 |
| 8 | LeNet | 81.40% | 81.55% | 81.40% | 80.40% | 61,581 |

---

## Key Findings

- VGG16 achieved the highest test accuracy of **100.00%**.
- CNN Deeper achieved **99.90% accuracy** with far fewer parameters than VGG16.
- EfficientNet-B3 achieved **99.81% accuracy** and provided a strong balance between performance and parameter efficiency.
- The Hybrid EfficientNet-B3 + Transformer model achieved **99.61% accuracy** in only 5 epochs.
- LeNet achieved the lowest performance due to its shallow architecture.
- Most classification errors occurred between `complex_cyst` and `simple_cyst`, which are visually similar ultrasound categories.

---

## Grad-CAM Explainability

Grad-CAM was applied to the trained EfficientNet-B3 model to visualize the regions that contributed most to predictions.

The Grad-CAM results showed that the model generally focused on meaningful ovarian ultrasound regions, including cystic structures, follicular patterns, and ovarian tissue regions.

This improves interpretability and provides visual support for model predictions.

---


##Single Image Prediction

The project also supports single-image prediction. A new ovarian ultrasound image can be uploaded, and the trained EfficientNet-B3 model predicts the class with confidence score.

Example output:
Predicted Class: simple_cyst
Confidence: 98.45%

Important: Prediction confidence for one image is not the same as model accuracy. Accuracy is calculated on a labeled test set.


## Repository Structure

```text
Comparative-Deep-Learning-Analysis-for-Ovarian-Ultrasound-Classification/
│
├── Ovarian_US_Dataset.ipynb
├── README.md
│
├── results/
│   ├── model comparison results
│   ├── classification reports
│   └── training histories
│
├── figures/
│   ├── confusion matrices
│   ├── training curves
│   ├── comparison graphs
│   └── Grad-CAM visualizations
│
└── models/
    ├── trained model checkpoints
    └── best model weights

