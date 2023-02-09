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

A short survey paper of methods that combine Topological Data Analysis with deep learning. TDA studies the general shape of the data and is robust to deformation and noise, which makes it a powerful tool for data analysis.
