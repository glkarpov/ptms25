---
title: "Probability Theory"
subtitle: "Discrete Multivariate Random Variables."
institute: "HSE GSB IB"
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

- That means that by using joint pmf we can restore the own pmf of a single random variable, separately from the random vector.

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
    \forall x_i, \; \forall y_j: \; P\{ X=x_1 \}P\{ X=x_1 \} = P(\{X=x_i \} \cap \{ Y=y_j\}) \\ = P(\{ X=x_i, Y=y_j \}).
\end{multline*}

## Functions from random vectors

- We discussed the idea that a function from a random variable is a random variable itself, _i.e._ $W = g(X)$.
- Function can be of more than one variable, and we can get now $W = f(X,Y)$.
- As in the 1-variable case we may want to predict $E[W] = E[f(X,Y)]$. 
- Recall:
    \begin{align*}
    E[X] & = \sum \limits_{i=1}^{n} x_i P(X = x_i) \\
    E[g(X)] & = \sum \limits_{i=1}^{n} g(x_i) P(X = x_i)
    \end{align*}
- In the new case:
$$
    E[g(X,Y)] = \sum \limits_{i=1}^{n} \sum \limits_{j=1}^{m} g(x_i, y_j) P(X = x_i, Y = y_j)
$$

## Example
The joint probability mass function of $X$ and $Y$ is given by:

\begin{center}
    \begin{tabular}{c | c c} 
    & \(Y=1\) & \(Y=2\) \\
    \hline
    \(X=1\) & $\frac{1}{8}$ & $\frac{1}{4}$ \\
    \(X=2\) & $\frac{1}{8}$ & $\frac{1}{2}$ \\
    \end{tabular}
\end{center}

Consider functions $W = XY$,  $G = X-Y$. Find their PMF, and expectations.

## Example

## Summation of random variables

- Often it is important to analyze the behaviour of the sum of two or more random variables
- Basically we want to understand how variable $T = aX \pm bY$ behaves, what are its characteristics.
- Linear property of the expectation: $E[aX \pm bY] = a E[X] \pm b E[Y]$.
\begin{multline*}
    E[T] = \sum \limits_{i=1}^{n} \sum \limits_{j=1}^{m} (a x_i \pm b y_j) P(X = x_i, Y = y_j) = \\ a \sum \limits_{i=1}^{n} \sum \limits_{j=1}^{m} x_i P(X = x_i, Y = y_j)  \pm b \sum \limits_{i=1}^{n} \sum \limits_{j=1}^{m} y_j P(X = x_i, Y = y_j) = \\
    a \sum \limits_{i=1}^{n} x_i \sum \limits_{j=1}^{m} P(X = x_i, Y = y_j)  \pm b \sum \limits_{j=1}^{m} y_j \sum \limits_{i=1}^{n} P(X = x_i, Y = y_j) = \\
    = a \sum \limits_{i=1}^{n} x_i P(X=x_i) \pm b \sum \limits_{j=1}^{m} y_j P(Y=y_j) = a E[X] \pm b E[Y]
\end{multline*}

## Summation of random variables
### But variance is another story...

- We are interested in $Var[T]$ which is $Var[aX \pm bY]$. 

- Let's straightforwardly apply the shortcut formula for the variance:
\begin{multline*}
    Var[T] = E[T^2] - (E[T])^2 = E[(aX \pm bY)^2] - (aE[X] \pm bE[Y])^2 \\
    = a^2 E[X^2] \pm 2abE[XY] + b^2 E[Y^2] - (aE[X])^2 \mp 2abE[X]E[Y] - (bE[Y])^2 \\
    = a^2 Var[X] + b^2 Var[Y] \pm 2(E[XY] - E[X]E[Y]) 
\end{multline*}

- Term $E[XY] - E[X]E[Y]$ is called the _covariance_ of $X$ and $Y$.
- In some sense it is a marker of dependency between $X$ and $Y$

## Covariance and independence

- Statement: If $X$ and $Y$ are independent random variables, then $E[XY] = E[X]E[Y]$

- Backward statement is not true!

## Correlation

- Covariance is not a good measure of dependency since it depends of scales of $X$ and $Y$.
- Idea: to normalize covariance and get rid of scales.
- Correlation:
$$
    Corr(X,Y) = \frac{Cov(X,Y)}{\sqrt{Var[X]Var[Y]}}
$$

- It is strictly bounded from $-1$ to $1$ and:
\begin{align*}
    Corr(X,Y) = 1 & \leftrightarrow Y = kX + b, \; k > 0 \\
    Corr(X,Y) = -1 & \leftrightarrow Y = -kX + b, \; k > 0
\end{align*}

- Important: If variables are independent, then their covariance (and correlation) equals to zero. Backward statement IS NOT True.

## Illustrative problems
### Example 1.

\begin{center}
    \begin{tabular}{c | c c} 
    & \(Y=3\) & \(Y=-3\) \\
    \hline
    \(X=-1\) & $\frac{3}{4}$ & $0$ \\
    \(X=2\) & $0$ & $\frac{1}{4}$ \\
\end{tabular}
\end{center}

\begin{enumerate}
    \item Compute marginal PMF for $X$ and $Y$.
    \item Are $X$ and $Y$ independent?
    \item Find covariance and correlation between $X$ and $Y$.
\end{enumerate}

## Illustrative problems

## Illustrative problems
### Example 2

\begin{center}
\begin{tabular}{c | c c c c} 
   $U$ & $u_1=0$ & $u_2 = \pi/3$ & $\ldots$ & $u_{6} = 5 \pi/3$ \\
   \hline
   $P_U$ &  $\frac{1}{6}$  &   $\ldots$  & $\ldots$ & $\frac{1}{6}$ \\
   \hline     
\end{tabular}
\end{center}

\begin{enumerate}
        \item Let's introduce variables $X = \cos{U}$, and $Y = \sin{U}$. Can we write down their joint distribution?
        \item Are they dependent? Consider for example $P(X = 1/2)$ and $P(X = 1/2 \; | \; Y = \sqrt{3}/2)$.
        \item What we can say about $E[X]$ and $E[Y]$?
        \item Find covariance and correlation between $X$ and $Y$.
\end{enumerate}

## Illustrative problems

## Illustrative problems
### Example 3

We have a joint PMF of random vector \((X,Y)^{\top}\) given in the following form:

\begin{center}
    \begin{tabular}{c | c c c} 
    & \(Y=-2\) & \(Y=0\) & \(Y=3\) \\
    \hline
    \(X=-2\) & \(0.15\) & \(0.15\) & \(c\) \\
    \(X=1\) & \(0.05\) & \(0.2\) & \(0.15\) \\
    \end{tabular}
\end{center}


\begin{itemize}
\item
    Find covariance \(\text{Cov}(X,Y)\),
\item
    Find the correlation coefficient,
\item
    Find the probabilities \(P\{ X=-2, Y < 0  \}\), \(P\{Y > -1 \}\), \(P\{Y > X \}\).
    \item Consider new random variable $T = X^2 - Y$, find its PMF.
\end{itemize}

## Illustrative problems

## Illustrative problems
### Example 4

Suppose that $X$ has distribution given by:

$$
    P\{X = -1 \} = P\{X = 0 \} = P\{ X = 1 \} = \frac{1}{3},
$$

and $Y$ is given by:

$$
    P \{  Y=0 \, | \, X=0 \} = P \{  Y=1 \, | \, X=1 \} = P \{  Y=1 \, | \, X=-1 \} = 1 
$$

Check whether $X$ and $Y$ are independent. Find covariance between $X$ and $Y$.

## Illustrative problems
