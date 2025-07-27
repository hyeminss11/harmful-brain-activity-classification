# Harmful Brain Activity Classification

**Multi-class EEG Classification using Deep Learning**  
[🔗 Kaggle Competition](https://www.kaggle.com/competitions/hms-harmful-brain-activity-classification)  
📌 Developed as part of an official university team project (Team GM2)

## 🧠 Overview
This project aims to classify harmful brain activity patterns (Seizure, LPD, GPD, LRDA, GRDA) using EEG data. We employed scalogram-based visual representations and trained multiple deep learning models to solve a multi-class classification problem.

## 👥 Team Members
- Team GM2 (5 members)  
- **My role**: Deep learning model implementation & analysis using **ResNet18**  
  → Suggested and implemented **Grad-CAM** for model interpretability
  
## 📂 Dataset
- HMS - Harmful Brain Activity Classification (Kaggle)
- EEG recordings in 50-second segments
- Label: One of five harmful activity types (or “Others” excluded)

## ⚙️ Preprocessing
- Montage transformation of raw EEG signals
- Applied bandpass filtering for better results
- Continuous Wavelet Transform (CWT) to generate scalograms
- Resized to 224x224 for CNN input

## 🧪 Models
- CNN baseline
- **ResNet18** (my part)
- EfficientNet
- Vision Transformer (ViT)
- Ensemble of the above three

**📈 Result:**  
- Ensemble Accuracy: ~81%  
- ResNet18 Accuracy: ~75%

## 🛠 Tech Stack
- Python, PyTorch, scikit-learn, Matplotlib

## 📷 Grad-CAM Visualization (my contribution)
![Grad-CAM](./assets/images/gradcam.png)
