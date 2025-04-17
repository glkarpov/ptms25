---
title: "Probability Theory"
subtitle: "Central Limit Theorem."
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
    \item Find $E[T]$ without construction of PMF for $T$.
    \item Construct PMF for the random variable $T$.
    \item Repeat previous steps for $G = \frac{X+Y}{2}$.
    \item Find probability $P(3 < T \leq 8)$.
\end{enumerate}

## Recall: function of two discrete RVs
\vspace{-6.5em}
### Example 1.

## The Central Limit Theorem
### Prerequisites

- Let $X_1, \ldots, X_n$ be a sequence of independent random variables taken from the **same** distribution, i.e. all $X_i$'s have the same expectation $\mu$ and finite variance $\sigma^2$. 

- We construct **new** random variable:
$$
S_n = \sum \limits_{i=1}^{n} X_i.
$$

- According to the properties of expectation and variance, properties of the new random variable are:
\begin{gather*}
    E[S_n] = E \Bigl[ \sum \limits_{i=1}^{n} X_i \Bigr] = \sum \limits_{i=1}^{n} E[X_i] = n \mu \\
    Var[S_n] = Var \Bigl[ \sum \limits_{i=1}^{n} X_i \Bigr] = \sum \limits_{i=1}^{n} Var[X_i] = n \sigma^2
\end{gather*}

## The Central Limit Theorem
### Straight ahead philosophical formulation

- **Central Limit Theorem**: distribution of such random variable $S_n$ tends to normal distribution as $n \rightarrow \infty$: 
$$
S_n  \rightarrow  Y \sim \mathcal{N}(n \mu, n \sigma^2).
$$

- More specifically formulated:
$$
  \forall x \in \mathbb{R} \quad  P(S_n < x) \underset{n \rightarrow \infty}{\longrightarrow} P(Y < x), \text{ where } Y \sim \mathcal{N}(n \mu, n \sigma^2).
$$

- To put simply: we can just say that $S_n \sim \mathcal{N}(n \mu, n \sigma^2)$, when $n$ is sufficiently large.

## The Central Limit Theorem

- Let $X_1, \, X_2, \, \ldots$ be independent and identically distributed random variables, each with mean $\mu$ and non-zero variance $\sigma^2$.

- The standardized version $Z_n$ of the sum $S_n = \sum\limits_{i=1}^{n} X_i$ satisfies:
$$
    P(Z_n \leq x) \underset{n \rightarrow \infty}{\longrightarrow} \int\limits_{-\infty}^{x} \frac{1}{\sqrt{2 \pi}} e^{-\frac{1}{2}u^2} du \quad \forall x \in \mathbb{R}
$$
