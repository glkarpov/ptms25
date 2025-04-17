---
title: "Mathematical Statistics"
subtitle: "Intro to Statistics. Sampling Distribution."
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
- $E[a] = a$, $Var[a] = 0$.

## Recall: The Central Limit Theorem
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

## Recall: The Central Limit Theorem
### Straight ahead philosophical formulation

- **Central Limit Theorem**: distribution of such random variable $S_n$ tends to normal distribution as $n \rightarrow \infty$: 
$$
S_n  \rightarrow  Y \sim \mathcal{N}(n \mu, n \sigma^2).
$$

- To put simply: we can just say that $S_n \sim \mathcal{N}(n \mu, n \sigma^2)$, when $n$ is sufficiently large.

- Another formulation: distribution of \textit{standardized} $S_n$ tends to standard normal distribution as $n \rightarrow \infty$:
$$
Z_n = \frac{S_n - E[S_n]}{\sqrt{Var[S_n]}}, \quad Z_n  \rightarrow  Z \sim \mathcal{N}(0, 1).
$$

## Recall: function of two discrete RVs

Let us assume that we throw two $6$-sided dices, in any sense independent from each other. We then observe discrete random vector $(X,Y)$, where $X$ and $Y$ are random variables corresponding to resulting numbers on each of the dices.
So far as there are $36$ distinct pairs, we have joint PMF given as: $P(X=x_i, \, Y=y_j) = \frac{1}{36}$.

Let's introduce new random variable $T$ being a function from $X$ and $Y$: $T = f(X,Y) = X + Y$.
\begin{enumerate}
    \item Construct PMF for the random variable $T$.
\end{enumerate}

## Recall: function of two discrete RVs

\begin{flushleft}
    \begin{tabular}{c | c | c | c | c |c | c | c | c |c | c | c | } 
    T & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 & 10 & 11 & 12 \\
    \hline
    $P_T$ & $\frac{1}{36}$ & $\frac{2}{36}$ & $\frac{3}{36}$ & $\frac{4}{36}$ & $\frac{5}{36}$ & $\frac{6}{36}$ & $\frac{5}{36}$ & $\frac{4}{36}$ & $\frac{3}{36}$ & $\frac{2}{36}$ & $\frac{1}{36}$
\end{tabular}
\end{flushleft}

## Statistics intro: example

## Statistics intro: example

- Simply put: we want to decipher a black box and find out, for example, the distribution of an unknown random variable. To do this, we want to observe it a certain number of times and make some judgment based on the accumulated information.

## What Does Statistics Study?

Statistics is a set of procedures and principles for collecting and analyzing information to make decisions in conditions of uncertainty.

- In probability theory, we go from assuming a model to the probability of a specific outcome, _i.e._ from general to specific. In statistics, tasks are solved almost entirely in reverse. Statistics investigates a relatively small specific outcome, and the goal is to learn something about the global properties of a random experiment.
- Thus, despite the close connection between these two things - probability and statistics - a clear distinction is evident between them.


## Random Sample and Its Realization

- Collected data is usually called a sample, but in statistics, we simultaneously deal with two different types of samples.
- A random sample is a vector (set, collection) of i.i.d. (independent & identically distributed) random variables:
$$
    \mathcal{X} = (X_1, \, X_2, \, \ldots, X_n), \quad f_{X_i}(x) = f_{X_j}(x), \; \forall i,j \in [1, \, n], \, \forall x.
$$
- The realization of a random sample is a set of observations from the random sample $\mathcal{X}$, a set of specific numbers:
$$
    \mathcal{x} = (x_1 \, x_2, \, \ldots, x_n).
$$

- Words we often use:
    - Population - the complete set of objects possessing the characteristic of interest, carrying the realization of the random variable of interest.
    - Statistic - any function that depends _only_ on the variables of the random sample, i.e., $f = f(X_1, \ldots, X_n)$.

## Statistics as Random Variables

- Each statistic can take a different value for a new realization $(x_1^{(2)}, \ldots , x_n^{(2)})$ of a random sample compared to the previous sample.
- Therefore, we can consider statistics as random variables! As random variables, they have their own distributions and characteristics. The probability distribution of the statistic $Y = f(X_1, \ldots, X_n)$ is called the sampling distribution for $Y$.

## Sampling Distributions

- Let $\mathcal{X} = (X_1, \ldots, X_n)$ be a random sample with mean $E_[X_i] = \mu$ and variance $Var[X_I] = \sigma^2 < \infty$.

- Possible statistic is just already covered sum of all elements $S_n = \sum \limits_{i=1}^{n} X_i$. Its characteristics are:
- $E[S_n] = n \mu$, $Var[S_n] = n \sigma^2$

- One of the most important statistics is the sample mean:
$$
    \bar{X} = \frac{X_1+ \ldots + X_n}{n} = \frac{1}{n}\sum\limits_{i=1}^{n} X_i
$$

- Characteristics of the sample mean $\bar{X}$:
    - $E[\bar{X}] = \mu$
    - $\text{Var} (\bar{X}) = \frac{\sigma^2}{n}$.
