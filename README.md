# Automated Diabetic Retinopathy Detection Using Capsule Networks with Explainability

[![Published](https://img.shields.io/badge/Published-IJSREM%20Vol.10%20Issue%2004%20April%202026-blue)](https://ijsrem.com)
[![DOI](https://img.shields.io/badge/DOI-10.55041%2FIJSREM59866-green)](https://doi.org/10.55041/IJSREM59866)
[![Impact Factor](https://img.shields.io/badge/Impact%20Factor-8.659-orange)](https://ijsrem.com)
[![Accuracy](https://img.shields.io/badge/Accuracy-92%25-brightgreen)]()
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)]()
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)]()

> A published research project implementing Capsule Networks (CapsNet) integrated with Explainable AI (Grad-CAM) for automated detection and classification of Diabetic Retinopathy from retinal fundus images — achieving **92% accuracy** and outperforming CNN-based baselines.

---

## Table of Contents
- [Overview](#overview)
- [Key Results](#key-results)
- [Architecture](#architecture)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Publication](#publication)
- [License](#license)

---

## Overview

Diabetic Retinopathy (DR) is a leading cause of preventable blindness worldwide. Early detection is critical but challenging. This project addresses this by:

- Using **Capsule Networks (CapsNet)** to preserve spatial hierarchies in retinal images — crucial for detecting microaneurysms
- Integrating **Grad-CAM (Explainable AI)** to generate visual heatmaps, enabling clinicians to trust and validate AI predictions
- Achieving superior performance over traditional CNNs with only **4.3M parameters** vs ResNet-50's 25.6M

### Problem Statement
Conventional CNNs fail to preserve spatial relationships between retinal features and lack interpretability — making clinical adoption difficult.

### Solution
CapsNet + Grad-CAM framework that is:
- **Accurate**: 92% classification accuracy across 5 DR severity levels
- **Explainable**: Visual heatmaps highlighting pathological regions
- **Efficient**: Lightweight model (4.3M parameters)
- **Clinically relevant**: Validated on APTOS 2019 dataset

---

## Key Results

| Metric | Value |
|--------|-------|
| Accuracy | **92%** |
| Precision | **89%** |
| Recall | **88%** |
| F1-Score | **88.5%** |

### Comparative Analysis

| Model | Accuracy | Precision | Recall | F1-Score | Parameters (M) |
|-------|----------|-----------|--------|----------|----------------|
| **CapsNet + XAI (Ours)** | **92.8%** | **91.5%** | **93.2%** | **92.3%** | **4.3** |
| CNN ResNet-50 | 89.5% | 87.8% | 88.9% | 88.3% | 25.6 |
| CNN VGG-16 | 86.7% | 85.4% | 86.2% | 85.8% | 138 |
| CNN Inception-V3 | 88.9% | 87.6% | 88.2% | 87.9% | 23.9 |
| Traditional SVM | 76.5% | 74.3% | 75.8% | 75.0% | - |

---

## Architecture

```
Input Retinal Image (128x128x3)
       |
 Convolutional Layer (32 filters, 9x9 kernel, ReLU)
       |
 Primary Capsules Layer (8 channels, 16-dim vectors, Squash)
       |
 Dynamic Routing Algorithm
       |
 Digit Capsules Layer (5 capsules x 16-dim — one per DR severity)
       |
 Length Layer (Vector norm = class probability)
       |
 DR Severity Classification (0=No DR, 1=Mild, 2=Moderate, 3=Severe, 4=Proliferative)
       |
 Grad-CAM XAI Module (Heatmap overlay on retinal image)
```

### Key Components
- **Primary Capsules**: Encode spatial position and feature presence
- **Dynamic Routing**: Iteratively determines capsule contribution weights
- **Squash Activation**: Normalizes capsule vector lengths to [0,1]
- **Grad-CAM**: Gradient-weighted class activation mapping for explainability

---

## Dataset

**APTOS 2019 Blindness Detection Dataset** — Kaggle
- Source: Asia Pacific Tele-Ophthalmology Society (APTOS)
- Classes: 5 DR severity levels (0–4)
- High-resolution retinal fundus images
- Link: https://www.kaggle.com/competitions/aptos2019-blindness-detection

### Preprocessing Pipeline
1. Image resizing to **128x128 pixels**
2. BGR to RGB color space conversion
3. Normalization (ImageNet mean/std)
4. Data Augmentation:
   - Horizontal flipping (p=0.5)
   - Random rotation (±20°)
   - Brightness/contrast adjustments (±0.2)
   - Gaussian blur and noise
5. Class imbalance handling via oversampling
6. 80/20 stratified train/validation split

---

## Installation

```bash
git clone https://github.com/MVVasudevreddy/diabetic-retinopathy-capsnet-xai.git
cd diabetic-retinopathy-capsnet-xai
pip install -r requirements.txt
```

### Requirements
```
tensorflow>=2.8
numpy
pandas
opencv-python
albumentations
matplotlib
scikit-learn
tqdm
```

---

## Usage

### Run on Google Colab (Recommended)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/18jjm6KwuVkep8pGVeaK2P21yaxYubDfr)

### Training
```python
# Set batch size and epochs
batch_size = 16
epochs = 50

# Optimizer: Adam (lr=0.0005)
# Loss: Margin Loss (CapsNet-specific)
# Callbacks: EarlyStopping, ReduceLROnPlateau, ModelCheckpoint
```

---

## Results

### Grad-CAM Explainability
The Grad-CAM module generates heatmaps overlaid on retinal images, highlighting:
- **DR Positive cases**: Microaneurysms and lesion regions highlighted in red/yellow
- **No DR cases**: Minimal or no highlighted regions

This bridges the gap between AI predictions and clinical interpretability, enabling ophthalmologists to validate and trust model decisions.

### Training Behavior
- **Loss**: Steadily decreasing — confirmed successful convergence
- **Accuracy**: Increasing trend — model learned efficiently
- **Overfitting**: Minimal — small train/validation divergence

---

## Publication

**Title**: Automated Diabetic Retinopathy Detection Using Capsule Networks with Explainability  
**Journal**: International Journal of Scientific Research in Engineering & Management (IJSREM)  
**Volume**: 10 | **Issue**: 04 | **Month**: April 2026  
**ISSN**: 2582-3930  
**Impact Factor**: 8.659  
**DOI**: [10.55041/IJSREM59866](https://doi.org/10.55041/IJSREM59866)  
**Indexing**: Open Access, Peer-Reviewed, Indexed in Major Databases  

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat&logo=keras&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-27338e?style=flat&logo=OpenCV&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-013243?style=flat&logo=numpy&logoColor=white)
![Google Colab](https://img.shields.io/badge/Colab-F9AB00?style=flat&logo=googlecolab&color=525252)

---

## Domain
Image Classification | Medical AI | Deep Learning | Explainable AI | Computer Vision

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

*B.Tech Major Project — Department of Computer Science and Engineering, BIHER, Chennai — May 2026*
