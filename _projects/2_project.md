---
layout: page
title: Quantum Generative Adversarial Networks
description: Created a quantum machine learning model capable of generating handwritten digits.
img: assets/img/MNIST.png
importance: 2
category:
giscus_comments: true
code: https://github.com/hillspen/qgan
paper: /assets/pdf/QGAN_CUCAI.pdf
slides: /assets/pdf/QGAN Slides.pdf
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

Quantum computing uses qbits (rather than bits) to represent data. While a bit is either 0 or 1, a qbit can be 0, 1, or both! This has many advantages (and disadvantages!), one of which is the ability to represent more data using comparitively fewer (q)bits. In the context of machine learning models, quantum computing allows us to define our model as a series of parametrized rotations, leading to lower complexity (in terms of the number of trainable parameters).

In this project, we created a quantum computing version of a generative adversarial network, known as a QGAN. In classical GANs, there is a discriminator model (which classifies a sample as real or fake) and a generative model (which creates new samples). They two are pitted against each other, improving adversarially. In the quantum realm, we are able to take advantage of entanglement to achieve more efficient training.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/QGAN.png" title="QGAN Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Architecture for a QGAN. 
</div>

We trained our QGAN to generate novel handwritten digits (using MNIST). We has to design a (very!) compressive autoencoder to reducde the 28x28 MNIST images to only 4 qubits. This method improved perceptually on the state-of-the-art QGAN architectures, which at the time used PCA to encode the images. We were quite limited by the number of qubits commercially available (in 2021 that number was 4). Nowadays, we would have been able to run our model on 27+ qubits. We presented this work at the Canadian Undergraduate Conference in AI (CUCAI) 2022 and published in their conference proceedings.
