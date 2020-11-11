---
layout: post
title: "Conjugate prior bootcamp"
author: "Jordan Bryan"
categories: journal
tags: [documentation,sample]
image: conjugate_priors.jpeg
---

This post follows the table at the end of the [Conjugate prior Wikipedia page](https://en.wikipedia.org/wiki/Conjugate_prior) to derive posterior distributions for parameters of a range of likelihood functions. Many resources for learning the mechanics of posterior inference under conjugate priors [already exist](https://www.johndcook.com/CompendiumOfConjugatePriors.pdf), so there's nothing particularly new to be seen here. However, maybe others learning about Bayesian inference will find this useful as a supplement to other resources.

The derivations here tend to show some of the intermediary steps that might not be obvious to students working these out for the first time. I also tried to follow common naming conventions for parameters of distributions and to keep the notation fairly consistent throughout so that the whole list can be read in a uniform way.

Lowercase \\(n\\) always indicates the number of independent data points drawn from the data-generating distribution, and lowercase \\(i\\) is always the index to this axis. The symbol \\(X\\) or \\(x\\) is always used to denote data.

Every derivation follows the same procedure:

1. Write the posterior distribution as proportional to the product of the joint likelihood function for data points \\(x_1, \dots, x_n\\) and the prior density.
2. Ignore all terms in the product that don't involve the parameter on which inference is being performed.
3. Combine like terms and recognize that the resulting expression has an analogous form to that of the conjugate prior density function.

The derivations for inference on the mean parameters in the \\(\text{Normal}\\) likelihood setting use a shortcut that skips the step of explicitly completing the square for the quadratic term inside the exponential. In general, for a random variable \\(Z\\), constants \\(a\\) and \\(b\\), and proper density function \\(p_Z(z)\\)

$$ 
p_Z(z) \propto e^{-\frac{az^2 + 2bz}{2}} \implies Z \sim \text{Normal}\bigg(a^{-1} b, a^{-1}\bigg)
$$

or equivalently

$$ 
p_Z(z) \propto e^{-\frac{z^2 - 2(b/a)z}{2/a}} \implies Z \sim \text{Normal}\bigg(a^{-1} b, a^{-1}\bigg)
$$

This extends to the multivariate setting where the term inside the exponential is a quadratic form and the constants \\(A\\) and \\(B\\) are a matrix and a vector, respectively:

$$
p_\mathbf{Z}(\mathbf{z}) \propto e^{-\frac{\mathbf{z}^T A \mathbf{z} + 2\mathbf{z}^T B}{2}} \implies \mathbf{Z} \sim \text{MultiNormal}\bigg(A^{-1} B, A^{-1}\bigg)
$$

The reason this shortcut works is because the constant term we would get from completing the square for the quadratic term does not involve the variable of interest \\(z\\). Therefore, it acts as a constant of proportionality equal to \\(e^{-\frac{C}{2}}\\) for some constant \\(C\\), which we can ignore.

## Discrete probability distributions

### Bernoulli likelihood

$$
p_{X|\theta}(x) = \theta^{x}(1-\theta)^{1-x}, ~~~~ x \in \{0, 1\}
$$

#### Inference on success probability \\(\theta\\)

##### Conjugate prior

As a function of \\(\theta\\) alone, the Bernoulli likelihood function is proportional to a Beta density function.

$$
p_{\theta | \alpha, \beta}(\theta) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)}\theta^{\alpha - 1}(1 - \theta)^{\beta - 1}
$$

##### Posterior update

$$
\begin{aligned}
p_{\theta | X_1, \dots, X_n}(\theta) &\propto p_{X_1, \dots, X_n|\theta}(x_1, \dots, x_n) \cdot p_{\theta | \alpha, \beta}(\theta) \\
&\propto \theta^{\sum_{i=1}^n x_i}(1-\theta)^{n-\sum_{i=1}^n x_i} \theta^{\alpha - 1}(1 - \theta)^{\beta - 1} \\
&= \theta^{\alpha + \sum_{i=1}^n x_i - 1}(1-\theta)^{\beta + n-\sum_{i=1}^n x_i - 1} \\
&\propto \text{Beta}\Big(\alpha + \sum_{i=1}^n x_i, \beta + n-\sum_{i=1}^n x_i\Big)
\end{aligned}
$$

### Binomial likelihood

