---
title: "Probability Theory"
date: '2019-12-26'
description: "Probability Theory Notes"
tags:
- math
- probability
- random
- stochastic
series:
- notes
categories:
- math
libraries:
- katex
katex: true
markup: "mmark"
---


Probability is about _random variables_.

>
> The probable is what usually happens. 
> 
> —Aristotle


# Random variables

**Random variables** are uncertain, numerical quantities (values in $$\mathbb{R}$$)

Usually we don't know with certainty what value a random variable $$X$$ will take, but we know how to compute probability that its value will be within some subset of $$\mathbb{R}$$

For example, we can compute $$\mathbb{P}[X \geq 7], \mathbb{P}[X \in[2,3.1]] $$ or $$\mathbb{P}[X \in\{1,2,3\}]$$

Such a collection is called a **distribution** of $$X$$. Note: don't confuse a random variable with its _distribution_, This can be easy especially when multiple random variables appear at same time.

When two random variables $$X$$ and $$Y$$ have same distribution, they are referred to as **equally distributed**. The common notation is $$X \stackrel{(d)}{=} Y$$. This implies $$ \mathbb{P}[X \in A]=\mathbb{P}[Y \in A] $$.

# Countable Sets

Different perspectives of countability of sets:

- A set is countable if it has the same number of elements as the set $$\mathbb{N}=\{1,2, \ldots\}$$ of natural numbers.

- Set $$A$$ is countable if there exists a function $$f: \mathbb{N} \rightarrow A$$ which is bijective (one to one and onto). 
  - $$f$$ can be thought as the correspondence that “proves” that there exactly as many elements of $$A$$ as there are elements of $$\mathbb{N}$$ 
  - $$ f $$ can be viewed as an ordering of $$A$$; it arranges $$A$$ into a particular order $$A=\left\{a_{1}, a_{2}, \ldots\right\}$$ where $$a_{1}=f(1), a_{2}=f(2)$$ etc.

### Examples:
- $$\mathbb{N}$$ is countable; $$f(n) = n$$

- $$\mathbb{N}_{0}=\{0,1,2,3, \ldots\}$$ is countable; use $$f(n) = n - 1$$. Set $$\mathbb{N}_{0}$$ and its proper subset $$\mathbb{N}$$ have same size!

