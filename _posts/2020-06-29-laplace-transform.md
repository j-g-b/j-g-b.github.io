---
layout: post
title: "The Laplace transform for computing integrals over the probability simplex"
author: "Jordan Bryan"
categories: journal
tags: [documentation,sample]
image: dirichlet.png
---

This post concerns taking integrals over the \\(K\\)-probability simplex, defined as

$$
\Delta_K = \left\{\boldsymbol{\theta} \in \mathbb{R}^K : \boldsymbol{\theta} \geq 0, \boldsymbol{\theta}^\top \mathbf{1} = 1\right\}
$$

In general, simplex integrals are difficult to evaluate. However, product functions of the form 

$$
\prod_{k=1}^K f_k (\theta_k)
$$

have a special structure that allows integrals over \\(\Delta_k\\) to be evaluated with tools from functional analysis. The first step to evaluating these kinds of integrals is to determine the bounds of integration that define \\(\Delta_K\\).

# Integration bounds

Integral bounds determine not only *which* space is filled, but also in some sense *how* that space is filled. Consider the example of an integral in two variables over the space 

$$
\mathcal{C} = \left\{(x,y) \in \mathbb{R}^2 : 0 < y < x < 1 \right\}
$$

This can be written as

$$
\int_{\mathcal{C}} xy ~ d(x,y) = \int_{0}^1 \int_{y}^1 xy ~ dx ~ dy
$$

or

$$
\int_{\mathcal{C}} xy ~ d(x,y) = \int_{0}^1 \int_{0}^x xy ~ dy ~ dx
$$

Although the value of the integral remains the same regardless of the order of integration, the manner in which the space is filled changes. The first choice of integration order says

- \\(y\\) varies from 0 to 1
- For each fixed \\(y\\) value, \\(x\\) varies from \\(y\\) to 1

The second choice of integration order says

- \\(x\\) varies from 0 to 1
- For each fixed \\(x\\) value, \\(y\\) varies from 0 to \\(x\\) 

# Convolution form of the simplex integral

With this in mind, consider the following procedure for filling the space \\(\Delta_K\\):

- \\(\theta_1\\) varies from 0 to 1
- \\(\theta_2\\) varies from 0 to \\(1 - \theta_1\\)
- \\(\theta_3\\) varies from 0 to \\(1 - \theta_1 - \theta_2\\)

and so forth, until

- \\(\theta_{K-1}\\) varies from 0 to \\(1 - \sum_{k=1}^{K-2} \theta_k \\)
- \\(\theta_K \\) is equal to \\(1 - \sum_{k=1}^{K-1} \theta_k \\)

This ordering can be used to evaluate the integral of a product of functions over \\(\Delta_K\\):

$$
\int_{\Delta_K} \prod_{k=1}^K f_k (\theta_k) d \boldsymbol{\theta} = \int_{0}^1 \int_{0}^{1 - \theta_1} \dots \int_{0}^{1 - \sum_{k=1}^{K-2} \theta_k} f_K\left(1 - \sum_{k=1}^{K-1} \theta_k \right)\prod_{k=1}^{K-1} f_k (\theta_k) d \theta_{K-1} d \theta_{K-2} \dots d \theta_{1}
$$

Notice that since \\(\theta_K\\) is fully determined by the values of the other \\(\theta\\)'s, we do not take an integral over \\(\theta_K\\). Instead, we plug in \\(1 - \sum_{k=1}^{K-1} \theta_k\\) as the argument of \\(f_K\\). 

Making the substitution \\(\tau_j = 1 - \sum_{k=1}^j \theta_k\\) yields

$$
\int_{0}^{\tau_0} \int_{0}^{\tau_1} \dots \int_{0}^{\tau_{K-3}} \prod_{k=1}^{K-2} f_k (\theta_k) \left[\int_{0}^{\tau_{K-2}} f_K\left(\tau_{K-2} - \theta_{K-1} \right) f_{K-1} (\theta_{K-1}) d \theta_{K-1} \right]  d \theta_{K-2} \dots d \theta_{1}
$$

The expression in the brackets above is the **convolution** of the functions \\(f_{K-1}\\) and \\(f_{K}\\), evaluated at \\(\tau_{K-2}\\). Substituting this back into the integral yields

