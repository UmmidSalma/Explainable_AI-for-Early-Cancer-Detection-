# UltraCamNet: Explainable AI for Early Cancer Detection in Digital Histopathology

![Conference](https://img.shields.io/badge/ICRAAI_2026-Accepted-brightgreen)
![Dataset](https://img.shields.io/badge/Dataset-PatchCamelyon-blue)
![Framework](https://img.shields.io/badge/Framework-TensorFlow_2.x-orange)


This repository contains the implementation of **UltraCamNet-V5**, a convolutional neural network architecture developed for robust and accurate detection of metastatic tissue in histopathology images using the PatchCamelyon (PCam) dataset. This work has been peer-reviewed and **accepted to the ICRAAI 2026 conference**.

---

## Overview

Automated detection of metastatic tissue in histopathology patches is a challenging computer vision problem. Lightweight models such as MobileNet variants have historically underperformed on this task, often achieving accuracies in the range of 48–50%. EfficientNet models show clear improvements through compound scaling, but still face limitations in fine-grained feature discrimination.

**UltraCamNet** is specifically engineered to overcome these limitations. By integrating **SE-Residual Blocks (Squeeze-and-Excitation)**, the architecture leverages channel-level recalibration combined with depthwise separable convolutions to maximize representational capacity without increasing computational burden. Additional techniques including **CutMix augmentation**, **Test-Time Augmentation (TTA)**, learning rate scheduling, and regularization ensure stable and effective optimization.

---

## Dataset

**PatchCamelyon (PCam)**
- Source: Kaggle (public histopathology benchmark)
- Total images: **327,680** patches (96×96 pixels)
- Binary classification: **Metastatic** vs **Non-metastatic** lymph node tissue
- Approximate size: ~8 GB
- Split:
  - Training: 262,144 images
  - Validation: 32,768 images
  - Testing: 32,768 images

---

## Results

UltraCamNet achieves significant performance improvement over all evaluated baselines:

### Table 1: Accuracy Comparison — Baseline CNNs vs. UltraCamNet

| Model | Accuracy |
|---|---|
| MobileNetV2 | 0.4866 |
| MobileNetV3 | 0.5004 |
| EfficientNet-B0 | 0.6823 |
| EfficientNet-B3 | 0.7033 |
| **UltraCamNet (Ours)** | **0.8733** |

### Key Metrics

| Metric | Value |
|---|---|
| Test Accuracy | **87.33%** |
| Validation AUC | **0.9660** |

UltraCamNet achieves an absolute improvement of **+0.14** (~20% relative improvement) over the strongest EfficientNet baseline, while maintaining a lightweight architecture suitable for resource-constrained deployment.

---

## Explainable AI — Grad-CAM Visualizations

Interpretability is critical in clinical and medical AI systems. UltraCamNet integrates **Grad-CAM (Gradient-weighted Class Activation Mapping)** to highlight spatial regions most influential to model predictions.

Grad-CAM visualizations serve to:
- Confirm the model attends to biologically relevant tissue regions during classification
- Detect and prevent spurious correlations or attention to visual artifacts
- Provide transparent, human-interpretable reasoning to support clinical trust
- Facilitate future research in scalable computational pathology

---
## System Architecture

![UltraCamNet Architecture](architecture.png)
*End-to-end pipeline: data loading, model training, callbacks, and Grad-CAM evaluation.*

---
## Architecture Highlights

- **SE-Residual Blocks** — Channel-wise feature recalibration for improved representational power
- **Depthwise Separable Convolutions** — Lightweight design without sacrificing depth
- **CutMix Augmentation** — Improves generalization by mixing training patches
- **Test-Time Augmentation (TTA)** — Boosts inference robustness
- **Mixed Precision Training** — Faster training with reduced memory footprint
- **Learning Rate Scheduling + Regularization** — Stable convergence and reduced overfitting

---

## Repository Contents

```
├── UltraCamNet_Cancer_Detection.ipynb   # Full pipeline: data loading, model architecture,
                                          # training, evaluation, and Grad-CAM visualization
└── README.md
```

### Running the Notebook

Open directly in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/01fe24bcs407-hash/UltraCamNet/blob/main/UltraCamNet_Cancer_Detection.ipynb)

> **Note:** The PCam dataset (~8 GB) can be downloaded via Kaggle API inside the notebook. Ensure your Kaggle credentials (`kaggle.json`) are configured.

---

## Dependencies

```
tensorflow>=2.x
keras
tf-keras-vis
numpy
opencv-python
matplotlib
h5py
```

Install via:
```bash
pip install tensorflow tf-keras-vis opencv-python matplotlib h5py
```


---

## Acknowledgments

This research was peer-reviewed and accepted to the **ICRAAI 2026 conference**. We thank the creators of the PatchCamelyon dataset and the open-source TensorFlow and tf-keras-vis communities.
