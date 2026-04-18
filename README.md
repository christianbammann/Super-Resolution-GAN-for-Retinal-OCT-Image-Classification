# Super-Resolution GAN for Retinal OCT Image Classification


This project aims to enhance binary classification of retinal OCT images by leveraging a Super-Resolution GAN (SRGAN) to generate high-resolution images from low-resolution inputs.

--- 

## Objectives

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

1. **Model A - Baseline Classifier**  
   A binary classifier trained on OCT images resized to 128×128

2. **Model B - GAN Augmented Classifier**  
   A classifier intended to be trained on high resolution SRGAN-generated images

---

## Methods

### Model A – Baseline Classifier
- Architecture: Transfer learning CNN
- Input size: 128×128
- Final layer: `Dense(1, activation='sigmoid')`
- Loss: Binary Crossentropy
- Optimizer: Adam
- Training epochs: 30
- Batch size: 16

### SRGAN Model
- Task: 32×32 → 128×128 super-resolution
- Generator: CNN with upsampling layers
- Discriminator: CNN binary classifier
- Training epochs: 150

### Model B – GAN-Augmented Classifier
- Same architecture as Model A
- Trained on generated images from SRGAN

## Reproducibility

1. Load the OCT dataset and filter for DME and DRUSEN
2. Resize images to 128×128 for classification
3. Downscale images to 32×32 for SRGAN training
4. Train Model A using transfer learning
5. Train SRGAN on low-resolution images
6. Generate high-resolution images using the trained generator
7. Train Model B using generated images
8. Evaluate models using Accuracy, F1 Score, and AUC

---

## Results

### Model A

| Metric | Value |
|------|------|
| Accuracy | 0.935 |
| F1 Score | 0.924 |
| AUC | 0.978 |
- These results indicate strong classification performance and effective separation between the two classes.

### Model B
- The SRGAN model was trained to generate 128×128 images from 32×32 inputs.  
- Visual inspection of generated images shows improved resolution compared to the low-resolution inputs, though some artifacts are present due to limited training time.
- Model B was intended to be trained on GAN-generated images to evaluate whether synthetic data could match or improve classification performance. However, due to technical limitations, full evaluation was not completed.

### Model Comparison

Model A achieved strong performance using real OCT images.  

Model B was expected to perform slightly worse due to:
- Artifacts introduced by GAN-generated images  
- Differences between real and synthetic data distributions  

This behavior is consistent with typical GAN-based augmentation scenarios.

---

## Limitations

- SRGAN training was limited due to Google Colab GPU constraints
- Keras Lambda layer prevented reloading the trained generator
- As a result, Model B could not be fully evaluated

---

## Conclusion

- Model A achieved strong performance on real OCT images.
- Despite limitations, the overall pipeline demonstrates a complete GAN-based augmentation framework.
- SRGAN demonstrated the ability to generate higher-resolution images, but practical limitations prevented full evaluation of Model B.  
- This highlights both the potential and challenges of GAN-based data augmentation in medical imaging.