$$
p_{X | N,\theta}(x) = {N \choose x} \theta^x(1-\theta)^{N-x}, ~~~~ x \in \{0, N\}
$$

#### Inference on success probability \\(\theta\\)

##### Conjugate prior

As a function of \\(\theta\\) alone, the Binomial likelihood function is proportional to a Beta density function.

$$
p_{\theta | \alpha, \beta}(\theta) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)}\theta^{\alpha - 1}(1 - \theta)^{\beta - 1}
$$

##### Posterior update

$$
\begin{aligned}
p_{\theta | X_1, \dots, X_n}(\theta) &\propto p_{X_1, \dots, X_n | \mathbf{N},\theta}(x_1, \dots, x_n) \cdot p_{\theta | \alpha, \beta}(\theta) \\
&\propto \theta^{\sum_{i=1}^n x_i}(1-\theta)^{\sum_{i=1}^n N_i -\sum_{i=1}^n x_i} \theta^{\alpha - 1}(1 - \theta)^{\beta - 1} \\
&= \theta^{\alpha + \sum_{i=1}^n x_i - 1}(1-\theta)^{\beta + \sum_{i=1}^n N_i -\sum_{i=1}^n x_i - 1} \\
&\propto \text{Beta}\Big(\alpha + \sum_{i=1}^n x_i, \beta + \sum_{i=1}^n N_i -\sum_{i=1}^n x_i\Big)
\end{aligned}
$$

### Negative binomial likelihood

$$
p_{X | r, \theta}(x) = {x+r-1 \choose x}(1-\theta)^r \theta^x, ~~~~ x \in \{0, \infty\}
$$

#### Inference on success probability \\(\theta\\)

##### Conjugate prior

As a function of \\(\theta\\) alone, the Negative Binomial likelihood function is proportional to a Beta density function.

$$
p_{\theta | \alpha, \beta}(\theta) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)}\theta^{\alpha - 1}(1 - \theta)^{\beta - 1}
$$

##### Posterior update

$$
\begin{aligned}
p_{\theta | X_1, \dots, X_n}(\theta) &\propto p_{X_1, \dots, X_n | \mathbf{r}, \theta}(x_1, \dots, x_n) \cdot p_{\theta | \alpha, \beta}(\theta) \\
&\propto \theta^{\sum_{i=1}^n x_i}(1-\theta)^{\sum_{i=1}^n r_i} \theta^{\alpha - 1}(1 - \theta)^{\beta - 1} \\
&= \theta^{\alpha + \sum_{i=1}^n x_i - 1}(1-\theta)^{\beta + \sum_{i=1}^n r_i - 1} \\
&\propto \text{Beta}\Big(\alpha + \sum_{i=1}^n x_i, \beta + \sum_{i=1}^n r_i \Big)
\end{aligned}
$$

### Poisson likelihood

$$
p_{X | \lambda}(x) =  \frac{\lambda^x e^{-\lambda}}{x!}, ~~~~ x \in \{0, \infty\}
$$

#### Inference on rate parameter \\(\lambda\\)

##### Conjugate prior

As a function of \\(\lambda\\) alone, the Poisson likelihood function is proportional to a Gamma density function.

$$
p_{\lambda | \alpha, \beta}(\lambda) = \frac{\beta^\alpha}{\Gamma(\alpha)} \lambda^{\alpha - 1} e^{-\beta \lambda}
$$

##### Posterior update

$$
\begin{aligned}
p_{\lambda | X_1, \dots, X_n}(\lambda) &\propto p_{X_1, \dots, X_n | \lambda}(x_1, \dots, x_n) \cdot p_{\lambda | \alpha, \beta}(\lambda) \\
&\propto \lambda^{\sum_{i=1}^n x_i} e^{-n\lambda} \lambda^{\alpha - 1} e^{-\beta \lambda} \\
&= \lambda^{\alpha + \sum_{i=1}^n x_i - 1} e^{-(\beta + n)\lambda} \\
&\propto \text{Gamma}\Big(\alpha + \sum_{i=1}^n x_i, \beta + n\Big)
\end{aligned}
$$

### Categorical likelihood

$$
p_{X | \theta_1, \dots, \theta_k} = \theta_1^{\mathbb{I}[x = 1]} \cdots \theta_k^{\mathbb{I}[x = k]}, ~~~~ x \in \{1, k\}
$$

