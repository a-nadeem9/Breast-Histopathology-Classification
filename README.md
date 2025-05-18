# Breast Histopathology Classification

![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)  ![Fast.ai](https://img.shields.io/badge/fast.ai-v2.4-orange)  ![PyTorch](https://img.shields.io/badge/pytorch-v1.13-red)

## Project Overview

This repository presents a thorough comparative study on classifying breast cancer histopathology images. We benchmark three model families under varied data treatments:

- **SimpleNet**: A shallow fully connected network  
- **CustomCNN**: A tailored convolutional neural network with four blocks of Conv→BN→ReLU→Pool  
- **VGG16 Transfer Learning**: Fine-tuning a pretrained VGG16 on histopathology data

Each architecture is evaluated across data scenarios:

- **Baseline**: No augmentation, standard resizing  
- **Augmentation**: Random flips, rotations, lighting and contrast adjustments  
- **Augmentation + Oversampling**: Balancing classes by duplicating minority samples  
- **Native vs. 100× Magnification**: Testing on both resolutions to gauge the impact of image detail

## Key Features

- **Modular Data Pipeline**: Fast.ai DataBlock API for easy experimentation  
- **Architectural Diversity**: From MLP to deep CNN and transfer learning  
- **Balanced Training**: Oversampling combined with augmentation for robust models  
- **Comprehensive Metrics**: Accuracy, precision, recall, specificity, and ROC threshold analysis

## Results and Analysis

1. **Overall Best Performer**: The VGG16 fine-tuned on augmented + oversampled 100× images achieved an **accuracy of 94.2%**, outperforming both the custom CNN (89.7%) and SimpleNet (81.3%). The high-resolution data provided richer texture cues, enabling the pretrained features to generalize effectively.

2. **Impact of Augmentation**:  
   - For the CustomCNN, augmentation alone boosted accuracy from **81.4%** to **86.9%**, reduced false negatives by 22%, and improved recall from 78% to 84%.  
   - SimpleNet showed only a modest gain (3% absolute), highlighting its limited capacity to leverage synthetic diversity.

3. **Benefit of Oversampling**:  
   - Class balance corrections further lifted precision by **4–6%** across all models, with the most pronounced effect on recall for the shallow network (+8%).  
   - Confusion matrices indicate a significant drop in missed malignant samples when oversampling is applied (see notebook Confusion Matrix section).

4. **Resolution Effects**:  
   - Moving to 100× magnification images improved detection of micro-architecture patterns: the CustomCNN’s AUC increased from **0.91** (native) to **0.95** (100×).  
   - However, training time doubled, suggesting a trade-off between accuracy and compute costs.

5. **Threshold Optimization**:  
   - ROC threshold analysis revealed that setting the decision threshold at **0.42** (instead of 0.5) for VGG16 yields an optimal balance: **96% sensitivity** with **92% specificity**, suitable for clinical-minded deployments.


