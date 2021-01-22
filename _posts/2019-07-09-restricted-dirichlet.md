---
layout: post
title: "Sampling from a Dirichlet distribution with quantile constraints"
author: "Jordan Bryan"
categories: journal
tags: [documentation,sample]
image: dirichlet.png
---

The Dirichlet distribution is a multivariate probability distribution over \\(K\\)-vectors whose entries sum to \\(1\\). It is the conjugate prior distribution for random variables with a Multinomial sampling likelihood.

The Dirichlet-Multinomial update may be used to construct finite approximations to the cumulative distribution function (CDF) of any bounded random variable. Let \\(X\\) be a bounded random variable and partition the sample space of \\(X\\) into \\(K\\) intervals \\(I_1, \dots, I_K\\). Next, define 

$$
Y_i = k~\text{when}~X_i \in I_k
$$

Then the model

$$
\begin{aligned}
Y_1, \dots, Y_n &\sim \text{Multinomial}(\theta_1, \dots, \theta_K) \\
\theta &\sim \text{Dirichlet}(\alpha_1, \dots, \alpha_K)
\end{aligned}
$$

yields a posterior density over \\(\theta\\) given by

$$
\text{Dirichlet} \left( \sum_{i=1}^n \mathbb{I}[Y_i = 1] + \alpha_1, \dots, \sum_{i=1}^n \mathbb{I}[Y_i = K] + \alpha_K \right)
$$

which is a coarse approximation to the density function \\(p_X (x)\\).

What if we already know something about the quantiles of \\(X\\)? We might express that knowledge as a set of constraints on the support of \\(\theta\\) that restrict the size of consecutive sums of the entries of \\(\theta\\). Suppose we know that interval \\(I_k\\) contains the \\(u^\text{th}\\) quantile of \\(X\\). Then the constraint may be expressed as

$$
\inf \{ l : \sum_{j=1}^l \theta_j > u \} = k
$$

Here we have to turn to the stick-breaking construction of the Dirichlet distribution, which expresses the Dirichlet as a particular construction of independent Beta random variables. Instead of using the typical construction of Betas, we will use a series of *truncated Beta random variables* to ensure that the support of the restricted Dirichlet adheres to the quantile constraints.

Let \\(b_k\\) and \\(u_k\\) be the least and greatest numbers, respectively, such that 

$$
\inf \{ l : \sum_{j=1}^l \theta_j > u_k \} = k~~\text{and}~~\inf \{ l : \sum_{j=1}^l \theta_j > b_k \} = k
$$

and let \\(S\\) be the length of stick remaining in the stick-breaking process. Then the \\(k^\text{th}\\) Beta sample in the stick-breaking process will be drawn from

$$
\beta_k \sim \text{Beta} \left(\alpha_k, \sum_{k+1}^K \alpha_k \right)
$$

with support limited to the interval

$$
\beta_k \in \left[ \frac{u_k + S - 1}{S}, \frac{b_{k+1} + S - 1}{S} \right]
$$

Does this actually yield a Dirichlet-distributed random variable with truncated support? It seems that the answer is yes. Without truncation, the stick-breaking process leads to the following decomposition of the joint distribution of the Beta-distributed random variables:

$$
p(B_1, \dots, B_K) = p(B_1) \cdot p(B_2 | B_1) \cdot p(B_3 | B_2, B_1) \cdots p(B_{K-1} | B_{K-2}, \dots, B_1)
$$

The first term in this product has the form:

$$
p_{B_1} \propto B_1^{\alpha_1 - 1} (1 - B_1)^{\sum_{j=2}^K \alpha_j}
$$

The product of the first two terms has the form:

$$
\begin{aligned}
p_{B_1, B_2} &\propto B_1^{\alpha_1 - 1} (1 - B_1)^{\sum_{j=2}^K \alpha_j} B_2^{\alpha_2 - 1} (1 - B_2)^{\sum_{j=3}^K \alpha_j}\\
&\propto B_1^{\alpha_1 - 1} \left((1 - B_1)B_2\right)^{\sum_{j=2}^K \alpha_j - 1} \left((1-B_1)(1 - B_2)\right)^{\sum_{j=3}^K \alpha_j - 1} (1- B_1)
\end{aligned}
$$

And so on until the product of the first \\(k\\) terms:

$$
p_{B_1, \dots, B_k} \propto B_1^{\alpha_1 - 1} \left(B_2(1 - B_1)\right)^{\sum_{j=2}^K \alpha_j - 1} \cdots \left(B_k \prod_{j=1}^{k-1} (1 - B_j)\right)^{\sum_{j=k}^K \alpha_j - 1} \left(\prod_{j=1}^{k} (1 - B_j)\right)^{\sum_{j=k+1}^K \alpha_j - 1} \left(\prod_{j=1}^{k-1} (1 - B_j)^{j-1}\right)
$$

Now we make the substitution

$$
\begin{aligned}
\theta_1 &= B_1 \\
\theta_2 &= B_2 (1-B_1) \\
\theta_3 &= B_3 (1-B_2)(1-B_1) \\
&\vdots \\
\theta_k &= \left(B_k \prod_{j=1}^{k-1} (1 - B_j)\right)
\end{aligned}
$$

And the Jacobian of the variable transformation is a lower triangular matrix with diagonal elements

$$
1~, ~1 - \theta_1~, ~(1 - \theta_1)(1 - \theta_2)~, ~\dots~, ~\prod_{j=1}^{k-1} (1 - \theta_j)
$$

whose product -- the determinant of the Jacobian -- yields the normalizing constant that gives back the Dirichlet density.

Truncation changes the procedure above, but only through the addition of an indicator function to each term in the expansion

$$
p(B_1) \cdot p(B_2 | B_1) \cdot p(B_3 | B_2, B_1) \cdots p(B_{K-1} | B_{K-2}, \dots, B_1)
$$

each of the form

$$
\mathbb{I} \left\{ B_k \in \left[ \frac{u_k + \prod_{j=1}^{k-1} (1 - B_j) - 1}{\prod_{j=1}^{k-1} (1 - B_j)}, \frac{b_{k+1} + \prod_{j=1}^{k-1} (1 - B_j) - 1}{\prod_{j=1}^{k-1} (1 - B_j)} \right] \right\}
$$

For each \\(k\\), these indicator functions only depend on the variables \\(B_1, \dots, B_{k-1}\\), mirroring the structure of the decomposition of the joint distribution of the Beta-distributed random variables.