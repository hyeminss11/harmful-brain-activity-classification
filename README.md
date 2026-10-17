# harmful-brain-activity-classification
**Interpretable EEG-based Harmful Brain Activity Classification using Deep Learning**

## Overview
This repository contains the code and results for a university team project (Team GM2, 5 members; supervisor: Dr. Georgios Moulantzikos). EEG is central to diagnosing neurological conditions such as seizures and brain injury, but reading it is slow, costly and subjective: agreement between expert clinicians is often low, and visually similar abnormal patterns are easy to confuse. The project builds deep-learning models that classify five harmful EEG patterns (Seizure, LPD, GPD, LRDA, GRDA) and uses explainability methods to show why each prediction was made, so that the output can serve as a second opinion a clinician can check.

## Research Questions
1. **Classification**: Can CNN-based models trained on EEG scalograms reliably distinguish five harmful brain activity patterns?
2. **Model Choice**: How do different architectures (2D CNN, ResNet18, EfficientNet, ViT) and their ensemble compare?
3. **Interpretability**: Do the models attend to clinically meaningful signals rather than background noise?

## Key Findings
- **Depth matters**: ResNet18 reached 74.7% accuracy, about 17 percentage points above a plain 2D CNN baseline (57.9%), which was discontinued due to poor generalisation. The largest gain was on LRDA, where recall rose from 8% to 53%
- **Ensembling helps on hard classes**: Some LRDA samples were misclassified as Seizure or LPD by single models; a weighted ensemble mitigated this and lifted overall accuracy to ~81%
- **The model looks at the right signals**: Grad-CAM showed ResNet18 attends to clinically meaningful EEG activity rather than background noise
- **Explainability does not transfer to every architecture**: Grad-CAM produced uninterpretable heatmaps for ViT, so attention-based methods are needed for transformer models

## Dataset
This project uses the EEG data from the [HMS - Harmful Brain Activity Classification](https://www.kaggle.com/competitions/hms-harmful-brain-activity-classification) Kaggle competition.

- 50-second EEG segments, each labelled as one of five harmful activity classes
- The "Other" class was excluded

> **Source**:
> HMS - Harmful Brain Activity Classification, Kaggle competition hosted by Harvard Medical School, 2024.
> [https://www.kaggle.com/competitions/hms-harmful-brain-activity-classification](https://www.kaggle.com/competitions/hms-harmful-brain-activity-classification)

## Models
Four architectures were compared, and three were combined into a weighted ensemble:

| Model | Description | Owner |
|-------|-------------|-------|
| **2D CNN** | Baseline (discontinued) | Me |
| **ResNet18** | Deeper CNN with residual connections, ImageNet-pretrained | Me |
| **EfficientNet** | Efficient CNN scaling | Team |
| **Vision Transformer (ViT)** | Attention-based model | Team |
| **Weighted Ensemble** | ResNet18 + EfficientNet + ViT | Team |

### Preprocessing
1. **Montage Transformation**: Re-referencing raw EEG channels
2. **Bandpass Filtering**: 0.5–40 Hz to isolate brain signals from noise
3. **Continuous Wavelet Transform (CWT)**: Converting signals into scalogram images
4. **Resizing**: 224 × 224 for CNN input

## Results Summary

### Classification Accuracy
| Model | Accuracy |
|-------|----------|
| 2D CNN (baseline) | 57.9% |
| ResNet18 | 74.7% |
| Weighted Ensemble | ~81% |

### Per-Class Recall (test set, 38 samples per class)
| Class | 2D CNN | ResNet18 |
|-------|--------|----------|
| Seizure | 68% | 71% |
| LPD | 76% | 89% |
| GPD | 63% | 79% |
| LRDA | 8% | 53% |
| GRDA | 74% | 82% |

### Confusion Matrices
<p align="center">
  <img src="./assets/ResNet18_scalogram_bp_cm.png" alt="ResNet18 confusion matrix" width="400">
  <img src="./assets/2dCNN_scalogram_bp_cm.png" alt="2D CNN confusion matrix" width="400">
</p>

## Interpretability Analysis
**Grad-CAM (Gradient-weighted Class Activation Mapping)** was applied to ResNet18 to visualise which regions of the scalogram drove each prediction:
- Strong sensitivity on **LPD** (89% recall) and **GRDA** (82%), where the model captured distinct patterns within the scalograms; **LRDA** remained the hardest class (53%), most often confused with Seizure and LPD
- Heatmaps concentrated on **clinically meaningful EEG activity** rather than background noise
- Grad-CAM does not support ViT well; future work could use SHAP, Attention Rollout or LRP for transformer explainability

<p align="center">
  <img src="./assets/gradcam.png" alt="Grad-CAM" width="400">
</p>

## My Role
- Implemented and trained the 2D CNN baseline and ResNet18
- Proposed and applied Grad-CAM for model interpretability
- Collaborated on model evaluation and ablation studies

## Reproducibility
Notebooks for the 2D CNN baseline and ResNet18 (training, evaluation and Grad-CAM) are in [`models/`](models/). Figures are in [`assets/`](assets/).

Tech stack: Python, PyTorch, scikit-learn, Matplotlib, Seaborn
