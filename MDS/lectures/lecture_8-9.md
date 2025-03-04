---
title: "Probability Theory"
subtitle: "Continuous Random Variables"
institute: "HSE FCS"
author: "Gleb Karpov"
format: 
    beamer:
        theme: Singapore
        fonmttheme: serif
---

## Fundamental Theorem of Calculus
- **Def.** If function $f(x)$ is continuous on the segment $[a,b]$, and $\Phi(x)$ is any of its antiderivatives on its, then:

$$
    \int \limits_{a}^{b} f(x) dx = \Phi(b) - \Phi(a) = \Phi \vert_{a}^{b}
$$

## Probability Density Function

- By definition: $X$ is a continuous random variable if there exists a nonnegative function $f_X(x)$ defined for $\forall x \in \mathbb{R}$, such that any probability of the form $P(a \leq X \leq b)$ can be found by:

$$
   P(a \leq X \leq b) = \int \limits_{a}^{b} f_X(x) dx  
$$


## Probability Density Function

- By definition: $X$ is a continuous random variable if there exists a nonnegative function $f_X(x)$ defined for $\forall x \in \mathbb{R}$, such that any probability of the form $P(a \leq X \leq b)$ can be found by:

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

- **Def.** CDF of random variable $X$ is a non-decreasing function $F_X(x)$ defined for $\forall x \in \mathbb{R}$, such that:

$$
    F_X(x) = P \{ X \in (-\infty, x) \}
$$

- For CRV we can rewrite it as:

$$
    F_X(x) = P \{ X \in (-\infty, x) \} = \int \limits_{-\infty}^{u} f_X(u) du
$$


## Cumulative Distribution Function

- **Def.** CDF of random variable $X$ is a non-decreasing function $F_X(x)$ defined for $\forall x \in \mathbb{R}$, such that:

$$
    F_X(x) = P \{ X \in (-\infty, x) \}
$$

- For CRV we can rewrite it as:

$$
    F_X(x) = P \{ X \in (-\infty, x) \} = \int \limits_{-\infty}^{u} f_X(u) du
$$

- Basic properties (for self-check also):

$$
    F_X(-\infty) = 0, \quad \quad F_X(\infty) = 1
$$

## CDF as a way to avoid intergration

- Suppose we are interested in $P(a < X < b)$. One way - to compute integral according to the defition of CRV.
- Consider interval $\mathcal{D} = (-\infty, b)$. It can be decoupled in a union of two complementary sets:

$$
    \mathcal{D} = (-\infty, \; a] \cup (a, \; b)
$$

## CDF as a way to avoid intergration

- Suppose we are interested in $P(a < X < b)$. One way - to compute integral according to the defition of CRV.
- Consider interval $\mathcal{D} = (-\infty, b)$. It can be decoupled in a union of two complementary sets:

$$
    \mathcal{D} = (-\infty, \; a] \cup (a, \; b)
$$

- Then according to additivity principle of probability:

$$
    P\{ \mathcal{D} \} = P\{ (-\infty, \; a] \} + P \{ (a, \; b) \}
$$

## CDF as a way to avoid intergration

- Return to the CDF formulation:

$$
    \int \limits_{-\infty}^{b} f_X(u) du = \int \limits_{-\infty}^{a} f_X(u) du  + \int \limits_{a}^{b} f_X(u) du
$$

- And finally:

$$
    \int \limits_{a}^{b} f_X(x) dx = F_X(b) - F_X(a). 
$$


## Examples

- A random variable $X$ has density function:

$$
    \begin{cases}
        2x, & 0 < x < 1 \\
        0, & \text{otherwise}
    \end{cases}
$$

Check that it is valid and find the cumulative distribution function of $X$.

## Examples

## Examples

Find the constant $c$ such that $f_X(x)$ is a valid p.d.f of a random variable $X$, find the cumulative distribution function, $F_X(x)$, and find a __median__ of the density function:

- $f(x) = \frac{x^3}{4}$, $0 < x < c$
- $f(x) = \frac{3x^2}{16}$, $-c < x < c$

## Examples
