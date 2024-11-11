---
kernelspec:
  display_name: Python 3
  language: python
  name: python3
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
---
# Autoencoders
## PCA as an Autoencoder

PCA can also be interpreted as a form of **linear autoencoder**. In an autoencoder, the goal is to compress high-dimensional data into a lower-dimensional representation and then reconstruct it as accurately as possible. PCA achieves this by finding a set of orthogonal axes (principal components) along which the variance in the data is maximized, effectively reducing the dimensionality of the dataset while preserving its essential structure.

In this sense, the **principal components** represent the compressed, latent representation, and the reconstruction involves projecting the data back into the original feature space using only these components. By calculating the first few principal components, we can reconstruct an approximation of the original matrix that captures most of the meaningful variance while filtering out noise and less important features.

This reconstruction can be expressed as:

$$
\mathbf{X} \approx \mathbf{U}_k \mathbf{S}_k \mathbf{V}_k^T
$$

where $\mathbf{U}_k$ and $\mathbf{V}_k$ represent the truncated versions of the original matrices containing only the top $k$ components, and $\mathbf{S}_k$ is the diagonal matrix of the corresponding singular values. The smaller $k$ is relative to the full dimensionality, the more compressed the representation. However, a larger $k$ retains more of the original information.

PCA as an autoencoder is particularly effective for **noise reduction**. By reconstructing the data using only the most important components, we eliminate much of the noise that might be captured by less significant components. This allows for a denoised version of the data that still retains the major underlying patterns. The same principle could be used for [imputations](https://en.wikipedia.org/wiki/Imputation_(statistics)) of [missing values](https://www.rdocumentation.org/packages/missMDA/versions/1.19/topics/imputePCA).


In practice, this approach can be very useful for reducing dimensionality, visualizing data, and improving subsequent machine learning tasks by focusing on the most informative features.

The autoencoder analogy also highlights a key limitation of PCA: it is inherently **linear**. PCA assumes that the important structures in the data can be captured through linear projections. 