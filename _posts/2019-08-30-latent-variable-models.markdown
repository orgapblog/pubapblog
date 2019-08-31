---
layout: post
title: Latent variable models
tags: [distill]
mathjax: true
---

Many statistical models are generative models (that is, models that specify a full probability density over all variables in the situation) that make use of latent variables to describe a probability distribution over observables.

Some examples of latent variable models are mixture models, which model the observables as coming from a superposed mixture of simple probability distributions (the latent variables are the unknown class labels of the examples); hidden Markov models (Rabiner and Juang, 1986; Durbin et al., 1998); and factor analysis. More recent ones that are also popularized by ML community are RBMs, VAEs and GANs.

The decoding problem for error-correcting codes can also be viewed in terms of a latent variable model - figure below. In that case, the encoding matrix $G$ is normally known in advance. In latent variable modelling, the parameters equivalent to $G$ are usually not known, and must be inferred from the data along with the latent variables $s$. In the figure, The $K$ latent variables are the independent source bits $s_1, \dots , s_K$; these give rise to the observables via the generator matrix $G$.

![](/photos/latent_var.PNG){: style="width: 250px; height: auto;"}

Usually, the latent variables have a simple distribution, often a separable distribution. Thus when we fit a latent variable model, we are finding a description of the data in terms of ‘independent components’. The ‘_independent component analysis_’ algorithm corresponds to perhaps the simplest possible latent variable model with continuous latent variables.

---

## Independent Component Analysis

Some references: [tutorial](/post/latent-variable-models/) and  Ch. 34 in David Mckay - `Information theory, Inference and Learning Algorithms’.

