# UltraCamNet: Explainable AI for Early Cancer Detection in Digital Histopathology

This repository contains the implementation of **UltraCamNet-V5**, a convolutional neural network architecture developed for robust and accurate detection of metastatic tissue in histopathology images (PatchCamelyon dataset). This work has been accepted to the **icAMC 2026 conference**.

## Overview

Detecting fine-grained textures on glands is exceptionally challenging. Deep learning models like MobileNet variants have historically faced a hard time, often resulting in relatively low accuracies (e.g., typically around 48–50%). EfficientNet models demonstrate a clear enhancement because of compound scaling, but still face limitations.

**UltraCamNet** is specifically engineered to overcome these limitations. With the integration of **SE-Residual Blocks**, the architecture leverages channel-level recalibration of features combined with depthwise separable convolutions to maximize representational capacity without increasing computational burdens.

## Superior Accuracy

The success of the UltraCamNet architecture is demonstrated by its significant performance enhancement over established baselines, achieving an absolute improvement of 0.14 (a ~20% relative improvement) over the strongest EfficientNet baseline, reaching a highest accuracy of **0.8733**.

### Table 1: Accuracy Comparison of Baseline CNN vs. UltraCamNet

| Model | Accuracy |
| --- | --- |
| MobileNetV2 | 0.4866 |
| MobileNetV3 | 0.5004 |
| EfficientNet-B0 | 0.6823 |
| EfficientNet-B3 | 0.7033 |
| **UltraCamNet** | **0.8733** |

## Explainable AI (Grad-CAM Visualizations)

Explainability is crucial in automated medical diagnostics. We integrate **Grad-CAM visualization** to highlight the spatial areas that have the most significant impact on model predictions. These localized areas:
- Prove the model's interpretability by identifying precisely where the network pays attention when classifying types of tumors.
- Prevent spurious classification by revealing any instances where the model concentrates on irrelevant visual artifacts.
- Provide transparent reasoning to inform future clinical trust and further automated histopathology analysis.

## Repository Contents
- `UltraCamNet_Cancer_Detection.ipynb`: A comprehensive Jupyter Notebook containing the data pipeline, the UltraCamNet architectural code, the training loop with mixed precision support, evaluation scripts, and the model interpretability implementation (Grad-CAM grids) using `tf-keras-vis`.

### Dependencies
- TensorFlow 2.x
- Keras
- tf-keras-vis (for Grad-CAM visualization)
- NumPy, OpenCV, Matplotlib, h5py

## Acknowledgments
We are thrilled to share that this research has been successfully peer-reviewed and **accepted to the ICAMC 2026 conference**.
