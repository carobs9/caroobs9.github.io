---
layout: post
title: learning about gaussian mixture models
date: 2024-05-15 21:01:00
description: a post about gaussian mixture models
tags: formatting images
categories: generative models
related_posts: false
thumbnail: assets/img/gmms1.png

---

# Using Gaussian Mixture Models to Cluster and Generate skicit-learn Iris Dataset

## Gaussian Mixture Models

Gaussian Mixture Models (GMMs) combine multiple Gaussian distributions to model the data. 

Unlike other clustering methods like K Means, GMM does not only capture the means of the clusters, but also the covariances, allowing to form clusters with ellipsoidal shapes. 

## Fitting Gaussian Mixture Models: Expectation Maximization Algorithm

To fit the GMM, we use the Expectation Maximization (EM) algorithm, which maximizes the likelihood of the observed data. EM is similar to K Means but assigns data points to clusters with soft probabilities, rather than a hard assignment.

GMMs assume that any observed data set is a combination of several Gaussian distributions, which is not always the case with real world datasets.

## Using Gaussian Mixture Models to Generate Data

Because of their generative nature, GMMs can generate synthetic data by sampling from the learned distribution. By randomly selecting a component according to the mixing weights and sampling from the corresponding Gaussian distribution, synthetic data points are drawn from the learned distribution, ensuring that the new data mimics the characteristics of the original data.

I used GMMs to generate 3 different types of irises’ (Setosa, Versicolour, and Virginica) using data on their petal and sepal length. This is the famous https://scikit-learn.org/1.5/auto_examples/datasets/plot_iris_dataset.html.

## Clustering Iris Dataset

This is a plot of the resulting clusters after fitting a GMM to classify observations of petal length and width:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/gmms1.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Clustering results.
</div>

## Generating Data

I use the previously fitted GMM to generate 300 observations of flowers:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/gmms12.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Generated data.
</div>


