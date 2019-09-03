---
layout: post
title: Latent Space Cartography (Liu et. al, 2019)
tags: [paper_summary]
mathjax: true
---

[Paper Link](https://idl.cs.washington.edu/files/2019-LatentSpaceCartography-EuroVis.pdf)

Employes latent-space visualization techniques (t-SNE, UMAP, and PCA) and contributes to methods eastbalishing semantic relationship between latent-space and the generated model. In particular, they contribute 
1. a review of domain literature and a characterization of common latent-space interpretation goals and tasks; 

2. a visual analysis system that supports these tasks, including novel projection strategies, visual and statistical methods to assess attribute vector uncertainty, and global attribute vector comparison methods; and 

3. three case studies demonstrating new insights into diverse data types across multiple domains.

In the literature, there exists 6 interpretation sub-tasks:

1. **View Reconstruction Examples:** A majority of articles on generative models (31/54) present a list of example generation results. These examples serve as qualitative evidence that the models produce compelling, plausible, yet novel outputs unseen in the training data. They also show reconstruction fidelity versus generation diversity, as there is usually a trade-off between the two.

2. **View Interpolation Results:** Linear interpolation in a continuous latent space is done by following a path between two points and displaying outputs at sampled locations on the path (usually in steps of equal distance). A number of articles (18/54) adopt this approach. Interpolation sequences naturally show the smoothness of the latent space, and they are important indicators of interpretability. For instance, authors may point out subtle changes in transitions that reflect deeper domain-specific principles

3. **Examine Nearest Neighbors:** This task is employed by articles on both word embeddings (10/24) and generative models (6/54), but the emphasis is different. Word embedding articles use
anecdotal nearest neighbors to qualitatively show what the algorithms manage to achieve. Articles on generative models use nearest neighbors from the training set as a comparison, demonstrating
that the algorithms generate novel results indistinguishable from, or better than, the input.

4. **Perform Attribute Vector Arithmetic:** An example of this task for word embeddings shows that the vector(king) - vector(man) + vector(woman) produces a vector very close to vector(queen).
This simple algebraic operation demonstrates that pairs of data points sharing a particular relationship have approximately constant vector offsets. We observe this task in both generative (3/54)
and word embedding (10/24) models.

5. **Compare Similarities:** This task is popular for benchmarks
of word embeddings (13/24), testing how well the cosine similarity
between word vectors matches ratings from human annotators.

6. **Visualize Distribution:** Researchers visualize latent spaces
using various means described in §3. This task is common to both
generative (20/54) and word embedding (7/24) settings.

