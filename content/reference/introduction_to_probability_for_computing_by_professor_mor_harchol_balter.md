---
title: "Introduction to Probability for Computing by Professor Mor Harchol-Balter"
author: ["Krish Matta"]
date: 2024-04-27T00:00:00-07:00
lastmod: 2024-05-07T00:00:00-07:00
tags: ["draft"]
draft: false
---

## Statistical Inference {#statistical-inference}

In probability, we generate data from a probabilistic model. In statistics, we infer a probabilistic model from the data.


### Estimators for Mean and Variance {#estimators-for-mean-and-variance}


#### Point Estimation {#point-estimation}

Point estimation is a type of estimation in which we are trying to recover a single value. For example, say that we sample
\\[
X\_1, X\_2, \dots, X\_n
\\]
which are i.i.d. from some unknown distribution, and we want to estimate the expected value of the distribution---this is point estimation.

****Definition 1 (Estimator)**** We write
\\[
\hat{\theta}(X\_1, X\_2, \dots, X\_n)
\\]
to denote an estimator of the unknown value \\(\theta\\) made from the sampled data \\(X\_1, X\_2, \dots, X\_n\\). Note that \\(\hat{\theta}(X\_1, X\_2, \dots, X\_n)\\) is a random variable, as it is a function of random variables. We write
\\[
\hat{\theta}(X\_1 = k\_1, X\_2 = k\_2, \dots, X\_n = k\_n)
\\]
to denote the constant estimation for \\(\theta\\) made with specific values of the sample data.


#### Sample Mean {#sample-mean}

Certain estimators come up frequently: for example, the mean estimator.

****Definition 2 (Mean estimator)**** Let \\(X\_1, X\_2, \dots, X\_n\\) i.i.d. samples of some unknown random variable \\(X\\). A mean estimator is a point estimator for the value of \\(\theta = \mathbb{E}[X]\\). It is typically defined via
\\[
\hat{\theta}(X\_1, X\_2, \dots, X\_n) = \dfrac{X\_1 + X\_2 + \dots + X\_n}{n}
\\]
and short-handed with \\(\overline{X}\\).


#### Desirable Properties of a Point Estimator {#desirable-properties-of-a-point-estimator}

There are of course many possible estimators of a value \\(\theta\\). Estimators are not equal, however. Here we discuss the desirable properties of an estimator.

****Definition 3 (Unbiased estimator)**** We call
\\[
\hat{\theta}(X\_1, X\_2, \dots, X\_n)
\\]
an unbiased estimator of \\(\theta\\) if \\(\mathbb{E}[\hat{\theta}] = \theta\\).

We want our estimators to have zero bias.

****Definition 4 (Mean squared error)**** The mean squared error (MSE) of an estimator \\(\hat{\theta}(X\_1, X\_2, \dots, X\_n)\\) is defined as \\(MSE(\hat{\theta}) = \mathbb{E}[(\hat{\theta} - \theta)^2]\\).

****Lemma 1**** If \\(\hat{\theta}\\) is an unbiased estimator of \\(\theta\\), then
\\[
Var(\hat{\theta}) = MSE(\hat{\theta}).
\\]

_Proof_

$$

\begin{aligned}
MSE(\hat{\theta}) &= \mathbb{E}\left[(\hat{\theta} - \theta)^2\right] \\\\
&= \mathbb{E}\left[(\hat{\theta} - \mathbb{E}[\hat{\theta}])^2\right] \tag{$\hat{\theta}$ unbiased} \\\\
&= Var(\hat{\theta}).
\end{aligned}

$$

It is also desirable that as our sample size increases, our estimator becomes increasingly accurate. This is referred to as consistency.

****Definition 5 (Consistent estimator)**** Let \\(\hat{\theta}\_1(X\_1), \hat{\theta}\_2(X\_1, X\_2), \dots\\) be a sequence of point estimators for \\(\theta\\) such that \\(\hat{\theta}\_n\\) is a function of \\(n\\) samples. We say that \\(\hat{\theta}\\) is a consistent estimator of \\(\theta\\) if for all \\(\epsilon > 0\\),
\\[
\lim\_{n \rightarrow \infty} P(|\hat{\theta}\_n - \theta| > \epsilon) = 0.
\\]

****Lemma 2**** Let \\(\hat{\theta}\_1(X\_1), \hat{\theta}\_2(X\_1, X\_2), \dots\\) be a sequence of point estimators for \\(\theta\\) such that \\(\hat{\theta}\_n\\) is a function of \\(n\\) samples. If
\\[
\lim\_{n \rightarrow \infty} MSE(\hat{\theta}\_n) = 0,
\\]
then \\(\hat{\theta}\_n\\) is a consistent estimator.

We show that the sample mean estimator is consistent. Define
\\[
\hat{\theta}\_n(X\_1, \dots, X\_n) = \dfrac{X\_1 + \dots + X\_n}{n}.
\\]
It suffices to show that
\\[
\lim\_{n \rightarrow \infty} MSE(\hat{\theta}\_n) = 0.
\\]
Observe that
$$

\begin{aligned}
MSE(\hat{\theta}\_n) &= Var(\hat{\theta}\_n) \tag{$\hat{\theta}\_n$ unbiased} \\\\
&= \dfrac{Var(X)}{n}
\end{aligned}

$$
which goes to 0 as \\(n\\) goes to infinity.


#### An Estimator for Variance {#an-estimator-for-variance}

We wish to find a good estimator for \\(\theta = Var(X)\\). There are two cases: when we know the mean of \\(X\\) and when we don't know the mean.

If we know the mean of \\(X\\), then a natural estimator is
\\[
\hat{\theta}(X\_1, X\_2, \dots, X\_n) = \frac{1}{n} \sum\_{i=1}^n \left( X\_i - \mathbb{E}[X] \right)^2 .
\\]
We can show that this is an unbiased estimator:
$$

\begin{aligned}
\mathbb{E}[\hat{\theta}] &= \dfrac{1}{n} \mathbb{E}\left[ \sum\_{i=1}^n \left( X\_i - \mathbb{E}[X] \right)^2 \right] \\\\
&= \dfrac{1}{n} \sum\_{i=1}^n \mathbb{E}\left[ \left( X\_i - \mathbb{E}[X] \right)^2 \right] \\\\
&= \dfrac{1}{n} \sum\_{i=1}^n Var(X) \\\\
&= Var(X),
\end{aligned}

$$
as desired.

Now assume that we don't know the mean of \\(X\\). Based on the prior result, we may attempt to define our estimator as
\\[
\hat{\theta}(X\_1, X\_2, \dots, X\_n) = \frac{1}{n} \sum\_{i=1}^n \left( X\_i - \overline{X} \right)^2,
\\]
where \\(\overline{X}\\) is the sample mean estimator. Surprisingly, we would find that
\\[
\mathbb{E}\left[\hat{X}\right] = \dfrac{n-1}{n} Var(X),
\\]
i.e. that this is a biased estimator. The fix is simple, as we can scale our estimator:
\\[
\hat{\theta}(X\_1, X\_2, \dots, X\_n) = \frac{1}{n-1} \sum\_{i=1}^n \left( X\_i - \overline{X} \right)^2,
\\]
which is unbiased.
