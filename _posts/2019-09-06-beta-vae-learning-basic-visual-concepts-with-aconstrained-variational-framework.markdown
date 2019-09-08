---
layout: post
date: 2019-09-06
title: Beta-VAE - Learning Basic Visual Concepts with a Constrained Variational Framework
tags: [paper_summary]
mathjax: true
---

[Original Paper link](https://openreview.net/references/pdf?id=Sy2fzU9gl)

They propose $β$-VAE, a deep unsupervised generative approach for disentangled factor learning that can automatically discover the *independent latent
factors* of variation in unsupervised data (see post on [Latent Variable Models](/post/latent-variable-models/)).

They propose
to augment the original VAE framework with a single hyperparameter $β$ that controls the extent
of learning constraints applied to the model. The constraints impose a limit on the capacity of the
latent information channel and an emphasis on learning statistically *independent latent factors*. This,
when combined with the data log likelihood maximisation objective of generative models, leads to
the model acquiring the most efficient latent representation of the data, which is disentangled if the
data is produced using at least some ground truth factors of variation that are independent.

They develop a new *measure of disentanglement* and show that β-VAE also significantly outperforms all
our baselines on this measure (ICA, PCA, VAE by Kingma & Ba (2014), DC-IGN by Kulkarni et al.
(2015), and InfoGAN by Chen et al. (2016))

**Key Step:** In order
to encourage this disentangling property in the inferred $q_{\phi}(z\vert x)$, we introduce a constraint over it by
trying to match it to a prior $p(z)$ that can both control the capacity of the latent information bottleneck,
and embodies the desiderata of statistical independence mentioned above. This can be achieved if
we set the prior to be an isotropic unit Gaussian ($p(z) = N(0; \mathbf{I})$), hence arriving at the constrained
optimisation problem, where $\epsilon$ specifies the strength of the applied constraint.

$$ \underset{φ;θ}{\mathrm{max}}~
\mathbb{E}_{x\sim D} \left[ \mathbb{E}_{q_{φ}(z\vert x)}[\log p_{θ}(x\vert z)] \right]  \quad \text{subject to}\quad D_{KL}(q_{φ}(z\vert x)\Vert p(z)) < \epsilon $$