- $$\mathbb{Z}=\{\ldots,-2,-1,0,1,2,3, \ldots\}$$ is countable. 
Here: $$f(k)=\left\{\begin{array}{ll}{2 k+1,} & {k \geq 0} \\{-2 k,} & {k<0}\end{array}\right.$$ so $$\mathbb{Z}$$ and $$\mathbb{N}$$ have same size.

- Set $$\mathbb{N} \times \mathbb{N}=\{(m, n): m \in \mathbb{N}, n \in \mathbb{N}\}$$ is also countable.

- Rational numbers (fractions) $$\mathbb{Q}$$ are countable.

- Set [0, 1] of all real numbers between 0 and 1 are **not countable**; proved by Georg Cantor using the diagonal argument.


# Discrete random variables  

Discrete - if random variable takes at most countably many values.

$$X$$ is said to be discrete if there exists a _finite_ or _countable_ set $$S \subset \mathbb{R}$$ such that $$\mathbb{P}[X \in S]=1$$ (e.g, if we know with certainty that only values $$X$$ can take are those in $$S$$). 

The smallest set $$S$$ with this property is called the **support** of $$X$$. Often written $$_{X}$$

Common supports:
- If $$X$$ takes only values 1, 2, 3, ..., we say $$X$$ is $$\mathbb{N}$$-**valued**.
- If we allow 0 (in addition to $$\mathbb{N}$$), so that $$\mathbb{P}[X \in S]=1$$, we say $$X$$ is $$\mathbb{N}_0$$-**valued**.
- Sometimes, it is convenient to have discrete random numbers that can take $$+\infty$$. For example, modeling waiting times which may or may not ever happen (infinite waiting time). In these cases, if $$
S=\{1,2,3, \ldots,+\infty\}=\mathbb{N} \cup\{+\infty\} $$ then can say random value is **extended $$\mathbb{N}_0$$-valued** or (**extended $$\mathbb{N}_0$$-valued**)
- Sometimes support isn't numbers. For example, heads/tails {H,T} or suit of cards, or a markov chain.

## Computation of probability for discrete random variables

In order to be able to compute any probability involving discrete random variable $$X$$, all you need to know how to compute the probabilities $$\mathbb{P}[X=x]$$, for all $$x \in S$$. Keep in mind that the sum of all of these probabilities adds up to 1.

For example, if you want to compute $$\mathbb{P}[X\in B]$$ for some set $$ B \subseteq \mathbb{R} $$, all you pick all are $$x \in S$$  which are also in $$B$$ and sum probabilities. E.g, $$\mathbb{P}[X \in B]=\sum_{x \in S \cap B} \mathbb{P}[X=x]$$

Because of this, the distribution of a discrete random variable $$X$$ is often described using a table:

$$
X \sim\left(\begin{array}{cccc}
{x_{1}} & {x_{2}} & {x_{3}} & {\dots} \\
{p_{1}} & {p_{2}} & {p_{3}} & {\dots}
\end{array}\right)
$$

where the top row lists all elements of $$S$$ (the support of $$X$$), and the bottom row lists the probabilities $$
\left(p_{i}=\mathbb{P}\left[X=x_{i}\right], i \in \mathbb{N}\right)$$.K

When the random variable is $$\mathbb{N}$$-valued or $$\mathbb{N}_0$$-valued, we know what $$x_{1}, x_{2}, \dots$$ are, so we just use the sequence $$p_{1}, p_{2}, \dots$$. This is called the **probability mass function**.  

For extended $$\mathbb{N}_0$$-valued, if you are given a pmf of the $$\mathbb{N}$$-valued or $$\mathbb{N}_0$$-valued cases and you sum them up, see if it is equal to 1. If so, then $$X$$ never takes $$+\infty$$, or else probability of $$+\infty$$ is positive.

If random variable has support $$S=\{0,1\}$$, it is called indicators (can be thought as of as signal lights). If $$X=1$$, then event of interest has happened  and if $$X=0$$, then event of interest has not happened. 

For example, if $$Y$$ is outcome of coin toss, and if you want to know if Heads (H) occurred, can write $$X=\mathbf{1}_{\{Y=H\}}$$

If you have two die, $$Y_1$$ and $$Y_2$$, with $$S=\{1, 2, 3, 4, 5, 6\}$$, and you want to know if probability that their sum is at least 9, define new random variable $$Z = Y_1 + Y_2 $$. Another random variable defined as indicator $$X=\mathbf{1}_{\{Z \geq 9\}}$$. i.e, 

$$
X=\left\{\begin{array}{ll}
{1,} & {Z \geq 9} \\
{0,} & {Z<9}
\end{array}\right.
$$

If we compute $$\mathbb{P}[X=1]$$, then this gives us probability whether the event of interest (X) has happened or not. 


## Expectation

For discrete random variable $$X$$ with support, the definition of $$\mathbb{E}[X]$$ of $$X$$ is:

$$
\mathbb{E}[X]=\sum_{x \in} x \mathbb{P}[X=x]
$$

as long as the (possibly) infinite sum $$\sum_{x \in} x \mathbb{P}[X=x]$$ absolutely converges, otherwise there is no expectation defined (if sum does not converge or only converges conditionally). 

For $$\mathbb{N}_0$$-valued$$ random variables, the above expression simplifies to:

$$
\mathbb{E}[X]=\sum_{i=0}^{\infty} i \times p_{i}
$$

where $$p_{i}=\mathbb{P}[X=i],$$ for $$i \in \mathbb{N}_0$$. In this case, if:

$$
\lim _{n \rightarrow \infty} \sum_{i=0}^{n} i p_{i}=+\infty
$$

This sum doesn't absolutely converge and expectation doesn't formally exist, but by convention we can write $$\mathbb{E}[X]=+\infty$$ to indicate that sum diverges towards infinity.

If $$\mathbb{E}[X]$$ exists, then $$X$$ is called **integrable**. 

If $$\mathbb{E}\left[X^{2}\right]<\infty$$ ($$X^{2}$$ is integrable), $$X$$ is called **squared integrable**. 

If $$\mathbb{E}\left[|X|^{m}\right]<\infty$$, for some $$m > 0$$, then $$X$$ has a **finite $$m$$-th moment.** 

If $$X$$ has a finite $$m$$-th moment, $$\left.\mathbb{E}[\|X-\mathbb{E}[X]]^{m}\right]$$ exists, and is called the **$$m$$-th central moment**. 

Expectations hold the following properties for random integrable variables $$X$$ and $$Y$$:

* **Linearity**: $$\mathbb{E}[\alpha X+\beta Y]=\alpha \mathbb{E}[X]+\beta \mathbb{E}[Y], \text { for } \alpha, \beta \in \mathbb{R}$$

* **Monotonicity**: $$\mathbb{E}[X] \geq \mathbb{E}[Y] \text { if } \mathbb{P}[X \geq Y]=1$$

If $$X$$ is **squared integrable**, a variance Var[$$X$$] can be defined as $$\mathbb{E}\left[(X-m)^{2}\right]$$ where $$m=\mathbb{E}[X]$$. The square root $$\sqrt{\operatorname{Var}[X]}$$ is called the **standard deviation**. 

If $$m$$-th moment exists, all lower moments exist. So, each square integrable random variable is also integrable. 

For random variables that can take on $$+\infty$$, we can say expectation doesn't exist as long as $$\mathbb{P}[X=+\infty]>0$$, that is, there is positive chance that it will take $$+\infty$$.

# Events

Probability is explained in terms of **sample space** or **probability space**, referred usually as $$\Omega$$. 

Various subsets of $$\Omega$$ are called **events**.

Events typically contain all **elementary events**, elements of the probability space, usually denoted as $$\omega$$. 

For example, if we want to compute likelihood of getting odd number as a sum of outcomes of two dice throws, first build probability space:
$$
\Omega=\{(1,1),(1,2), \ldots,(6,1),(2,1),(2,2), \ldots,(2,6), \ldots,(6,1),(6,2), \ldots,(6,6)\}
$$

then define event A which contains all pairs $$(k, l) \in \Omega$$ such that k + l is an odd number. i.e,
$$
A=\{(1,2),(1,4),(1,6),(2,1),(2,3), \ldots,(6,1),(6,3),(6,5)\}
$$

Events are thus turn into simple indicator random variables. For event A, the random variable $$\mathbf{1}_{A}$$ is denoted as
$$
\mathbf{1}_{A}=\left\{\begin{array}{ll}
{1,} & {A \text { happened }} \\
{0,} & {A \text { did not happen }}
\end{array}\right.
$$

Conversely, for indicator random variable $$X$$, indicated event $$A$$ is a set of events for which X takes value 1. If we apply expectation to indicator random variable $$X=\mathbf{1}_{A}$$, we get probability of $$A$$: $$\mathbb{E}\left[\mathbf{1}_{A}\right]=1 \times \mathbb{P}[A]+0 \times \mathbb{P}\left[A^{c}\right]=\mathbb{P}[A]$$ ($$\mathbf{1}_{A}$$ takes 1 on A, 0 on complement $$A^{c}=\Omega \backslash A$$).

# Dependence and independence

One of the main differences between random variables and deterministic quantities os that in former case, whole is more than sum of its parts. 

For example, with random variable $$X$$ ans $$Y$$, both of the following cases will give a same distribution:
1. throwing two dice, denote first one by $$X$$, and second one by $$Y$$.
2. throw two dice, denote outcome of first by $$X$$, and set $$Y=6-X$$. 

In both case, X and Y will have same distribution:
$$
X, Y \sim\left(\begin{array}{cccccc}
{1} & {2} & {3} & {4} & {5} & {6} \\
{\frac{1}{6}} & {\frac{1}{6}} & {\frac{1}{6}} & {\frac{1}{6}} & {\frac{1}{6}} & {\frac{1}{6}}
\end{array}\right)
$$

The pairs $$(X, Y)$$ are very different in two examples. In first, if value of $$X$$ is revealed, it does not affect view of value of $$Y$$. In second, knowledge of $$X$$ gives us knowledge of $$Y$$ ($$6-X$$). 

In general, when more than one random variable is considered, one must look at external information about their relationship outside of their distributions. If there is no relationship, they are **independent**. i, for two discrete random variables X and Y: 
$$
\mathbb{P}[X=x \text { and } Y=y]=\mathbb{P}[X=x] \mathbb{P}[Y=y]
$$

for all $$x$$ and $$y$$ in the respective supports $$_X and _Y$$ of $$X$$ and $$Y$$.

Two events $$A$$ and $$B$$ are independent if:
$$
\mathbb{P}[A \cap B]=\mathbb{P}[A] \mathbb{P}[B]
$$

# Conditional probability

When two random variables are not independent, we still want to know how the knowledge of the exact value of one affects our guesses the value of the other. This is given by the **conditional probability**.

For events $$A, B$$ such that $$\mathbb{P}[B]>0$$, the conditional probability $$
\mathbb{P}[A | B] $$ of $$A$$ given $$B$$ is:
$$
\mathbb{P}[A | B]=\frac{\mathbb{P}[A \cap B]}{\mathbb{P}[B]}
$$

The conditional probability is not defined when $$\mathbb{P}[B]=0$$, because this would be dividing by zero. 

A collection of events $$A_{1}, A_{2}, \ldots, A_{n}$$ is called a **partition** of $$\Omega$$ if $$A_{1} \cup A_{2} \cup \ldots A_{n}=\Omega$$ and $$A_{i} \cap A_{j}=\emptyset$$ for all pairs $$i, j=1, \ldots, n \text { with } i \neq j$$

For a partition $$A_{1}, A_{2}, \ldots, A_{n}$$ and event B of $$\Omega$$, the following hold true:

**Law of total probability**:
 $$
\mathbb{P}[B]=\sum_{i=1}^{n} \mathbb{P}\left[B | A_{i}\right] \mathbb{P}\left[A_{i}\right]
$$

**Bayes formula**:  for $$k=1, \ldots, n$$, we have:

$$
\mathbb{P}\left[A_{k} | B\right]=\frac{\mathbb{P}\left[B | A_{k}\right] \mathbb{P}\left[A_{k}\right]}{\sum_{i=1}^{n} \mathbb{P}\left[B | A_{i}\right] \mathbb{P}\left[A_{i}\right]}
$$

Above laws are stated for finite partitions, but hold true if $$A_{k}$$ is countability infinite - you just replace finite sums by infintie series.

Random variables can be substituted for events in definition of conditional probability. For two random variables X and Y, the conditional probability $$X=x$$ given $$Y=y$$ with $$x$$ and $$y$$ in the respective supports $$_X and _Y$$ of $$X$$ and $$Y$$ is given by:
$$
\mathbb{P}[X=x | Y=y]=\frac{\mathbb{P}[X=x \text { and } Y=y]}{\mathbb{P}[Y=y]}
$$

This formula produces different probability distribution for each $$y$$. This is called the conditional distribution of $$X$$, given $$Y=y$$.

Example:
Let X be number of heads obtained when two coins are thrown. Let Y be indicator of the event that the second coin shows heads. The distribution of X is binomial:
$$
X \sim\left(\begin{array}{ccc}
{0} & {1} & {2} \\
{\frac{1}{4}} & {\frac{1}{2}} & {\frac{1}{4}}
\end{array}\right)
$$

Or in more compact notation, $$X \sim\left(\frac{1}{4}, \frac{1}{2}, \frac{1}{4}\right)$$. Random variable Y has bernoulli distribution $$Y=\left(\frac{1}{2}, \frac{1}{2}\right)$$

If we are told that Y=0, e.g, second coin is heads, then:

$$
\mathbb{P}[X=x | Y=0]=\left\{\begin{array}{l}
{\frac{\mathbb{P}[X=0, Y=0]}{\mathbb{P}[Y=0]}=\frac{\mathbb{P}[\text { the pattern is } \operatorname{TT}]}{\mathbb{P}[Y=0]}=\frac{1 / 4}{1 / 2} = {1/2}} \\
{\frac{\mathbb{P}[X=1, Y=0]}{\mathbb{P}[Y=0]}=\frac{\mathbb{P}[\text { the pattern is HT }]}{\mathbb{P}[Y=0]}=\frac{1 / 4}{1 / 2}={1/2}} \\
{\frac{\mathbb{P}[X=2, Y=0]}{\mathbb{P}[Y=0]}=\frac{\mathbb{P}[\text { well, there is no such pattern }]}{\mathbb{P}[Y=0]}=0}
\end{array}\right.
$$

If X and Y are independent:
$$
\mathbb{P}[X=x | Y=y]=\frac{\mathbb{P}[X=x, Y=y]}{\mathbb{P}[Y=y]}=\frac{\mathbb{P}[X=x] \mathbb{P}[Y=y]}{\mathbb{P}[Y=y]}=\mathbb{P}[X=x]
$$

Generalizing to larger collection of random variables (for all $$X_{1}, X_{2}, \ldots, X_{n} $$):
$$
\mathbb{P}\left[X_{1}=x_{1}, X_{2}=x_{2}, \ldots X_{n}=x_{n}\right]=\mathbb{P}\left[X_{1}=x_{1}\right] \mathbb{P}\left[X_{2}=x_{2}\right] \ldots \mathbb{P}\left[X_{n}=x_{n}\right]
$$

For collection of n independent random variables $$ (X_{1}, X_{2}, \ldots, X_{n} )$$:
1. $$ g_{1}\left(X_{1}\right), \ldots, g_{n}\left(X_{n}\right)$$ are also independent for (most) functions $$g_{1}, \dots, g_{n}$$
2. if $$ X_{1}, X_{2}, \ldots, X_{n} $$ are integrable, then product $$ X_{1}, X_{2}, \ldots, X_{n} $$ is integrable, and:
$$
\mathbb{E}\left[X_{1} \ldots X_{n}\right]=\mathbb{E}\left[X_{1}\right] \ldots \mathbb{E}\left[X_{n}\right]
$$
3. if $$ X_{1}, X_{2}, \ldots, X_{n} $$ is square integrable, then:
  
$$
\operatorname{Var}\left[X_{1}+\cdots+X_{n}\right]=\operatorname{Var}\left[X_{1}\right]+\cdots+\operatorname{Var}\left[X_{n}\right]
$$

or equivalently:

$$
\operatorname{Cov}\left[X_{i}, X_{j}\right]=\mathbb{E}\left[\left(X_{1}-\mathbb{E}\left[X_{1}\right]\right)\left(X_{2}-\mathbb{E}\left[X_{2}\right]\right)\right]=0
$$

for all $$i \neq j \in\{1,2, \ldots, n\}$$. This means that independent random variables are **uncorrelated**. The converse is not true. Uncorrelated random variables may or may not be independent. 

When some random variables $$ (X_{1}, X_{2}, \ldots, X_{n}) $$ are considered together, you can group them into **random vector**. 

Distribution of random vector $$ X=(X_{1}, X_{2}, \ldots, X_{n}) $$ is the collection of all probabilities:
$$
\mathbb{P}\left[X_{1}=x_{1}, X_{2}=x_{2}, \ldots, X_{n}=x_{n}\right]
$$
when $$ x_{1}, x_{2}, \ldots, x_{n} $$ range through all numbers in all appropriate supports. Unlike a single random variable, writing down distribution of multiple random vectors in tables is a bit more difficult. In two dimensional cae, you need entire matrix. In high dimensions, you need hologram. 

The distributions of components $$ X_{1}, X_{2}, \ldots, X_{n} $$ of random vector $$X$$ is called the **marginal distribution** of random variables $$ X_{1}, X_{2}, \ldots, X_{n} $$

If random variables $$ X_{1}, X_{2}, \ldots, X_{n} $$ are part of the same random vector, the distribution of $$X$$ is called the **joint distribution** of $$ X_{1}, X_{2}, \ldots, X_{n} $$. Unless random variables are known to be independent, the joint distribution holds more information about $$X$$ than all marginal distributions together.

## Example discrete random variables:

**Bernoulli**: Success (1) or failure (0) with probability p. If success is encoded by 1, failure by $$-1$$ and $$p=\frac{1}{2}$$ we call it the coin toss.

- parameters : $$\quad p \in(0,1)(q=1-p)$$
- notation: $$b(p)$$
- support: $$\{0,1\}$$
- pmf: $$\quad p_{0}=p$$ and $$p_{1}=q=1-p$$
- generating function: $$p s+q$$
- mean : $$p$$ 
- standard deviation: $$\sqrt{p q}$$


**Binomial**: The number of successes in n repetitions of a Bernoulli trial with success probability

- parameters : $$\quad n \in \mathbb{N}, p \in(0,1) \quad(q=1-p)$$
- notation: $$\quad b(n, p)$$ 
- support: $$\quad\{0,1, \dots, n\}$$
- pmf: $$\quad p_{k}=\left(\begin{array}{l}{n} \\ {k}\end{array}\right) p^{k} q^{n-k}, k=0, \ldots, n$$
- generating function : $$(p s+q)^{n}$$
- mean : $$n p$$
- standard deviation: $$\sqrt{n p q}$$

**Poisson**: The number of spelling mistakes one makes while typing a single page.
- parameters: $$\lambda>0$$
- notation : $$\quad p(n, p)$$
- support: $$\mathbb{N}_{0}$$ 
- pmf $$: \quad p_{k}=e^{-\lambda} \frac{\lambda^{k}}{k !}, k \in \mathbb{N}_{0}$$
- generating function: $$e^{\lambda(s-1)}$$
- mean : $$\lambda$$
- standard deviation: $$\sqrt{\lambda}$$

**Geometric**: The number of repetitions of a Bernoulli trial with parameter p until the first success.
- parameters : $$\quad p \in(0,1), q=1-p$$
- notation : $$(g(p)$$ 
- support: $$\mathbb{N}_{0}$$
- pmf: $$\quad p_{k}=p q^{k-1}, k \in \mathbb{N}_{0}$$
- generating function : $$\frac{p}{1-q s}$$ 
- mean: $$p$$
- standard deviation: $$\frac{\sqrt{q}}{p}$$

**Negative Binomial**: The number of failures it takes to obtain r successes in repeated independent Bernoulli trials with success probability p.

- parameters : $$\quad r \in \mathbb{N}, p \in(0,1)(q=1-p)$$
- notation : $$\quad g(n, p)$$
- support: $$\mathbb{N}_{0}$$
- pmf: $$\quad p_{k}=\left(\begin{array}{c}{-r} \\ {k}\end{array}\right) p^{r} q^{k}, k=\in \mathbb{N}_{0}$$
- generating function : $$\left(\frac{p}{1-q s}\right)^{r}$$
- mean : $$r \frac{q}{p}$$
- standard deviation : $$\frac{\sqrt{q r}}{p}$$


# Stochastic Processes

Stochastic Processes usually model evolution of a random system in time. 

If $$\mathcal{T}$$ is a subset of $$[0, \infty)$$, a family of random variables $$\left\{X_{t}\right\}_{t \in \mathcal{T}}$$ indexed by $$\mathcal{T}$$ is called a stochastic (or random) process. If $$\mathcal{T}=\mathbb{N}$$ or $$\mathcal{T}=\mathbb{N}_{0}$$, then $$\left\{X_{t}\right\}_{t \in \mathcal{T}}$$ is a discrete-time process (changes happen discretely), if $$[\mathcal{T}=0, \infty)$$, then it  is continuous time (value of process can change every instant).

If $$\mathcal{T}$$ is a singleton, $$\left\{X_{t}\right\}_{t \in \mathcal{T}} \equiv X_{1}$$ is a single random variable. If $$\mathcal{T}$$  is finite ($$\mathcal{T}=\{1,2, \ldots, n\}$$), then it is a random vector. Therefore, stochastic/random processes are generalizations of random vectors. However, interpretation is usually different. Usually components of random vector are usually different spatial coordinates, while index $$t \in T $$ is usually interpreted as time. 

Usually hard to define notion of a density or PMF for a stochastic process because of the infinity. Usually a family of finite-dimensional distributions (joint distributions of random vectors) are considered:
$$
\left(X_{t_{1}}, X_{t_{2}}, \ldots, X_{t_{n}}\right)
$$
for all $$ n \in \mathbb{N}$$  and all choices $$t_{1}, \ldots, t_{n} \in \mathcal{T}$$.

Every stochastic process can be viewed as a function of two variables: $$t$$ and $$\omega$$. For each fixed $$t$$, $$\omega \mapsto X_{t}(\omega)$$ is a random variable. If you keep $$\omega$$ fixed, the stochastic process is a function mapping $$\omega$$ to real valued $$t \mapsto X_{t}(\omega)$$. These functions are called trajectories of the stochastic process $$X$$.

## Canonical probability space


If you have a infinite index ($$ \# \mathcal{T}=+\infty$$) stochastic process, constructing a full probability space ($$\Omega, \mathcal{F}, \mathbb{P}$$) requires quite a bit of technical work. If you make some simplifying assumptions, it is simpler.

Starting with sample space $$\Omega$$:
$$\Omega=[0,1] \times[0,1] \times \cdots=[0,1]^{\infty}$$

any general element of $$\Omega$$ will be a sequence $$\omega=\left(\omega_{0}, \omega_{1}, \omega_{2}, \ldots\right)$$ of real numbers in [0, 1].  For $$n \in \mathbb{N}_{0}$$, if we define the mapping $$\gamma_{n}: \Omega \rightarrow[0,1]$$ which simply chooses the $$n$$-th coordinate:
$$
\gamma_{n}(\omega)=\omega_{n}
$$
The following holds true:
There exists a $$\sigma$$-algebra $$\mathcal{F}$$ and a probability $$\mathbb{P} \text { on } \Omega$$ such that:
1. each $$\gamma_{n}, n \in \mathbb{N}_{0}$$ is a random variable with uniform distribution on [0, 1] and
2. the sequence $$\left\{\gamma_{n}\right\}_{n \in \mathbb{N}_{0}}$$ is independent.

The sample space $$\Omega$$ as a source of all randomnesss in system. The elementary event $$\omega \in \Omega$$ is chosen by a process out of our control and exact value of $$\omega$$ is asumed to be unknown. All other parts of system are determinstic (but possibly complicated) functions of $$\omega$$ (random variables).

For example, when a coin is toss, only a single drop of randomess is needed, the outome of the toss. When several coins are tossed, the sample space must be a bigger. When a system involves a infinite number of random variables, a large sample space $$\Omega$$ is needed.

### Simple Random Walk on Canonical Probablity Space

A stochastic process $$\left\{X_{n}\right\} n \in \mathbb{N}_{0}$$ is called a simple random walk if:
1. $$X_{0}=0$$
2. the increment $$X_{n+1}-X_{n}$$ is independent of $$\left(X_{0}, X_{1}, \ldots, X_{n}\right)$$ for each $$n \in \mathbb{N}_{0-}$$
3. the increment $$X_{n+1}-X_{n}$$ has a coin toss distribution: $$\mathbb{P}\left[X_{n+1}-X_{n}=1\right]=\mathbb{P}\left[X_{n+1}-X_{n}=-1\right]=\frac{1}{2}$$

For the sequence $$\left\{\gamma_{n}\right\}_{n \in \mathbb{N}_{0}}$$ defined in the canonical probablity space, if we define a new sequence $$
\left\{\xi_{n}\right\} n \in \mathbb{N}
$$ of random variables:
$$
\xi_{n}=\left\{\begin{array}{ll}
{1,} & {\gamma_{n} \geq \frac{1}{2}} \\
{-1,} & {\text { otherwise }}
\end{array}\right
$$

The stochastic process X as a simple random walk is then defined as: $$
X_{0}=0, X_{n}=\sum_{k=1}^{n} \xi_{k}, n \in \mathbb{N}
$$

Here, each $$\xi_{n}$$ emulates a coin toss, and the value of the process $$X$$ at time $$n$$ is the cumulative sum of the first $$n$$ coin tosses.
