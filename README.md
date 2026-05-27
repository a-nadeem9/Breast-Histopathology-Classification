# Breast Histopathology Classification

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![FastAI](https://img.shields.io/badge/FastAI-v2-orange)
![PyTorch](https://img.shields.io/badge/PyTorch-1.x-red)
![Notebook](https://img.shields.io/badge/Jupyter-Notebook-lightgrey)

This repository contains a notebook-based deep learning analysis for classifying breast histopathology images as benign or malignant. The project compares a shallow neural network, a custom convolutional neural network, and VGG16 transfer learning under different preprocessing and training setups.

The analysis uses breast cancer histopathology images organized by class label and magnification level, including 100x images. The notebook workflow is written for Google Colab and FastAI/PyTorch.

## Project Scope

The notebook explores:

- benign vs. malignant image classification
- baseline training without augmentation
- image augmentation with FastAI transforms
- oversampling to reduce class imbalance
- comparison of shallow, custom CNN, and transfer learning models
- ROC curves, confusion matrices, precision, recall, specificity, and accuracy
- effect of 100x magnification images on model performance

## Models Compared

| Model | Description |
| --- | --- |
| `SimpleNet` | Shallow fully connected neural network used as a baseline |
| `CustomCNN` | Four-block convolutional neural network with batch normalization and pooling |
| `VGG16` | Pretrained VGG16 model fine-tuned for binary histopathology classification |

## Workflow

1. Load histopathology images from Google Drive.
2. Build FastAI `DataBlock` pipelines for benign/malignant labels.
3. Train baseline models.
4. Apply augmentation and class balancing.
5. Re-train models under the updated data setup.
6. Evaluate models using confusion matrices, ROC curves, and threshold-based metrics.
7. Repeat selected experiments on 100x magnification images.

## Repository Contents

```text
.
|-- README.md
`-- breast_histopathology_classification.ipynb
```

## Dataset

The notebook uses a local Google Drive dataset path and does not include image data in this repository. The folder structure is expected to separate images by class label, for example:

```text
Breast_Cancer_Dataset/
|-- benign/
`-- malignant/
```

The class counts and magnification setup are consistent with the BreaKHis breast histopathology dataset, which contains benign and malignant breast tumor images across multiple magnification levels, including 40x, 100x, 200x, and 400x.

BreaKHis dataset reference: https://web.inf.ufpr.br/vri/databases/breast-cancer-histopathological-database-breakhis/

## Notes

- The notebook was developed in Google Colab and uses Google Drive paths.
- Dataset files are not committed to this repository.
- Results may vary because random train/validation splits and augmentation are used.
