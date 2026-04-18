# Super-Resolution GAN for Retinal OCT Image Classification

This project explores the use of a Super-Resolution GAN (SRGAN) to enhance retinal OCT images and evaluate its impact on binary classification performance between **DME** and **DRUSEN**.

---

## Authors
- **Christian Bammann** – Data preprocessing, model development, experimentation, and documentation

---

## Dataset
- Retinal OCT Images (Srinivasan)
- Classes used: **DME** and **DRUSEN**
- Dataset split:
  - **70% Training**
  - **30% Testing**

---

## Project Overview

This project consists of two main components:

1. **Model A (Baseline Classifier)**  
   A binary classifier trained on real OCT images resized to **128×128**

2. **Model B (GAN-Augmented Classifier)**  
   A classifier intended to be trained on **SRGAN-generated high-resolution images**

---

## Data Preprocessing

- Images resized to **128×128** for classification
- Low-resolution inputs generated at **32×32** for SRGAN training
- Normalization applied using:
  ```python
  rescale = 1./255
