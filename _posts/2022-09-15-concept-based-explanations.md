---
layout: post
title: "Concept-based explanations"
categories:
    - "paper review"
    - "english"
tags:
    - "english"
---

These notes are a short summary ad review of the paper [Interpretability Beyond Feature Attribution: Quantitative Testing with Concept Activation Vectors (TCAV)](https://arxiv.org/pdf/1711.11279.pdf) by Been Kim et al., which I encountered while reading another, related paper: [Concept-based techniques for "musicologist-friendly" explanations in a deep music classifier](https://arxiv.org/pdf/2208.12485.pdf).

<!--more-->

## What are concept-based explanations and why do we need them?
A lot of explainability techniques for machine learning models' decisions focus on feature importance: which column of a table has the most weight when it comes to deciding whether a client will renew their subscription, which area of an image is scrutinized the most closely by a model that classifies a tumor as benign or cancerous... Although these can be helpful, they rapidly become intractable for models that take many features into account: for an image classifier, each pixel is a feature. And since *machines don't think like humans do*[^1], a raw explanation of what combination of tiny details a model considers important is often impossible to translate into proper human reasons. 

Concept-based explanations are one possible solution to this issue: instead of focusing on low-level *features*, they consider higher-level *concepts*: for example, does a model that classify images of horses and zebras know the concept of stripes? 

Concepts are represented by sets of examples, which need not be part of the original dataset: for our zebra example, we might take closeups of zebra fur, but also blades of grass, or drawings of stripes on paper. The techniques presented in the paper turn these examples into a Concept Activating Vector (CAV), on which we can measure the model's activation, via Testing with a Concept Activating Vector (TCAV). This will allow us to quantify how strongly the model associates this concept with the task it has been trained to do.

## Methodology

This is where it gets technical. The CAV is a vector that needs to capture how the model reacts to examples of the concet, vs. random samples. To do this, one studies the vectors of activations in the neural network. 

For example, consider a NN whose inputs are of dimension $$n$$ and with one layer $$\ell$ of dimension $$m$$. So the activation function of layer $$\ell$$ is a function $$f_\ell : \RR^n \to \RR^m$$. We give the network two sets of samples: one is an example set for our concept (for example, pictures of striped objects), and the other is a set of random examples (for example, pictures of random objects). Each of the samples in these sets is sent to a vector in $$\RR^m$$ via $$f_\ell$$. The Concept Activation Vector is then defined as a normal vector to a hyperplane separating the activation functions for the example dataset and the random dataset. In other words, the CAV is a vectors that "points in the direction of the concept".






[^1]: Machines don't think at all, actually.
