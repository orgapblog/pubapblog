---
layout: post
date: 2019-09-08
title: Fixing the NaNs in SVD.backward() problem
tags: [distill]
mathjax: true
---

Typically, in the case of datasets such as MNIST, CIFAR-10; we have categorical labels. When the number of samples is less than the number of categories, this means that the kernel matrix of such dataset will be severly rank deficient; no matter whatever the function map is used. In RKMs, we can easily hedge that problem because we add many kernel matrices togather. Hence, the resulting matrix could be made well-conditioned, since the data in $\mathcal{X}$ is typically distinct.  