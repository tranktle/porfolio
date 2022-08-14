---
layout: post
title: MRI classification with Pytorch - 98% Accuracy
feature-img: "assets/img/feature-img/mri_image.png"
thumbnail: "assets/img/feature-img/mri_image.png"
tags: [cnn, image classification, transfer learning]
---

This project is about using Pytorch for 2D MRI image classification using transfer learning with Resnet34 with a testing accuracy is 98%.

The images are downloaded from [Kaggle](https://www.kaggle.com/datasets/tourist55/alzheimers-dataset-4-class-of-images). These images will be classified into four categories, including 

NOD: Non Demented, \
VMD: Very Mild Demented, \
MID: Mild Demented, \
MOD: Moderate Demented. \

Index | Description | Jupiter notebook| Content | data | 
------------- | ------------- |---------------|------------|--------------|
1 | Val_accuracy: 0.98 <br> Testing accuracy: 0.68 😢 | [01_Resrnet34.ipynb](https://github.com/tranktle/2022_mri_classification/blob/main/01-Resnet34.ipynb) |Download data <br> split to train, val, test <br> Train with Resnet34 <br> Testing evaluation <br> Reasoning | org_day|
2 | Val_accuracy: 0.99 <br> Testing accuracy: 0.98 😃 <br> Is this approach ok? 🤔| [02_Resnet34.ipynb](https://github.com/tranktle/2022_mri_classification/blob/main/02-Resnet34.ipynb)| Combine data<br> Split data <br> Train model<br> Evaluate the model| allnew|
