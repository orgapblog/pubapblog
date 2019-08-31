---
layout: post
date: 2019-08-08
title: Inference in probabilistic models
tags: [distill]
mathjax: true
---

Statistical Machine Learning algorithms try to learn the structure of data by fitting a parametric distribution $p(x;θ)$ to it. Given a dataset, if we can represent it with a distribution, we can:

1. Generate new data “for free” by sampling from the learned distribution in silico; no need to run the true generative process for the data. This is a useful tool if the data is expensive to generate, i.e. a real-world experiment that takes a long time to run. Sampling is also used to construct estimators of high-dimensional integrals over spaces.
2. Evaluate the likelihood of data observed at test time (this can be used for rejection sampling or to score how good our model is).
3. Find the conditional relationship between variables. For example, learning the distribution $p(x_2\vert x_1)$ allows us to build discriminative classification or regression models.
4. Score our algorithm by using complexity measures like entropy, mutual information, and moments of the distribution.

__Inference__: $x\sim p_{X}$, $z=f(x)$.  
__Generation__: $z\sim p_{Z}$, $x=f^{-1}(z)$

How can we use a model $p(\mathbf{x}, \mathbf{z})$ to analyze some data $\mathbf{x}$? In other words, what hidden structure of $\mathbf{z}$ explains the data? We seek to infer this hidden structure using the model.

One method of inference leverages Bayes’ rule to define the posterior
\\[p(\mathbf{z} \mid \mathbf{x}) = \frac{p(\mathbf{x}, \mathbf{z})}{\int_{z} p(\mathbf{x}, \mathbf{z}) \text{d}\mathbf{z}}.\\]
​​ 
The posterior is the distribution of the latent variables $\mathbf{z}$, conditioned on some (observed) data $\mathbf{x}$. Drawing analogy to representation learning, it is a probabilistic description of the data’s hidden representation. Often this distribution is unknown and difficult to compute due to intractable denominator (which has to be computed over all comfiguration of states). Hence, we go for approximations.

$2$ methods exist: Sampling methods a.k.a. Monte-Carlo methods and Variational inference.

**Sampling methods** involves drawing random samples from an unknown true distribution. Some methods are Importance sampling, Rejection sampling, Metropolis-hastings method and Gibbs sampling. The last two mthods falls under category of MCMC methods.

**Variational methods** involves approximating the unknown true distribution $p(\mathbf{x})$ with a simpler known distribution $q(\mathbf{x};\theta)$ parametrized by $\theta$. Basically we minimize the divergence between these distributions over $\theta$. To approximate $p(\mathbf{x})$, *variational lower bound* is the key. We then maximize this VB to approximate $q$ to $p$. Its connections with deeplearning are beautifully established in paper - [Auto-encoding Variational Bayes (Kingma & Welling, 2014)](https://arxiv.org/abs/1312.6114).

More on these methods could be read in the excellent book by David Mckay - `Information theory, Inference and Learning Algorithms' and from blogs [1](https://medium.com/neuralspace/inference-in-probabilistic-models-monte-carlo-and-deterministic-methods-eae8800ee095), [2](http://arogozhnikov.github.io/2016/12/19/markov_chain_monte_carlo.html).

---

### Example: Use of Variational Inference to obtain lower-bound on the marginal likelihood
Consider a general probabilistic model with observations $x$, latent variables $z$ over which we must integrate, and model parameters $θ$. We introduce an approximate posterior distribution for the latent variables $q_{\phi}(z\vert x)$ and follow the variational principle (Jordan et al., 1999) to obtain a bound on the marginal likelihood: 

$$\begin{align*} \log p_{θ}(x) & = \log \int p_{θ}(x\vert z)p(z)dz \\ 
                              & = \log \int \frac{q_{\phi}(z\vert x)}{q_{\phi}(z\vert x)} p_{θ}(x\vert z)p(z)dz \\
                              & = \log \left( \mathbb{E}_{q} \left[ \frac{p( z)}{q_{\phi}(z\vert x)} . q_{\phi}(z\vert x) p_{θ}(x\vert z) \right] \right) \\
                              & \geq \mathbb{E}_{q} \left[\log \left(\frac{p( z)}{q_{\phi}(z\vert x)} . q_{\phi}(z\vert x) p_{θ}(x\vert z)\right) \right]  \\
                              & \geq \mathbb{E}_{q} \left[\log \left(\frac{p( z)}{q_{\phi}(z\vert x)}\right) + \log\left(q_{\phi}(z\vert x) p_{θ}(x\vert z)\right) \right]  \\
                              & = -\mathbb{D}_{\mathrm{KL}} [q_{\phi}(z\vert x) \Vert p( z)] + \mathbb{E}_q [\log p(x\vert z)],
        \end{align*}$$

where we have used Jensen's inequality $ \left(f (\mathbb{E}[x]) ≤ \mathbb{E} [f(x)]\right) $. $p_θ (x\vert z)$ is a likelihood function and $p(z)$ is a prior over the latent variables. This bound is often referred to as the negative free energy $\mathcal{F}$ or as the evidence lower bound (ELBO). It consists of two terms: the first is the KL-divergence between the approximate posterior and the prior distribution (which acts as a regularizer), and the second is a reconstruction error. This bound provides a unified objective function for optimization of both the parameters $θ$ and $\phi$ of the model and variational approximation, respectively.

Current best practice in variational inference performs this optimization using mini-batches and stochastic gradient descent, which is what allows variational inference to be scaled to problems with very large data sets. There are two problems that must be addressed to successfully use the variational approach:

1. efficient computation of the derivatives of the expected log-likelihood $$\nabla_{\phi} \mathbb{E}_{q_{\phi}(z)}\left[\log p_{\theta} (x\vert z)\right]$$. This is tackled in the paper [Auto-encoding Variational Bayes (Kingma & Welling, 2014)](https://arxiv.org/abs/1312.6114) 
2. choosing the richest, computationally-feasible approximate posterior distribution $q(·)$. This is tackled in the paper [Variational Inference of Normalizing Flows (Rezende & Shakir, 2015)](/post/checksum/).
