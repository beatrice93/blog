---
layout: post
title: ArXiv musings - 2023, week 6
categories:
    - "arxiv musings"
    - "paper review"
    - "english"
tags:
    - "english"
---

(It's been a while.) Here is a summary of a few papers that caught my eye this week.

<!--more-->
## [Clinical BioBERT Hyperparameter Optimization using Genetic Algorithm](https://arxiv.org/abs/2302.03822)

The authors use regex + a neural network classifier to extract Social Determinants of Health from medical records. Social determinants of health are things like where a person is born, their level of education, etc. They impact health outcomes like diabetes, obesity, respiratory illnesses... but are rarely recorded in a systematic fashion (in general, they are filled as plain text by the person's physician). The authors of this paper use regex to extract potentially relevant sentences from medical forms/reports, then a language model to classify this text as relevant or not in terms of Social Determinants of Health. The language model's hyperparameters were tuned using a genetic algorithm.

## [Topological Deep Learning: A Review of an Emerging Paradigm](https://arxiv.org/pdf/2302.03836.pdf)

A short survey paper of methods that combine Topological Data Analysis with deep learning. TDA studies the general shape of the data and is robust to deformation and noise, which makes it a powerful tool for data analysis. It can be integrated at several point in a deep learning model: either as a layer to learn embeddings of topological features, as a loss term that compares the topological features of the output to those of the expected output, or after training, to estimate the topological complexity of the model.

The applications seem interesting, and TDA has shown some successes in classification/clustering tasks; but there are some limitations to its integration in a deep learning process: its lack of robustness to sampling (different data samples might have different topologies), and the computational cost of calculating persistent homology, to name a few.


