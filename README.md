# Breast Histopathology Classification

A notebook-based comparison of simple deep learning models for benign vs. malignant breast histopathology image classification.

The analysis uses FastAI/PyTorch to compare:

- a shallow fully connected neural network
- a custom convolutional neural network
- VGG16 transfer learning

The notebook includes basic preprocessing, augmentation, oversampling for class imbalance, confusion matrices, ROC curves, and threshold-based metrics. It also includes experiments on 100x magnification images.

## Files

```text
.
|-- README.md
`-- breast_histopathology_classification.ipynb
```

## Notes

- Image data is not included in this repository.
- The notebook was developed in Google Colab and uses Google Drive paths.
- The dataset layout expects separate benign and malignant image folders.
