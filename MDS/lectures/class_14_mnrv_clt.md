---
title: "Probability Theory"
subtitle: "Multivariate Normal Random Variables. \n Central Limit Theorem."
institute: "HSE FCS MDS"
author: "Gleb Karpov"
format: 
    beamer:
        theme: Singapore
        section-titles: false
        incremental: true
        include-in-header: ../../files/header.tex  # Custom LaTeX commands and preamble
        fonttheme: serif
---

## Recall: Linear combination of RVs

Suppose we have $X$ and $Y$ - two random variables. The following properties work for *any* possible nature of these variables.

- Linear property of the expectation: $E[aX \pm bY] = a E[X] \pm b E[Y]$.
- Variance of the linear combination: $Var[aX \pm bY] = a^2 Var[X] + b^2 Var[Y] \pm 2ab(E[XY] - E[X]E[Y])$.
- If $X$ and $Y$ are independent: $Var[aX \pm bY] = a^2 Var[X] + b^2 Var[Y]$.

## Recall: function of two discrete RVs
### Example 1.

Let us assume that we throw two $6$-sided dices, in any sense independent from each other. We then observe discrete random vector $(X,Y)$, where $X$ and $Y$ are random variables corresponding to resulting numbers on each of the dices.
So far as there are $36$ distinct pairs, we have joint PMF given as: $P(X=x_i, \, Y=y_j) = \frac{1}{36}$.

Let's introduce new random variable $T$ being a function from $X$ and $Y$: $T = f(X,Y) = X + Y$.
\begin{enumerate}
    \item Find $E[T]$ and $Var[T]$ without construction of PMF for $T$.
    \item Construct PMF for the random variable $T$.
    \item Find probability $P(3 < T \leq 8)$.
\end{enumerate}

## Recall: function of two discrete RVs
\vspace{-6.5em}
### Example 1.

## Multivariate Normal Random Variables


## Illustrative problems
### Example 2.

A machine filling cans supplies, to each can, a volume $X$ of fruit and a volume $Y$ of juice. It is known that $X$ has a normal distribution with mean $260$ and a standard deviation of $17$, whereas $Y$ has a normal distribution with mean $150$ and a standard deviation of $10$. These variables may be regarded as independent. 

\begin{enumerate}
    \item Calculate the probability that the volume of fruit supplied is greater than $290$ units.
    \item Find the probability that the volume of fruit supplied is more than twice the amount of juice.
    \item If the capacity of a particular can is $400$, what is the probability of the can being under-filled?
\end{enumerate}

## Illustrative problems
\vspace{-6.5em}
### Example 2.

## The Central Limit Theorem
### Convergence in probability 

- The sequence $X_1$, $X_2$, \ldots of random variables **converges in probability** to $X$ as $n \rightarrow \infty$ if:
$$
    \forall \varepsilon > 0: \quad P \bigl( |X - X_n| > \varepsilon \bigr) \rightarrow 0 \text{ as } n \rightarrow \infty
$$

## The Central Limit Theorem

- Let $X_1, \, X_2, \, \ldots$ be independent and identically distributed random variables, each with mean $\mu$ and non-zero variance $\sigma^2$.
- Introduce new random variable $S_n = \sum\limits_{i=1}^{n} X_i$.
- Expectation of $S_n$: $E[S_n] = E \Bigl[ \sum\limits_{i=1}^{n} X_i \Bigr] = \sum\limits_{i=1}^{n} E[X_i] = n \mu$.
- Variance of $S_n$: $Var[S_n] = Var \Bigl[ \sum\limits_{i=1}^{n} X_i \Bigr] = \sum\limits_{i=1}^{n} Var[X_i] = n \sigma^2$.
- Standardized variable: $Z_n = \frac{S_n - E[S_n]}{\sqrt{Var[S_n]}} = \frac{S_n - n \mu}{\sigma \sqrt{n}}$.
- $E[Z_n] = E \Bigl[\frac{S_n}{\sigma \sqrt{n}} \Bigl] - E \Bigl[\frac{n \mu}{\sigma \sqrt{n}} \Bigr] = \frac{S_n}{\sigma \sqrt{n}} - \frac{S_n}{\sigma \sqrt{n}} = 0$.
- $Var[Z_n] = Var \Bigl[\frac{S_n}{\sigma \sqrt{n}} \Bigl] + Var \Bigl[\frac{n \mu}{\sigma \sqrt{n}} \Bigr] = \frac{Var[S_n]}{n \sigma^2} + 0 = 1$.

## The Central Limit Theorem

- Let $X_1, \, X_2, \, \ldots$ be independent and identically distributed random variables, each with mean $\mu$ and non-zero variance $\sigma^2$.

- The standardized version $Z_n$ of the sum $S_n = \sum\limits_{i=1}^{n} X_i$ satisfies:
$$
    P(Z_n \leq x) \underset{n \rightarrow \infty}{\longrightarrow} \int\limits_{-\infty}^{x} \frac{1}{\sqrt{2 \pi}} e^{-\frac{1}{2}u^2} du \quad \forall x \in \mathbb{R}
$$

## Additional slide
