---
layout: post
title: Intuition behind Generative RKM
tags: [distill]
mathjax: true
---

Extracting feature through feature maps (in our case CNN), and then forming a latent space whose basis is formed by eigenvectors of kernel matrix. We strongly suspect that this encodes a disentangled representation of input data. This is in strong spirit with latent variable models, where we seek to find the indpendent hidden factors that lead to data generation in first place. For further connections, see post on [latent variable models](/post/latent-variable-models/index.html).