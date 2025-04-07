---
title: "Probability Theory"
subtitle: "Discrete Multivariate Random Variables."
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
- Recall. Independence of a pair events:
\begin{gather*}
P(A) = P(A|B), \quad P(B) = P(B|A) \\
P(A) = P(A|B) = \frac{P(A \cap B)}{P(B)} \rightarrow P(A \cap B) = P(A)P(B).
\end{gather*}

## Independence

- Consider every possible pair of the following events:

\begin{columns}
\column{.5\textwidth}
\begin{itemize}
    \item $\{ X=x_1 \}$ \tikzmark{x_1}
    \item $\{ X=x_2 \}$
    \item \ldots
    \item $\{ X=x_n \}$ \tikzmark{x_n}
\end{itemize}

\column{.5\textwidth}
\begin{itemize}
    \item \tikzmark{y_1} $\{ Y=y_1 \}$ 
    \item \tikzmark{y_2} $\{ Y=y_2 \}$
    \item \ldots
    \item \tikzmark{y_m} $\{ Y=y_m \}$
\end{itemize}
\end{columns}

\begin{tikzpicture}[overlay,remember picture]
\draw[red!25, very thick, Stealth-Stealth]         ($({pic cs:x_1})+(1ex,1ex)$)
    to [left, ""]  ($({pic cs:y_1})+(-2ex,1ex)$);
\draw[red!25, very thick, Stealth-Stealth]         ($({pic cs:x_1})+(1ex,1ex)$)
    to [left, ""]  ($({pic cs:y_2})+(-2ex,1ex)$);
\draw[red!25, very thick, Stealth-Stealth]         ($({pic cs:x_1})+(1ex,1ex)$)
    to [left, ""]  ($({pic cs:y_m})+(-2ex,1ex)$);
\draw[green!25, very thick, Stealth-Stealth]         ($({pic cs:x_n})+(1ex,1ex)$)
    to [left, ""]  ($({pic cs:y_1})+(-2ex,1ex)$);
\draw[green!25, very thick, Stealth-Stealth]         ($({pic cs:x_n})+(1ex,1ex)$)
    to [left, ""]  ($({pic cs:y_2})+(-2ex,1ex)$);
\draw[green!25, very thick, Stealth-Stealth]         ($({pic cs:x_n})+(1ex,1ex)$)
    to [left, ""]  ($({pic cs:y_m})+(-2ex,1ex)$);
\end{tikzpicture}

- If each pair turns to be independent events, then we say that random variables $X$ and $Y$ are independent.

-
\begin{multline*}
    \forall x_i, \; \forall y_j: \; P\{ X=x_i \}P\{ Y = y_j \} = P(\{X=x_i \} \cap \{ Y=y_j\}) \\ = P(\{ X=x_i, Y=y_j \}).
\end{multline*}

## Problems

The joint probability mass function of $X$ and $Y$ is given by:

\begin{center}
        \begin{tabular}{c | c c}
    & \(Y=1\) & \(Y=2\) \\
    \hline
    \(X=1\) & $\frac{1}{8}$ & $\frac{1}{4}$ \\
    \(X=2\) & $\frac{1}{8}$ & $\frac{1}{2}$ \\

    \end{tabular}
\end{center}

\begin{enumerate}
    \item Find marginal Probability Mass Functions for each random variable.
    \item Compute the conditional mass function of $X$ given $Y = i$, $i = 1, 2$.
    \item Are $X$ and $Y$ independent?
    \item Compute $P\{XY \leq 3\}$, $P\{ X + Y > 2 \}$, $P \{ \frac{X}{Y} > 1 \}$.
\end{enumerate}

## Problems

## Problems

 We are given a joint PMF of the random vector \((X,Y)^{\top}\):

\begin{center}
        \begin{tabular}{c | c c c c}
    & \(Y=0\) & \(Y=1\) & \(Y=2\) & \(Y=3\) \\
    \hline
    \(X=-1\) & \(0.02\) & \(0.03\) & \(0.09\) & \(0.01\) \\
    \(X=0\) & \(0.04\) & \(0.2\) & \(0.16\) & \(0.1\) \\
    \(X=1\) & \(0.05\) & \(0.1\) & \(0.15\) & \(0.05\) \\
    \end{tabular}
\end{center}

Find:

\begin{itemize}
\item
  marginal PMFs for each random variable,
\item
  check whether they are independent,
\item
  conditional PMF of \(X\) given that \(Y = 2\), and conditional PMF of
  \(Y\) given that \(X = 1\),
\item
  probability \(P[Y > X]\).
\end{itemize}

## Problems