#### Inference on membership probabilities \\(\theta_1, \dots, \theta_k\\)

##### Conjugate prior

As a function of \\(\theta_1, \dots, \theta_k\\) alone, the Categorical likelihood function is proportional to a Dirichlet density function.

$$
p_{\theta_1, \dots, \theta_k | \alpha_1, \dots, \alpha_k}(\theta_1, \dots, \theta_k) = \frac{\Gamma\big(\sum_{j=1}^k \alpha_j \big)}{\prod_{j=1}^k \Gamma(\alpha_j)} \prod_{j=1}^k \theta_j^{\alpha_j - 1}
$$

##### Posterior update

$$
\begin{aligned}
p_{\theta_1, \dots, \theta_k | X_1, \dots, X_n} &\propto p_{X_1, \dots, X_n | \theta_1, \dots, \theta_k}(x_1, \dots, x_n) \cdot p_{\theta_1, \dots, \theta_k | \alpha_1, \dots, \alpha_k}(\theta_1, \dots, \theta_k) \\
&\propto \prod_{j=1}^k \theta_j^{\sum_{i=1}^n \mathbb{I}[x_i = j]} \prod_{j=1}^k \theta_j^{\alpha_j - 1} \\
&= \prod_{j=1}^k \theta_j^{\alpha_j + \sum_{i=1}^n \mathbb{I}[x_i = j] - 1} \\
&\propto \text{Dirichlet}\bigg(\alpha_1 + \sum_{i=1}^n \mathbb{I}[x_i = 1]~~, \dots, ~\alpha_k + \sum_{i=1}^n \mathbb{I}[x_i = k]\bigg)
\end{aligned}
$$

### Multinomial likelihood

$$
p_{\mathbf{X} | \theta_1, \dots, \theta_k, N}(x_1, \dots, x_k) = \frac{N!}{x_1! \cdots x_k!}\prod_{j=1}^k \theta_j^{x_j}, ~~~~ \mathbf{x} \in \{0, N\}^k
$$

#### Inference on membership probabilities \\(\theta_1, \dots, \theta_k\\)

##### Conjugate prior

As a function of \\(\theta_1, \dots, \theta_k\\) alone, the Multinomial likelihood function is proportional to a Dirichlet density function.

$$
p_{\theta_1, \dots, \theta_k | \alpha_1, \dots, \alpha_k}(\theta_1, \dots, \theta_k) = \frac{\Gamma\big(\sum_{j=1}^k \alpha_j \big)}{\prod_{j=1}^k \Gamma(\alpha_j)} \prod_{j=1}^k \theta_j^{\alpha_j - 1}
$$

##### Posterior update

$$
\begin{aligned}
p_{\theta_1, \dots, \theta_k | \mathbf{X}_1, \dots, \mathbf{X}_n} &\propto p_{\mathbf{X}_1, \dots, \mathbf{X}_n | \theta_1, \dots, \theta_k, N}(\mathbf{x}_1, \dots, \mathbf{x}_n) \cdot p_{\theta_1, \dots, \theta_k | \alpha_1, \dots, \alpha_k}(\theta_1, \dots, \theta_k) \\
&\propto \prod_{j=1}^k \theta_j^{\sum_{i=1}^n x_{ij}} \prod_{j=1}^k \theta_j^{\alpha_j - 1} \\
&= \prod_{j=1}^k \theta_j^{\alpha_j + \sum_{i=1}^n x_{ij} - 1} \\
&\propto \text{Dirichlet}\bigg(\alpha_1 + \sum_{i=1}^n x_{i1}~~, \dots, ~\alpha_k + \sum_{i=1}^n x_{ik}\bigg)
\end{aligned}
$$

### Geometric likelihood

$$
p_{X | \theta}(x) = (1 - \theta)^{x-1}\theta, ~~~~ x \in \{1, \infty\}
$$

#### Inference on success probability \\(\theta\\)

##### Conjugate prior

As a function of \\(\theta\\) alone, the Geometric likelihood function is proportional to a Beta density function.

$$
p_{\theta | \alpha, \beta}(\theta) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)}\theta^{\alpha - 1}(1 - \theta)^{\beta - 1}
$$

##### Posterior update

