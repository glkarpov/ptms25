---
title: "Probability Theory"
subtitle: "Continuous Random Variables. Normal distribution."
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

## Recap:

- **Def.** We call $X$ a continuous random variable if there exists a nonnegative function $f_X(x)$ defined for $\forall x \in \mathbb{R}$, such that any probability of the form $P(a \leq X \leq b)$ can be found by:
$$
   P(a \leq X \leq b) = \int \limits_{a}^{b} f_X(x) dx  
$$


- Normalisation property. Since $P(\Omega_X)$ should be equal to $1$, here we have:
$$ 
    1 = P \{ X \in (-\infty, +\infty) \} = \int \limits_{-\infty}^{+\infty} f_X(x) dx
$$

## Cumulative Distribution Function

- **Def.** CDF of random variable $X$ is a non-decreasing function $F_X(x)$ defined for $\forall x \in \mathbb{R}$, such that:

$$
    F_X(x) = P \{ X \in (-\infty, x) \}
$$

## Cumulative Distribution Function

- **Def.** CDF of random variable $X$ is a non-decreasing function $F_X(t)$ defined for $\forall t \in \mathbb{R}$, such that:

$$
    F_X(t) = P \{ X \in (-\infty, t) \}
$$

- For CRV we can rewrite it as:
$$
    F_X(t) = P \{ X \in (-\infty, t) \} = \int \limits_{-\infty}^{t} f_X(x) dx
$$

- Basic properties:
$$
    F_X(-\infty) = 0, \quad \quad F_X(\infty) = 1
$$


## CDF as a way to avoid integration

- Suppose we are interested in $P(a < X < b)$.
- Consider interval $\mathcal{D} = (-\infty, b)$. It can be decoupled in a union of two complementary sets: $\mathcal{D} = (-\infty, \; a] \cup (a, \; b)$.

- According to the additivity principle of probability:
$$
    P\{ X \in \mathcal{D} \} = P\{ X \in (-\infty, \; a] \} + P \{ X \in (a, \; b) \}
$$

- In the intergal formulation:
$$
    \int \limits_{-\infty}^{b} f_X(x) dx = \int \limits_{-\infty}^{a} f_X(x) dx  + \int \limits_{a}^{b} f_X(x) dx
$$

- Finally:
$$
    \int \limits_{a}^{b} f_X(x) dx = F_X(b) - F_X(a). 
$$


## Expectation of the CRV

- Continuous RV also have their expectation and variance (wow!).
- Recall that in DRV we compute expectation as a 'weighted sum':
$$
    E[X] = \sum \limits_{i=1}^{n} x_i P(X = x_i), \text { computed for } \forall x_i \in \Omega_X.
$$

- If we have another RV $G$ being a function from $X$: $G = g(X)$:
$$
    E[g(X)] = \sum \limits_{i=1}^{n} g(x_i) P(X = x_i)
$$

## Expectation

- For the continuous case we just change the sum to the integral:
\begin{align*}
    \sum \limits_{i=1}^{n} x_i P(X = x_i) \Rightarrow \int \limits_{-\infty}^{+\infty} x f_X(x) dx \\
    \sum \limits_{i=1}^{n} g(x_i) P(X = x_i) \Rightarrow \int \limits_{-\infty}^{+\infty} g(x) f_X(x) dx
\end{align*}

- Finally:
\begin{align*}
E[X] & = \int \limits_{-\infty}^{+\infty} x f_X(x) dx \\
E[g(X)] & = \int \limits_{-\infty}^{+\infty} g(x) f_X(x) dx
\end{align*}

## Variance
- Formula for the variance is the same:
$$
    Var[X] = E \left[ (X - E[X])^2 \right] = E[X^2] - (E[X])^2
$$

- Proof recall:
\begin{multline*}
    Var[X] = E \left[ (X - E[X])^2 \right] = E[X^2 - 2 X E[X] + (E[X])^2] =  \\
    E[X^2] - 2 E[X] E[X] + (E[X])^2 = E[X^2] - (E[X])^2.
