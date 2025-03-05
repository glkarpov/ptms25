---
title: "Probability Theory"
subtitle: "Discrete Multivariate Random Variables."
institute: "HSE GSB DPM"
author: "Gleb Karpov"
format: 
    beamer:
        theme: Singapore
        section-titles: false
        incremental: true
        include-in-header: ../../files/header.tex  # Custom LaTeX commands and preamble
        fonttheme: serif
---

## Introduction
### Back to the discrete world

- The same way as we can observe result of two coins flipped simultaneously, we can observe result of more than one random variable at once.
- To describe this experiment we use new concept - _multivariate random variable_ or just _random vector_ :
$$
X = (X_1, X_2, \ldots, X_n)^{\top}, \text{ or in 2-dimensional case } (X, Y)^{\top}.
$$
- Compare it with simple outcome of the form $\omega = ( \text{state}_1, \ldots, \text{state}_n )$, _i.e._ for simultaneous or sequential coin drop:
$$
\omega = \left(h, \, t, \, h, \ldots, t \right).
$$

- They are indeed similar in some sense - but now we want to deal only with numbers. (Recall out initial motivation of inventing random variables.)

## Joint Probability Mass Function

- Our interest is _mutual behaviour_ of those random variables. 
- Are they connected in some sense? Is some value of one variable more frequently accompanied with some other value of the second variable? Finally, can we take out more insights about occuring random experiments, when we take into account interaction of variables with each other?
- To describe this interaction, or mutual behaviour, we use **joint PMF**, _i.e._ :

\begin{center}
\begin{tabular}{c | c c} 
        & \(Y=1\) & \(Y=2\) \\
        \hline
        \(X=1\) & $\frac{1}{8}$ & $\frac{1}{4}$ \\
        \(X=2\) & $\frac{1}{8}$ & $\frac{1}{2}$ \\
    
\end{tabular}
\end{center}

## Joint Probability Mass Function

- To put it generally:
\begin{center}
\begin{tabular}{c | c c c} 
        & $Y=y_1$ & \ldots & $Y=y_m$ \\
        \hline
        $X=x_1$ & $P(\{ X=x_1, Y=y_1 \})$ & \ldots & $P(\{ X=x_1, Y=y_m \})$ \\
        \ldots & \ldots                   & \ldots & \ldots \\
        $X=x_n$ & $P(\{ X=x_n, Y=y_1 \})$ & \ldots & $P(\{ X=x_n, Y=y_m \})$ \\
\end{tabular}
\end{center}

- We can also write $P(\{ X=x_i, Y=y_j \})$ as $P_{X, \, Y} \left(x_i, y_j\right)$



### Properties

- $P_{X, \, Y} \left(x_i, y_j\right) \geq 0$, for all possible $(x_i, \, y_j)$
- Since $P(\Omega) = 1$, here we have $\Omega = \{ (x_1, y_1), (x_1, y_2),\ldots, (x_n, y_m) \}$. From that follows:
$$
        \sum\limits_{i=1}^{n} \sum\limits_{j=1}^{m} P(\{ X=x_i, Y=y_j \}) = 1.
$$

## Marginal PMF

- Suppose we are interested in getting result $X=x_i$, no matter what $Y$ is equal to. That means that all the following pairs are valid, and they form a special event:
$$
        A = \{\text{we obtain } X = x_i\} = \{ (x_i, \, y_1), (x_i, \, y_2), \ldots, (x_i, \, y_m) \}
$$

- If then we want to find the probability of this event:
$$
        P (\{X = x_i\}) = P_{X, \, Y}(x_i, y_1) + P_{X, \, Y}(x_i, y_2) + \ldots + P_{X, \, Y}(x_i,y_m)
$$

- That means that by using joint pmf we can restore the own pmf of some random variable, separately from the random vector.

- Before we called it just **pmf** but now we need to specify, because there are too many different pmf's.

## Marginal PMF

- In a general form:
\begin{gather*}
P (\{X = x_i\}) = \sum\limits_{j=1}^{m} P(\{ X=x_i, Y=y_j \}) = \sum\limits_{j=1}^{m} P_{X, \, Y}(x_i, y_j) \\
P (\{Y = y_j\}) = \sum\limits_{i=1}^{n} P(\{ X=x_i, Y=y_j \}) = \sum\limits_{i=1}^{n} P_{X, \, Y}(x_i, y_j)
\end{gather*}

- In other words, those own mass functions (marginal pmf's) are summations across corresponding row or column in the table of joint distribution:
\begin{center}
\begin{tabular}{c | c c c} 
        & $Y=y_1$ & \ldots & $Y=y_m$ \\
        \hline
        $X=x_1$ & $P(\{ X=x_1, Y=y_1 \})$ & \ldots & $P(\{ X=x_1, Y=y_m \})$ \\
        \ldots & \ldots                   & \ldots & \ldots \\
        $X=x_n$ & $P(\{ X=x_n, Y=y_1 \})$ & \ldots & $P(\{ X=x_n, Y=y_m \})$ \\
\end{tabular}
\end{center}

## Conditional PMF

- In this set up we can also investigate questions of the following form: $P(X = x_i | Y = y_j)$
- We name it yet another pmf - __conditional pmf__
- Recall: conditional probability is sort of parametrized function, where event-condition serves as parameter. Functions $P(X|A)$ and $P(X|B)$, $A \neq B$, are different functions!
- By applying definition of conditional probability:
\begin{gather*}
        P(X = x_i | Y = y_j) = \frac{P(\{X=x_i \} \cap \{ Y=y_j\})}{P(Y=y_j)} = \frac{P(\{ X=x_i, Y=y_j \})}{P(Y=y_j)} \\
        P(Y = y_j| X = x_i) = \frac{P(\{X=x_i \} \cap \{ Y=y_j\})}{P(X=x_i)} = \frac{P(\{ X=x_i, Y=y_j \})}{P(X=x_i)}
\end{gather*}

## Independence
- Finally, there is important talk about the independence of random variables. In a way that is even more important than independence of single events.
- 

## Problems
