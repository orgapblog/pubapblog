---
layout: post
date: 2019-08-08
title: Inference in probabilistic models
tags: [distill]
mathjax: true
---

__Inference__: $x\sim p_{X}$, $z=f(x)$.  
__Generation__: $z\sim p_{Z}$, $x=f^{-1}(z)$

How can we use a model $p(\mathbf{x}, \mathbf{z})$ to analyze some data $\mathbf{x}$? In other words, what hidden structure of $\mathbf{z}$ explains the data? We seek to infer this hidden structure using the model.

One method of inference leverages Bayes’ rule to define the posterior
\\[p(\mathbf{z} \mid \mathbf{x}) = \frac{p(\mathbf{x}, \mathbf{z})}{\int_{z} p(\mathbf{x}, \mathbf{z}) \text{d}\mathbf{z}}.\\]
​​ 
The posterior is the distribution of the latent variables $\mathbf{z}$, conditioned on some (observed) data $\mathbf{x}$. Drawing analogy to representation learning, it is a probabilistic description of the data’s hidden representation. Often this distribution is unknown and difficult to compute due to intractable denominator (which has to be computed over all comfiguration of states). Hence, we go for approximations.

$2$ methods exist: Sampling methods a.k.a. Monte-Carlo methods and Variational inference.

**Sampling methods** involves drawing random samples from an unknown true distribution. Some methods are Importance sampling, Rejection sampling, Metropolis-hastings method and Gibbs sampling. The last two mthods falls under category of MCMC methods.

**Variational methods** involves approximating the unknown true distribution $p(\mathbf{x})$ with a simpler known distribution $q(\mathbf{x};\theta)$ parametrized by $\theta$. Basically we minimize the divergence between these distributions over $\theta$. To appriximate $p(\mathbf{x})$, *variational lower bound* is the key. 2 ways to derive it: using Jensen's inequality and using KL divergence. More on this [here](http://users.umiacs.umd.edu/~xyang35/files/understanding-variational-lower.pdf). We then maximize this VB to approximate $q$ to $p$. Its connections with deeplearning are beautifully established in paper - *Auto-encoding Variational Bayes*.

More on these methods could be read in the excellent book by David Mckay - `Information theory, Inference and Learning Algorithms' and from blogs [1](https://medium.com/neuralspace/inference-in-probabilistic-models-monte-carlo-and-deterministic-methods-eae8800ee095), [2](http://arogozhnikov.github.io/2016/12/19/markov_chain_monte_carlo.html).