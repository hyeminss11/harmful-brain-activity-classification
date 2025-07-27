# Harmful Brain Activity Classification

**Multi-class EEG Classification using Deep Learning**  
🔗 [Kaggle Competition](https://www.kaggle.com/competitions/hms-harmful-brain-activity-classification)  
📌 Developed as part of an official university team project (Team GM2)

## 🧠 Overview
This project aims to classify harmful brain activity patterns (Seizure, LPD, GPD, LRDA, GRDA) using EEG data. We employed scalogram-based visual representations and trained multiple deep learning models to solve a multi-class classification problem.

## 👥 Team Members
- Team GM2 (5 members)  
- **My role**:  
  - Implemented **ResNet18** for EEG classification  
  - Proposed and applied **Grad-CAM** for explainability  
  - Also tested a base **2D CNN**, which was discarded due to low performance
  
## 📂 Dataset
- Source: [Kaggle - HMS Harmful Brain Activity Classification](https://www.kaggle.com/competitions/hms-harmful-brain-activity-classification)
- EEG segments: 50 seconds each
- Labels: Five harmful activity classes (excluding “Others”)

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

## 📈 Performance

| Model        | Accuracy |
|--------------|----------|
| ResNet18     | ~75%     |
| Ensemble     | ~81%     |

## 🛠 Tech Stack
- Python, PyTorch, scikit-learn, Matplotlib, Seaborn

## 📷 Grad-CAM Visualization
<p align="center">
  <img src="./assets/gradcam.png" alt="Grad-CAM" width="400">
</p>