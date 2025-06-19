---
layout: page
title: 3D Human Body Generation
description: Applied the TreeGAN architecture to generate 3D point clouds of the human body.
img: assets/img/3D Generation.png
redirect:
importance: 3
category: work
code: https://github.com/hillspen/3d-human-generation
paper: /assets/pdf/3D Generation.pdf
slides: /assets/pdf/3D Generation CUCAI.pdf
---

<div class="mb-3">
  {% if page.paper %}
    <a href="{{ page.paper }}" class="btn btn-sm btn-project-resource mr-1" target="_blank" role="button">Paper</a>
  {% endif %}
    {% if page.code %}
    <a href="{{ page.code }}" class="btn btn-sm btn-project-resource mr-1" target="_blank" role="button">Code</a>
  {% endif %}
  {% if page.slides %}
    <a href="{{ page.slides }}" class="btn btn-sm btn-project-resource mr-1" target="_blank" role="button">Slides</a>
  {% endif %}
</div>

It is important to machine learning models in the medical field to have access to a large amount of anonymized patient data to train on. This data, however, is often prohibitively expensive or time-consuming to obtain. One solution (at least at the time of our project in 2020) is to generate synthetic data which belongs to the distribution of patients without being conneted to an individual. Generative adversarial networks (GANs) are a machine learning model specifically designed to do just that.

This project designed and implemented a tree-based graph convolutional generative adversarial network (TreeGAN) capable of generating 3D point clouds of the human body. It involved preprocessing meshes into point clouds (for computational savings), implemented graph convolutional networks, and training using the Wasserstein loss.