$$
\int_{0}^{\tau_0} \int_{0}^{\tau_1} \dots \int_{0}^{\tau_{K-4}} \prod_{k=1}^{K-3} f_k (\theta_k) \int_{0}^{\tau_{K-3}} f_{K-2}(\theta_{K-2}) (f_{K-1} \ast f_{K})(\tau_{K-2})  d \theta_{K-2} \dots d \theta_{1}
$$

Re-writing the interior integral in terms of \\(\tau_{K-3}\\), we have

$$
\int_{0}^{\tau_0} \int_{0}^{\tau_1} \dots \int_{0}^{\tau_{K-4}} \prod_{k=1}^{K-3} f_k (\theta_k) \left[ \int_{0}^{\tau_{K-3}} f_{K-2}(\theta_{K-2}) (f_{K-1} \ast f_{K})(\tau_{K-3} - \theta_{K-2})  d \theta_{K-2}\right] d \theta_{K-3} \dots d \theta_{1}
$$

which again gives the convolution form \\( (f_{K-2} \ast f_{K-1} \ast f_K)(\tau_{K-3})\\) in the brackets above. By induction, we obtain

$$
\int_{\Delta_K} \prod_{k=1}^K f_k (\theta_k) d \boldsymbol{\theta} = \left( f_1 \ast f_2 \ast \dots \ast f_K \right) (\tau_0) = \left( \otimes_{k=1}^K f_k \right) (1)
$$

This form is compact, but still difficult to evaluate. The **convolution theorem** will help to transform this expression into something computable.

# The Laplace transform

The **Laplace transform** is an operator on functions with the following definition

$$
\mathcal{L} \left[ f \right](s) = \mathcal{F}(s) = \int_{0}^\infty e^{-s t} f(t) dt
$$

The convolution theorem says that the Laplace transform of a convolution of functions is the product of the respective Laplace transforms. Namely,

$$
\mathcal{L} \left[(f \ast g)\right](s) = \mathcal{F}(s) \mathcal{G}(s)
$$

We can use the convolution theorem, along with the **inverse Laplace transform**, to observe that the following relationship holds in general

$$
\left( \otimes_{k=1}^K f_k \right) (t) = \mathcal{L}^{-1} \left[ \mathcal{L}\left[ \left( \otimes_{k=1}^K f_k \right) \right] \right] (t) = \mathcal{L}^{-1} \left[ \prod_{k=1}^K \mathcal{F}_k(s) \right] (t)
$$

Since we showed that the simplex integral in the section above can be written as a \\(K\\)-fold convolution, we now have a new way to write the simplex integral 

$$
\int_{\Delta_K} \prod_{k=1}^K f_k (\theta_k) d \boldsymbol{\theta} = \mathcal{L}^{-1} \left[ \prod_{k=1}^K \mathcal{F}_k(s) \right] (1)
$$

# Application to normalization constants

The trick above is helpful for computing normalization constants of probability densities, whose support is \\(\Delta_k\\). One prominent example of a simplex distribution is the Dirichlet distribution, whose probability density function has kernel

$$
p_\text{Dir} (\boldsymbol{\theta} | \boldsymbol{\alpha}) \propto \prod_{k=1}^K \theta_k^{\alpha_k - 1}
$$

The Laplace transform of the function \\(f(t) = t^a\\) is

$$
\mathcal{L}\left[ f \right](s) = \frac{\Gamma(a+1)}{s^{a+1}}
$$

This means that the integral of the Dirichlet kernel is

$$
\mathcal{L}^{-1} \left[ \frac{\prod_{k=1}^K \Gamma(\alpha_k)}{s^{\sum_{k=1}^K \alpha_k}} \right] (1) = \frac{\prod_{k=1}^K \Gamma(\alpha_k)}{\Gamma\left(\sum_{k=1}^K \alpha_k\right)}
$$

which can be verified by looking at the [Dirichlet distribution Wikipedia page](https://en.wikipedia.org/wiki/Dirichlet_distribution).

# References

Many thanks to this helpful blog post: [Integration of product of functions on a probability simplex](https://memming.wordpress.com/2010/09/09/integration-of-product-of-functions-on-a-probability-simplex/)