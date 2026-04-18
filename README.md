# Super-Resolution GAN for Retinal OCT Image Classification


This project aims to enhance binary classification of retinal OCT images by leveraging a Super-Resolution GAN (SRGAN) to generate high-resolution images from low-resolution inputs.

--- 

## Project Objectives

The primary goals of this project are:

1. Develop a high-performing baseline classifier
2. Implement a Super-Resolution GAN to enhance image quality
3. Use generated images to train a second classifier
4. Compare the performance of both models using different metrics such as F1, Accuracy, AUC


---

## Authors
- **Christian Bammann** – Data preprocessing, model development, experimentation, and documentation

---

## Dataset
- Retinal OCT Images (Srinivasan)
- Classes: **DME** and **DRUSEN**
- Dataset split: **70% Train** / **30% Test**

---

## Project Overview

This project consists of two main components:

1. **Model A - Baseline Model**  
   A binary classifier trained on OCT images resized to **128×128**

2. **Model B - SRGAN Model**  
   A classifier intended to be trained on **SRGAN-generated high-resolution images**

---

## Data Preprocessing

- Images resized to **128×128** for classification
- Low-resolution inputs generated at **32×32** for SRGAN training
- Normalization applied using:
  ```python
  rescale = 1./255
