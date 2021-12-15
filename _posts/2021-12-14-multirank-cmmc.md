---
layout: post
title: "The multirank likelihood and cyclically monotone Monte Carlo"
author: "Jordan Bryan"
categories: journal
tags: [documentation,sample]
image: cmmc.png
---

New joint work with [Peter Hoff](https://pdhoff.github.io)  and [Jonathan Niles-Weed](https://www.jonathannilesweed.com) is out today. Find the abstract below and read more on [arXiv.org](https://arxiv.org/abs/2112.07465).

**Abstract:**

Many analyses of multivariate data are focused on evaluating the dependence between two sets of variables, rather than the dependence among individual variables within each set. Canonical correlation analysis (CCA) is a classical data analysis technique that estimates parameters describing the dependence between such sets. However, inference procedures based on traditional CCA rely on the assumption that all variables are jointly normally distributed. We present a semiparametric approach to CCA in which the multivariate margins of each variable set may be arbitrary, but the dependence between variable sets is described by a parametric model that provides a low-dimensional summary of dependence. While maximum likelihood estimation in the proposed model is intractable, we develop a novel MCMC algorithm called cyclically monotone Monte Carlo (CMMC) that provides estimates and confidence regions for the between-set dependence parameters. This algorithm is based on a multirank likelihood function, which uses only part of the information in the observed data in exchange for being free of assumptions about the multivariate margins. We illustrate the proposed inference procedure on nutrient data from the USDA.