$$
\begin{aligned}
p_{\theta | X_1, \dots, X_n}(\theta) &\propto p_{X_1, \dots, X_n | \theta}(x_1, \dots, x_n) \cdot p_{\theta | \alpha, \beta}(\theta) \\
&\propto (1 - \theta)^{\sum_{i=1}^n x_i - n}\theta^n \theta^{\alpha - 1}(1 - \theta)^{\beta - 1} \\
&= \theta^{\alpha + n - 1}(1-\theta)^{\beta + \sum_{i=1}^n x_i - n - 1} \\
&\propto \text{Beta}\Big(\alpha + n, \beta + \sum_{i=1}^n x_i - n \Big)
\end{aligned}
$$

## Continuous probability distributions

### Normal likelihood

$$
p_{X | \mu, \sigma^2}(x) = \frac{1}{\sqrt{2\pi \sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}
$$

#### Inference on mean \\(\mu\\) with known variance \\(\sigma^2\\)

##### Conjugate prior

As a function of \\(\mu\\) alone, the Normal likelihood function is proportional to a Normal density function.

$$
p_{\mu | \tau, \sigma_0^2} (\mu) = \frac{1}{\sqrt{2 \pi \sigma_0^2}} e^{-\frac{(\mu - \tau)^2}{2 \sigma_0^2}}
$$

##### Posterior update

$$
\begin{aligned}
p_{\mu | X_1, \dots, X_n, \sigma^2} &\propto p_{X_1, \dots, X_n | \mu, \sigma^2}(x_1, \dots, x_n) \cdot p_{\mu | \tau, \sigma_0^2} (\mu) \\
&\propto e^{-\frac{\sum_{i=1}^n (x_i-\mu)^2}{2\sigma^2}} \cdot e^{-\frac{(\mu - \tau)^2}{2 \sigma_0^2}} \\
&= e^{-\frac{\sigma_0^2(\sum_{i=1}^n x_i^2 - 2\mu \sum_{i=1}^n x_i + n\mu^2) + \sigma^2(\mu^2 - 2 \mu \tau + \tau^2)}{2\sigma^2 \sigma_0^2}} \\
&\propto e^{-\frac{(n\sigma_0^2+\sigma^2) \mu^2 - 2 (\sigma^2 \tau + \sigma_0^2 \sum_{i=1}^n x_i) \mu}{2\sigma^2 \sigma_0^2}} \\
&= e^{-\frac{\mu^2 - 2 \big(\frac{\sigma^2 \tau + \sigma_0^2\sum_{i=1}^n x_i}{n\sigma_0^2+\sigma^2}\big) \mu}{2 \big(\frac{\sigma^2 \sigma_0^2}{n\sigma_0^2+\sigma^2} \big)}} \\
&= e^{-\frac{\mu^2 - 2 \bigg(\frac{\frac{\tau}{\sigma_0^2} + \frac{\sum_{i=1}^n x_i}{\sigma^2}}{\frac{n}{\sigma^2}+\frac{1}{\sigma_0^2}}\bigg) \mu}{2 \big(\frac{n}{\sigma^2}+\frac{1}{\sigma_0^2} \big)^{-1}}} \\
&\propto \text{Normal}\bigg(\Big( \frac{n}{\sigma^2} + \frac{1}{\sigma_0^2} \Big)^{-1}\Big(\frac{n}{\sigma^2} \bar{x} + \frac{1}{\sigma_0^2} \tau \Big), \Big(\frac{n}{\sigma^2} + \frac{1}{\sigma_0^2}\Big)^{-1} \bigg)
\end{aligned}
$$

#### Inference on variance \\(\sigma^2\\) with known mean \\(\mu\\)

##### Conjugate prior

As a function of \\(1 / \sigma^2\\) alone, the Normal likelihood function is proportional to a Gamma density function.

$$
p_{1/\sigma^2 | \alpha, \beta}(1/\sigma^2) = \frac{\beta^\alpha}{\Gamma(\alpha)} \Big(\frac{1}{\sigma^2}\Big)^{\alpha - 1} e^{- \frac{\beta}{\sigma^2}}
$$

##### Posterior update

$$
\begin{aligned}
p_{1 / \sigma^2 | X_1, \dots, X_n, \mu}(1 / \sigma^2) &\propto p_{X_1, \dots, X_n | \mu, 1 / \sigma^2}(x_1, \dots, x_n) \cdot p_{1/\sigma^2 | \alpha, \beta}(1/\sigma^2) \\
&\propto \Big(\frac{1}{\sigma^2}\Big)^{n/2} e^{-\frac{\sum_{i=1}^n (x_i-\mu)^2}{2\sigma^2}} \Big(\frac{1}{\sigma^2}\Big)^{\alpha - 1} e^{- \frac{\beta}{\sigma^2}} \\
&= \Big(\frac{1}{\sigma^2}\Big)^{\alpha + n/2 - 1} e^{-\frac{\beta + \frac{1}{2}\sum_{i=1}^n(x_i-\mu)^2}{\sigma^2}} \\
&\propto \text{Gamma}\bigg(\alpha + n/2, \beta + \frac{1}{2}\sum_{i=1}^n(x_i-\mu)^2 \bigg)
\end{aligned}
$$

### Multivariate normal likelihood

$$
p_{\mathbf{X} | \mu, \Sigma}(\mathbf{x}) = \frac{1}{\sqrt{2 \pi |\Sigma|}} e^{-\frac{(\mathbf{x} - \mu)^T \Sigma^{-1} (\mathbf{x} - \mu) }{2}}
$$

#### Inference on mean vector \\(\mu\\) with known covariance matrix \\(\Sigma\\)

##### Conjugate prior

As a function of \\(\mu\\) alone, the Multivariate Normal likelihood function is proportional to a Multivariate Normal density function.

$$
p_{\mu | \tau, \Sigma_0}(\mu) = \frac{1}{\sqrt{2 \pi |\Sigma_0|}} e^{-\frac{(\mu - \tau)^T \Sigma_0^{-1} (\mu - \tau) }{2}}
$$

##### Posterior update

$$
\begin{aligned}
p_{\mu | \mathbf{X}_1, \dots, \mathbf{X}_n, \Sigma}(\mu) &\propto p_{\mathbf{X}_1, \dots, \mathbf{X}_n | \mu, \Sigma}(\mathbf{x}_1, \dots, \mathbf{x}_n) \cdot p_{\mu | \tau, \Sigma_0}(\mu) \\
&\propto e^{-\frac{\sum_{i=1}^n (\mathbf{x}_i - \mu)^T \Sigma^{-1} (\mathbf{x}_i - \mu) }{2}} e^{-\frac{(\mu - \tau)^T \Sigma_0^{-1} (\mu - \tau) }{2}} \\
&= e^{-\frac{\sum_{i=1}^n \mathbf{x}_i^T \Sigma^{-1} \mathbf{x}_i - 2 \mu^T \Sigma^{-1} \sum_{i=1}^n \mathbf{x}_i + n \mu^T  \Sigma^{-1} \mu}{2}} e^{-\frac{\mu^T  \Sigma_0^{-1} \mu - 2 \mu^T  \Sigma_0^{-1} \tau + \tau^T  \Sigma_0^{-1} \tau}{2}} \\
&\propto e^{-\frac{\mu^T \big(n\Sigma^{-1} + \Sigma_0^{-1}\big) \mu - 2 \mu^T \big(\Sigma^{-1} \sum_{i=1}^n \mathbf{x}_i + \Sigma_0^{-1}\tau\big)}{2}} \\
&\propto \text{MultiNormal}\bigg(\big(n\Sigma^{-1} + \Sigma_0^{-1}\big)^{-1} \big(n \Sigma^{-1} \bar{\mathbf{x}} + \Sigma_0^{-1}\tau\big), \big(n\Sigma^{-1} + \Sigma_0^{-1}\big)^{-1} \bigg)
\end{aligned}
$$

#### Inference on covariance matrix \\(\Sigma\\) with known mean \\(\mu\\)

##### Conjugate prior

As a function of \\(\Sigma^{-1}\\) alone, the Multivariate Normal likelihood function is proportional to a Wishart density function.

$$
p_{\Sigma^{-1} | \Sigma_0^{-1}, \nu_0}(\Sigma^{-1}) = \frac{1}{2^{\nu_0p/2}|\Sigma_0|^{\nu_0/2} \Gamma_{p}(\nu_0/2)} |\Sigma^{-1}|^{\frac{\nu_0 - p - 1}{2}} e^{\text{tr}\big(\Sigma_0^{-1} \Sigma^{-1}\big)/2}
$$

##### Posterior update

$$
\begin{aligned}
p_{\Sigma^{-1} | \mathbf{X}_1, \dots, \mathbf{X}_n, \mu}(\Sigma^{-1}) &\propto p_{\mathbf{X}_1, \dots, \mathbf{X}_n | \mu, \Sigma}(\mathbf{x}_1, \dots, \mathbf{x}_n) \cdot p_{\Sigma^{-1} | \Sigma_0^{-1}, n}(\Sigma^{-1}) \\
&\propto |\Sigma|^{-n/2} e^{-\frac{\sum_{i=1}^n (\mathbf{x}_i - \mu)^T \Sigma^{-1} (\mathbf{x}_i - \mu) }{2}} |\Sigma|^{-\frac{\nu_0 - p - 1}{2}} e^{\text{tr}\big(\Sigma_0^{-1} \Sigma^{-1}\big)/2} \\
&= |\Sigma^{-1}|^{\frac{n + \nu_0 - p - 1}{2}} e^{-\frac{\text{tr}\big([\sum_{i=1}^n (\mathbf{x}_i - \mu)(\mathbf{x}_i - \mu)^T] \Sigma^{-1}\big) + \text{tr}\big(\Sigma_0^{-1} \Sigma^{-1}\big)}{2}} \\
&= |\Sigma^{-1}|^{\frac{n + \nu_0 - p - 1}{2}} e^{-\frac{\text{tr}\big(([\sum_{i=1}^n (\mathbf{x}_i - \mu)(\mathbf{x}_i - \mu)^T]  + \Sigma_0^{-1}) \Sigma^{-1}\big)}{2}} \\
&\propto \text{Wishart}\bigg(\big([\sum_{i=1}^n (\mathbf{x}_i - \mu)(\mathbf{x}_i - \mu)^T]  + \Sigma_0^{-1}\big)^{-1}, n + \nu_0 \bigg)
\end{aligned}
$$

### Uniform likelihood

$$
p_{X | \theta}(x) = \frac{1}{\theta} \cdot \mathbb{I}[0 < x \leq \theta]
$$

#### Inference on upper boundary \\(\theta\\)

##### Conjugate prior

As a function of \\(\theta\\) alone, the Uniform likelihood is proportional to a Pareto density function.

$$
p_{\theta | k, m}(\theta) = \frac{k m^k}{\theta^{k + 1}} \cdot \mathbb{I}[m \leq \theta]
$$

##### Posterior update

$$
\begin{aligned}
p_{\theta | X_1, \dots, X_n} &\propto p_{X_1, \dots, X_n | \theta}(x_1, \dots, x_n) \cdot p_{\theta | k, m}(\theta) \\
&\propto \frac{\mathbb{I}[0 < \max(x_1, \dots, x_n) \leq \theta]}{\theta^n} \frac{\mathbb{I}[m \leq \theta]}{\theta^{k + 1}} \\ 
&= \frac{\mathbb{I}[0 < \max(x_1, \dots, x_n, m) \leq \theta]}{\theta^{k + n + 1}} \\
&\propto \text{Pareto}\bigg(\max(x_1, \dots, x_n, m), k + n \bigg)
\end{aligned}
$$

### Pareto likelihood

$$
p_{X | k, m}(x) = \frac{k m^k}{x^{k + 1}}
$$

#### Inference on shape parameter \\(k\\) with known minimum value \\(m\\)

##### Conjugate prior

As a function of \\(k\\) alone, the Pareto likelihood function is proportional to a Gamma density function.

$$
p_{k | \alpha, \beta}(k) = \frac{\beta^\alpha}{\Gamma(\alpha)} k^{\alpha - 1} e^{-\beta k}
$$

##### Posterior update

$$
\begin{aligned}
p_{k | X_1, \dots, X_n, m}(k) &\propto p_{X_1, \dots, X_n | k, m}(x_1, \dots, x_n) \cdot p_{k | \alpha, \beta}(k) \\
&\propto \frac{k^n m^{nk}}{\prod_{i=1}^n x_i^{k + 1}} k^{\alpha - 1} e^{-\beta k} \\
&= k^n e^{-k\sum_{i=1}^n \log(x_i/m)} k^{\alpha - 1} e^{-\beta k} \\
&= k^{\alpha + n - 1} e^{-(\beta + \sum_{i=1}^n \log (x_i / m))k} \\
&\propto \text{Gamma}\bigg(\alpha + n, \beta + \sum_{i=1}^n \log (x_i / m)\bigg)
\end{aligned}
$$

### Weibull likelihood

$$
p_{X | \theta, k}(x) = k\theta x^{k-1} e^{-\theta x^k}
$$

#### Inference on scale parameter \\(\theta\\) with known shape \\(k\\)

##### Conjugate prior

As a function of \\(\theta\\) alone, the Weibull likelihood function is proportional to a Gamma density function.

$$
p_{\theta | \alpha, \beta}(\theta) = \frac{\beta^\alpha}{\Gamma(\alpha)} \theta^{\alpha - 1} e^{-\beta \theta}
$$

##### Posterior update

$$
\begin{aligned}
p_{\theta | X_1, \dots, X_n, k} &\propto p_{X_1, \dots, X_n | \theta, k}(x_1, \dots, x_n) \cdot p_{\theta | \alpha, \beta}(\theta) \\
&\propto \theta^n e^{-\theta\sum_{i=1}^n x_i^k} \theta^{\alpha - 1} e^{-\beta \theta} \\
&= \theta^{\alpha + n - 1} e^{-(\beta + \sum_{i=1}^n x_i^k)\theta} \\
&\propto \text{Gamma}\bigg(\alpha + n, \beta + \sum_{i=1}^n x_i^k \bigg)
\end{aligned}
$$

### Log-normal likelihood

$$
p_{X | \mu, \sigma^2}(x) = \frac{1}{x \sqrt{2 \pi \sigma^2}} e^{-\frac{(\log x - \mu)^2}{2 \sigma^2}}
$$

#### Inference on mean \\(\mu\\) with known variance \\(\sigma^2\\)

##### Conjugate prior

As a function of \\(\mu\\) alone, the Log-normal likelihood function is proportional to a Normal density function.

$$
p_{\mu | \tau, \sigma_0^2}(\mu) = \frac{1}{\sqrt{2 \pi \sigma_0^2}} e^{-\frac{(\mu - \tau)^2}{2\sigma_0^2}}
$$

##### Posterior update

$$
\begin{aligned}
p_{\mu | X_1, \dots, X_n, \sigma^2}(\mu) &\propto p_{X_1, \dots, X_n | \mu, \sigma^2}(x_1, \dots, x_n) \cdot p_{\mu | \tau_0, \sigma_0^2}(\mu) \\
&\propto e^{-\frac{\sum_{i=1}^n (\log x_i - \mu)^2}{2 \sigma^2}} e^{-\frac{(\mu - \tau)^2}{2\sigma_0^2}} \\
&= e^{-\frac{\sigma_0^2(\sum_{i=1}^n \log(x_i)^2 - 2\mu \sum_{i=1}^n \log x_i + n\mu^2) + \sigma^2(\mu^2 - 2 \mu \tau + \tau^2)}{2\sigma^2 \sigma_0^2}} \\
&\propto e^{-\frac{(n\sigma_0^2+\sigma^2) \mu^2 - 2 (\sigma^2 \tau + \sigma_0^2 \sum_{i=1}^n \log x_i) \mu}{2\sigma^2 \sigma_0^2}} \\
&= e^{-\frac{\mu^2 - 2 \big(\frac{\sigma^2 \tau + \sigma_0^2\sum_{i=1}^n \log x_i}{n\sigma_0^2+\sigma^2}\big) \mu}{2 \big(\frac{\sigma^2 \sigma_0^2}{n\sigma_0^2+\sigma^2} \big)}} \\
&= e^{-\frac{\mu^2 - 2 \bigg(\frac{\frac{\tau}{\sigma_0^2} + \frac{\sum_{i=1}^n \log x_i}{\sigma^2}}{\frac{n}{\sigma^2}+\frac{1}{\sigma_0^2}}\bigg) \mu}{2 \big(\frac{n}{\sigma^2}+\frac{1}{\sigma_0^2} \big)^{-1}}} \\
&\propto \text{Normal}\bigg(\Big( \frac{n}{\sigma^2} + \frac{1}{\sigma_0^2} \Big)^{-1}\Big(\frac{n}{\sigma^2} \frac{\sum_{i=1}^n \log x_i}{n} + \frac{1}{\sigma_0^2} \tau \Big), \Big(\frac{n}{\sigma^2} + \frac{1}{\sigma_0^2}\Big)^{-1} \bigg)
\end{aligned}
$$

#### Inference on variance \\(\sigma^2\\) with known mean \\(\mu\\)

##### Conjugate prior

As a function of \\(1 / \sigma^2\\) alone, the Log-normal likelihood function is proportional to a Gamma density function.

$$
p_{1/\sigma^2 | \alpha, \beta}(1/\sigma^2) = \frac{\beta^\alpha}{\Gamma(\alpha)} \Big(\frac{1}{\sigma^2}\Big)^{\alpha - 1} e^{- \frac{\beta}{\sigma^2}}
$$

##### Posterior update

$$
\begin{aligned}
p_{1 / \sigma^2 | X_1, \dots, X_n, \mu}(1 / \sigma^2) &\propto p_{X_1, \dots, X_n | \mu, 1 / \sigma^2}(x_1, \dots, x_n) \cdot p_{1/\sigma^2 | \alpha, \beta}(1/\sigma^2) \\
&\propto \Big(\frac{1}{\sigma^2}\Big)^{n/2} e^{-\frac{\sum_{i=1}^n (\log x_i-\mu)^2}{2\sigma^2}} \Big(\frac{1}{\sigma^2}\Big)^{\alpha - 1} e^{- \frac{\beta}{\sigma^2}} \\
&= \Big(\frac{1}{\sigma^2}\Big)^{\alpha + n/2 - 1} e^{-\frac{\beta + \frac{1}{2}\sum_{i=1}^n(\log x_i-\mu)^2}{\sigma^2}} \\
&\propto \text{Gamma}\bigg(\alpha + n/2, \beta + \frac{1}{2}\sum_{i=1}^n(\log x_i-\mu)^2 \bigg)
\end{aligned}
$$

### Exponential likelihood

$$
p_{X | \lambda}(x) = \lambda e^{-\lambda x}
$$

#### Inference on rate parameter \\(\lambda\\)

##### Conjugate prior

As a function of \\(\lambda\\) alone, the Exponential likelihood function is proportional to a Gamma density function.

$$
p_{\lambda | \alpha, \beta}(\lambda) = \frac{\beta^\alpha}{\Gamma(\alpha)} \lambda^{\alpha - 1} e^{-\beta \lambda}
$$

##### Posterior update

$$
\begin{aligned}
p_{\lambda | X_1, \dots, X_n}(\lambda) &\propto  p_{X_1, \dots, X_n | \lambda}(x_1, \dots, x_n) \cdot p_{\lambda | \alpha, \beta}(\lambda) \\
&\propto \lambda^n e^{-\lambda \sum_{i=1}^n x_i} \lambda^{\alpha - 1} e^{-\beta \lambda} \\
&= \lambda^{\alpha + n - 1} e^{-(\beta + \sum_{i=1}^n x_i) \lambda} \\
&\propto \text{Gamma}\bigg(\alpha + n, \beta + \sum_{i=1}^n x_i\bigg)
\end{aligned}
$$

### Gamma likelihood

$$
p_{X | \alpha, \beta}(x) = \frac{\beta^\alpha}{\Gamma(\alpha)} x^{\alpha - 1} e^{-\beta x}
$$

#### Inference on scale parameter \\(\beta\\) with known shape \\(\alpha\\)

##### Conjugate prior

As a function of \\(\beta\\) alone, the Gamma likelihood function is proportional to a Gamma density function.

$$
p_{\beta | \alpha_0, \beta_0}(\beta) = \frac{\beta_0^{\alpha_0}}{\Gamma(\alpha_0)} \beta^{\alpha_0 - 1} e^{-\beta_0 \beta}
$$

##### Posterior update

$$
\begin{aligned}
p_{\beta | X_1, \dots, X_n, \alpha}(\beta) &\propto p_{X_1, \dots, X_n | \alpha, \beta}(x_1, \dots, x_n) \cdot p_{\beta | \alpha_0, \beta_0}(\beta) \\
&\propto \beta^{n\alpha} e^{-\beta \sum_{i=1}^n x_i} \beta^{\alpha_0 - 1} e^{-\beta_0 \beta} \\
&= e^{\alpha_0 + n\alpha - 1} e^{-(\beta_0 + \sum_{i=1}^n x_i) \beta} \\
&\propto \text{Gamma}\bigg(\alpha_0 + n\alpha, \beta_0 + \sum_{i=1}^n x_i \bigg)
\end{aligned}
$$