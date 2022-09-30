---
layout: post
title: ArXiv musings - 2022, week 39
categories:
    - "arxiv musings"
    - "paper review"
    - "english"
tags:
    - "english"
---

(It's been a while.) Here is a summary of a few papers that caught my eye this week.

<!--more-->
## [Fool SHAP with Stealthily Biased Sampling](https://arxiv.org/abs/2205.15419)

Yet another method to cheat at demonstrating model fairness: with subtly biased sampling of a dataset, one can manipulate the importance values returned by SHAP. I'm always interested in the prerequisites for a posteriori explanation methods to be reliable (for example, importances returned for a model that performs very poorly will be unreliable), and this paper partially answers the question: the testing/explanation dataset has to be sampled from the same distribution as the training dataset. 



## [TruEyes: Utilizing microtasks in mobile apps for crowdsourced labeling of machine learning datasets](https://arxiv.org/pdf/2209.14708.pdf)

A paper that proposes a novel approach to crowdsourcing dataset labeling: instead of relying on Amazon Turks, the research team proposes inserting annotation tasks in place of ads in mobile apps and games.

Not sure how I feel about this...


## [Depression Symptoms Modelling from Social Media Text: A Semi-supervised Learning Approach](https://arxiv.org/pdf/2209.02765.pdf)

While surveys can be unreliable for this purpose (due in part to the cognitive biases of the person surveyed), the language used in social media posts can be used to identified signs of depression. This paper proposes a semi-supervised approach, where tweets were collected from self-disclosed depressive users, and annotated by clinicians. From this smaller dataset, a Depression Symptoms Detection model is trained, more examples are harvested, and the model is fine-tuned.

