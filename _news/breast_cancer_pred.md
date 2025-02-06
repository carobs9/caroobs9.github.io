---
layout: post
title: breast cancer predIction
date: 2024-05-25 21:01:00
description: breast cancer prediction
tags: medical-applications
categories: machine-learning
related_posts: false

---

# Breast Cancer Prediction  

I performed a binary prediction task using the famous [Wisconsin Breast Cancer Dataset](https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic9).


## Exploratory Data Analysis and Feature Selection

The dataset contains up to 30 features, computed from a digitized image of a fine needle aspirate (FNA) of a breast mass. They describe characteristics of the cell nuclei present in the image. Each row is labelled as malign (M) or benign (B) under the 'diagnosis' column, indicating whether the observation was diagnosed as cancer or not. 

I started the classification task by performing an exploratory data analysis to understand the features and select the most explanatory ones to train a simple neural network. 

To select the features, I explore different techniques: correlation, random forest classification or PCA (Principal COmponent Analysis). According to the results, only around 11 features explain the data distribution.

In the following Jupyter Notebook I go over a set of EDA and feature selection methods, just to understand the data better and consider reducing the number of features:

<iframe src="{{ site.baseurl }}/assets/html/data_eda.html" width="150%" height="700px"></iframe>

## Building Neural Network Using Keras

I standardized the feature data and, as a first test that actually gives great results, I built a neural network with Keras, where the input are the 30 standardized initial features. The data is split into train (75%) and test (25%) sets.

As specified in the Jupyter Notebook, the model contains:

    - an input shape of 30.
    - 7 layers.
    - 8 neurons per hidden layer.
    - weight initializer: he normal.
    - regularization: L2 and dropout.
    - a final sigmoid activation to keep the outputs as a probability between 0 and 1.
    - the probablities are turned in to classes (0 or 1) using a 0.5 threshold. This threshold might change due to different applications. Considering that I am dealing with potential cancer cases, tuning the threshold so it favors class 1 predictions (cancer) could be beneficial.

The model is trained with the following parameters:

    - binary cross entropy loss.
    - adam optimizer at 0.001 learning rate.
    - accuracy as the main metric to optimize.
    - a batch size of 64.
    - the model gives best results when trained during 300 epochs. That means that the model learns to classify between benign (0) and malign (1) after 300 epochs.

As key notes:
    - the test loss decreases from 0.7472 (first epoch) to 0.0668 (last epoch).
    - the test set accuracy increases during training from 0.608 (first epoch) to 0.986 (last epoch).
    - the test loss is lower than the training loss overall, propably because of the use of dropout regularization in the training phase. This essentially makes the model more robust during test than during training.


<iframe src="{{ site.baseurl }}/assets/html/breast_cancer_prediction.html" width="150%" height="700px"></iframe>
