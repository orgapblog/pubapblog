---
layout: post
title: Meta-Learning Deep Energy-Based Models
tags: [paper_summary]
mathjax: true
---

[Paper link](https://arxiv.org/abs/1910.02720)

They study the problem of learning associative memory – a system which is able to retrieve a remembered pattern based on its distorted or incomplete version. 

Attractor networks (Hopfield networks are a particular type) provide a sound model of associative memory: patterns are stored as attractors of the network dynamics and associative retrieval is performed by running the dynamics starting from a query pattern until it converges to an attractor.

In such models the dynamics are often implemented as an optimization procedure that minimizes an energy function, such as in the classical Hopfield networks.

![](\photos\sergey_bartunov.png){: style="width: 600px; height: auto;"}

Basically they have interpretation in terms of auto-encoder and minimize the reconstruction errors on distorted patterns to learn appropriate writing and retrieval rules.

\\[ \underset{\theta, r, \tau}{\mathop{min}}~\mathbb{E}_{X\sim p(X)} \left[\mathcal{L}\left(X, \mathop{read}\left(\tilde{X};\mathop{write}(X)\right)\right)\right].\\]

Here writing loss is defined as:

$$ \mathcal{W}\left(x, \theta\right)= \mathcal{E}\left(x, \theta\right) + \alpha ||\nabla_{x}\mathcal{E}\left(x, \theta\right) ||_{2}^{2}+ \beta ||\theta - \bar{\theta}||_{2}^{2}. $$

The Early-stopping gradient descent is implement on writing loss to implement the writing rule:

\\[ \mathop{write}(X)=\theta^{(T)},~~\theta^{(T+1)}=\theta^{(T)}- \eta^{(T)} \frac{1}{N}\sum_{i=1}^{N}\nabla_{\theta}\mathcal{W}(x_i ; \theta^{(T)}) . \\]
Here, $\mathop{write}$ is modelled by encoder and $\mathop{read}$ is modelled by decoder.
