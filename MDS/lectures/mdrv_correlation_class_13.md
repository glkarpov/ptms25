---
title: "Probability Theory"
subtitle: "Discrete Multivariate Random Variables. \n Covariance and Correlation."
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

## Recall: Conditional PMF

- In this set up we can also investigate questions of the following form: $P(X = x_i | Y = y_j)$
- We name it yet another pmf - __conditional pmf__
- Recall: conditional probability is sort of parametrized function, where event-condition serves as parameter. Functions $P(X|A)$ and $P(X|B)$, $A \neq B$, are different functions!
- By applying definition of conditional probability:
\begin{gather*}
        P(X = x_i | Y = y_j) = \frac{P(\{X=x_i \} \cap \{ Y=y_j\})}{P(Y=y_j)} = \frac{P(\{ X=x_i, Y=y_j \})}{P(Y=y_j)} \\
        P(Y = y_j| X = x_i) = \frac{P(\{X=x_i \} \cap \{ Y=y_j\})}{P(X=x_i)} = \frac{P(\{ X=x_i, Y=y_j \})}{P(X=x_i)}
\end{gather*}

## Recall: Independence

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
    \forall x_i, \; \forall y_j: \; P\{ X=x_i \}P\{ Y = y_j \} = P(\{X=x_i \} \cap \{ Y=y_j\}) \\ = P(\{ X = x_i, Y = y_j \}).
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
    = a^2 Var[X] + b^2 Var[Y] \pm 2ab(E[XY] - E[X]E[Y]) 
\end{multline*}

- Term $E[XY] - E[X]E[Y]$ is called the _covariance_ of $X$ and $Y$.
- In some sense it is a marker of dependency between $X$ and $Y$

## Covariance and independence

- Statement: If $X$ and $Y$ are independent random variables, then $E[XY] = E[X]E[Y]$

- Proof:
\begin{multline*}
    E[XY] = \sum \limits_{i=1}^{n} \sum \limits_{j=1}^{m} x_i y_j P(X = x_i, Y = y_j) = \sum \limits_{i=1}^{n} \sum \limits_{j=1}^{m} x_i y_j P_X(x_i) P_Y(y_j) \\ = \sum \limits_{i=1}^{n} x_i P_X(x_i) \sum \limits_{j=1}^{m} y_j P_Y(y_j) = E[X] E[Y].
\end{multline*}

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
    \item Find covariance (and correlation) between $X$ and $Y$.
\end{enumerate}

## Illustrative problems

## Illustrative problems
### Example 2
We are given with discrete random variable $U$ with its PMF presented in the table below:
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
    \item Find covariance (and correlation) between $X$ and $Y$.
\end{enumerate}

## Illustrative problems
\vspace{-6.5em}
### Example 2

\begin{center}
    \begin{tabular}{c | c | c | c |} 
    & \(Y=0\) & \(Y= \frac{\sqrt{3}}{2} \) & \(Y= - \frac{\sqrt{3}}{2} \) \\
    \hline
    \(X=1\) &  &  &     \\
    \hline
    \(X=1/2\)  &  &  &  \\
    \hline
    \(X=-1/2\) &  &  &  \\
    \hline
    \(X=-1\)   &  &  &  \\
    \hline
\end{tabular}
\end{center}

## Illustrative problems
\vspace{-6.5em}
### Example 2

\begin{center}
    \begin{tabular}{c | c | c | c |} 
    & \(Y=0\) & \(Y= \frac{\sqrt{3}}{2} \) & \(Y= - \frac{\sqrt{3}}{2} \) \\
    \hline
    \(X=1\) & $\frac{1}{6}$ & $0$ & $0$ \\
    \hline
    \(X=1/2\)  & $0$ & $\frac{1}{6}$ & $ \frac{1}{6} $ \\
    \hline
    \(X=-1/2\) & $0$ & $\frac{1}{6}$ & $ \frac{1}{6} $ \\
    \hline
    \(X=-1\)   & $ \frac{1}{6} $ & $ 0 $ & $ 0 $ \\
    \hline
\end{tabular}
\end{center}

## Illustrative problems
### Example 3

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
\vspace{-6.5em}
### Example 3

\begin{flushleft}
    \begin{tabular}{c | c | c |} 
    & \(Y=0\) & \(Y= 1 \) \\
    \hline
    \(X=1\) &  &   \\
    \hline
    \(X=0\)  &  &  \\
    \hline
    \(X=-1\)   &  & \\
    \hline
\end{tabular}
\end{flushleft}

## Illustrative problems

## Illustrative problems
### Example 4

The random variables $U$ and $V$ each take the values $\pm 1$. Their joint distribution is given by:

$$
    P\{U = -1 \} = P\{ U = 1 \} = \frac{1}{2},
$$


\begin{align*}
    P\{V = + 1 | U = 1 \} & = P\{V = -1 | U = -1 \} = \frac{1}{3}, \\
    P\{V = -1 | U = 1 \} & = P\{V = +1 | U = -1 \} = \frac{2}{3}, \\
\end{align*}

\begin{enumerate}
    \item Find the probability that $x^2 + U x + V = 0$ has at least one real root.
    \item Find the probability that $x^2 + (U + V) x + (U + V) = 0$ has at least one real root.
\end{enumerate}

\textit{(Oxford 1980)}

## Illustrative problems
\vspace{-6.5em}
### Example 4
\begin{tabular}{c | c | c |} 
    & \(V=1\) & \(V= -1 \) \\
    \hline
    \(U=1\) &  &    \\
    \hline
    \(U=-1\)   &  &  \\
    \hline
\end{tabular}


## Illustrative problems