\end{multline*}

## Example

The random variable $X$ has density function

$$
    f_X(x) = 
    \begin{cases}
    \frac{c}{x^2}, \quad 1 \leq x \leq 5 \\
    0, \quad \text{otherwise}
    \end{cases}
$$ 

\begin{enumerate}
    \item Determine a valid constant $c$,
    \item Find CDF of $X$.
    \item Find $E[X]$, $E[X \ln X]$.
    \item Find $Var[X]$.
\end{enumerate}

## Example

## Example 
![Influence of $\sigma$ parameter](pdf_cdf_example.pdf){#fig-pdf_cdf_example}

## Normal distribution

- Fundamental and extremely useful
- Probability Density Function is parametrized by two constants $\mu$ and $\sigma^2$ and is written as:
$$
    f_X(x) = \frac{1}{\sqrt{2 \pi} \sigma^2} e^{-\frac{(x - \mu)^2}{2\sigma^2}}, \; \forall x \in \mathbb{R}
$$

- Parameters influence the behaviour of the normal random variable. To emphasize the specific normal variable we write:
$$
    X \sim \mathcal{N} \, (\mu, \sigma^2)
$$

- By rather funny **coincidence** we have:
$$
    E[X] = \mu, \; Var[X] = \sigma^2
$$

## Influence of parameters to normal PDF

![Influence of $\mu$ parameter](mu_influence_normal.pdf){#fig-mu}

## Influence of parameters to normal PDF

![Influence of $\sigma$ parameter](sigma_influence_normal.pdf){#fig-sigma}

## Influence of parameters to normal PDF

![Influence of $\sigma$ parameter](sigma_area_diff.pdf){#fig-sigma-diff}

## Standard Normal Variable
### One distribution ~~ring~~ to rule them all

- As long as there are infinite number of pairs $(\mu, \sigma^2)$ there are also infinite number of different normal distributions.
- It would have required to calculate dozens of complicated probability integrals each time.
- What if calculation of probability of **any** normal RV could be reduced to knowledge of just one variable?

## Standard Normal Variable
### One distribution ~~ring~~ to rule them all

- Meet Standard Normal Variable:
$$
    Z \sim \mathcal{N} \, (0,1), \quad f_Z(x) = \frac{1}{\sqrt{2 \pi}} e^{-\frac{x^2}{2}}, \; \forall x \in \mathbb{R}
$$

- Long ago mathematicians calculated dozens of probability integrals and created *Standard normal table*, which shows CDFs $F_Z(x)$ for many possible values of $x$.
- We can find any probability of any Normal random variable by transforming it to the Standard Normal.

## Standard Normal Variable
### Transformation formula

- Let $X$ be Normal random variable and $X \sim \mathcal{N} \, (\mu, \sigma^2)$.
- Then the following function (transformation) transforms $X$ to the Standard Normal variable:
$$
    Z = \frac{X - \mu}{\sigma}
$$
![Transformation to the Standard Normal](x2z_transform.pdf){#fig-x2z}

## Standard Normal Variable

- Let $X$ be Normal random variable and $X \sim \mathcal{N} \, (\mu, \sigma^2)$.
- We are interested in some probability $P(a < X < b)$, $\forall a, \, b: a \leq b$.
- Apply transformation to each part of the inequlaity in order not to break it:
\begin{multline*}
    P(a < X < b) = P \left( \frac{a - \mu}{\sigma} < \frac{X - \mu}{\sigma} < \frac{b - \mu}{\sigma}  \right) = \\
    P \left( \tilde{a} < Z < \tilde{b} \right) = F_Z(\tilde{b}) - F_Z(\tilde{a}).
\end{multline*}

## Standard Normal Variable

![Calculation of probability using CDF](normal_cdf_diff.pdf){#fig-normal_cdf_diff}

## Standard Normal Variable
![Standard normal table](normal_distr_table.pdf){#fig-normal_table}


## Problems
