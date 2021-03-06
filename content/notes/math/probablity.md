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

**Random variables** are uncertain numerical quantities (values in $$\mathbb{R}$$)

Usually, we don't know with certainty what value a random variable $$X$$ will take, but we know how to compute the probability that its value will be within some subset of $$\mathbb{R}$$

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

- Set [0, 1] of all real numbers between 0 and 1 are **not countable**. This was proved by Georg Cantor using the diagonal argument.


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

If random variable has supported $$S=\{0,1\}$$, it is called indicators (can be thought as of as signal lights). If $$X=1$$, then event of interest has happened  and if $$X=0$$, then event of interest has not happened.

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

As long as the (possibly) infinite sum $$\sum_{x \in} x \mathbb{P}[X=x]$$ absolutely converges, otherwise there is no expectation defined (if sum does not converge or only converges conditionally).

For $$\mathbb{N}_0$$-valued$$ random variables, the above expression simplifies to:

$$
\mathbb{E}[X]=\sum_{i=0}^{\infty} i \times p_{i}
$$

where $$p_{i}=\mathbb{P}[X=i],$$ for $$i \in \mathbb{N}_0$$. In this case, if:

$$
\lim _{n \rightarrow \infty} \sum_{i=0}^{n} i p_{i}=+\infty
$$

This sum doesn't absolutely converge and the expectation doesn't formally exist, but by convention we can write $$\mathbb{E}[X]=+\infty$$ to indicate that sum diverges towards infinity.

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

The sample space $$\Omega$$ as a source of all randomness in system. The elementary event $$\omega \in \Omega$$ is chosen by a process out of our control and the exact value of $$\omega$$ is assumed to be unknown. All other parts of system are deterministic (but possibly complicated) functions of $$\omega$$ (random variables).

For example, when a coin is toss, only a single drop of randomness is needed, the outcome of the toss. When several coins are tossed, the sample space must be a bigger. When a system involves a infinite number of random variables, a large sample space $$\Omega$$ is needed.

### Simple Random Walk on Canonical Probability Space

A stochastic process $$\left\{X_{n}\right\} n \in \mathbb{N}_{0}$$ is called a simple random walk if:
1. $$X_{0}=0$$
2. the increment $$X_{n+1}-X_{n}$$ is independent of $$\left(X_{0}, X_{1}, \ldots, X_{n}\right)$$ for each $$n \in \mathbb{N}_{0-}$$
3. the increment $$X_{n+1}-X_{n}$$ has a coin toss distribution: $$\mathbb{P}\left[X_{n+1}-X_{n}=1\right]=\mathbb{P}\left[X_{n+1}-X_{n}=-1\right]=\frac{1}{2}$$

For the sequence $$\left\{\gamma_{n}\right\}_{n \in \mathbb{N}_{0}}$$ defined in the canonical probability space, if we define a new sequence $$\left\{\xi_{n}\right\} n \in \mathbb{N}$$ of random variables:
$$
\xi_{n}=\left\{\begin{array}{ll}
{1,} & {\gamma_{n} \geq \frac{1}{2}} \\
{-1,} & {\text { otherwise }}
\end{array}\right
$$

The stochastic process X as a simple random walk is then defined as: $$X_{0}=0, X_{n}=\sum_{k=1}^{n} \xi_{k}, n \in \mathbb{N}$$

Here, each $$\xi_{n}$$ emulates a coin toss, and the value of the process $$X$$ at time $$n$$ is the cumulative sum of the first $$n$$ coin tosses.

## Simulation

Another way of thinking about sample spaces and randomness is via simulation. A simulation is cheap, and can be repeated to compute various statistics (mean, variance, etc). 

Each simulation involves:
1. actual sequence of outcomes of coin tosses (or samples from other distribution)
2. structure of the model. have to program in what happens when if heads shows vs tails shows. for example, in random walk, "go up" if heads, "go down" if tails shows. 

In general, #1, will usually remain the same as in the simple random walk, even in most complicated models. All you need is a sequence of random numbers. If can get a source of independently sequenced uniform distributed numbers between 0 and 1, you can simulate trajectories of all important stochastic processes. 

### Random number generation

Want the Random Number Generator (RNG) to be as unpredictable as possible, despite getting generated from a deterministic computer.

Want to cover interval [0, 1] evenly (be uniformly distributed over that interval). Over the long run, the number of random numbers in each subinterval $$[a,b]$$ should b e proportional to length $$b-a$$.

Want each pair of produced numbers cover the square [0, 1] x [0, 1] uniformly - that is, over a long run, the proportion of pairs falling in a patch A of the square [0, 1] x [0, 1] will be proportional to area. Want to continue with such requirements, and ask it for each triple, quadruples, etc.. The highest dimension $$n$$ that produces uniformly distributed numbers in $$[0,1]^n$$ is called the order of the RNG. The Messene Twister has an order of 623.

After a while, the RNGs will start to repeat (because of the finiteness of a computer's memory ). This is called the period of the RNG. Usually, RNGs use a hidden called a random seed and is used as an input to the RNG next time it's called. 

### Simulation of Random Variables

If you want to simulate random variables with distributions different from uniform on [0, 1], you use the transformation of the output of the RNG. 

Typically use a real (deterministic) function $$f:[0,1] \rightarrow \mathbb{R}$$. 

Some fairly popular procedures:

#### Discrete Random Numbers

If $$X$$ has discrete  distribution given by: 
$$
X \sim\left(\begin{array}{cccc}
{x_{1}} & {x_{2}} & {\dots} & {x_{n}} \\
{p_{1}} & {p_{2}} & {\dots} & {p_{n}}
\end{array}\right)
$$

For discrete distributions that take infinite number of values, can truncate to very large n and approximate. We know that probabilities $$p_{1}, p_{2}, \dots, p_{n}$$ add up to 1, so we can define numbers $$ 0 = q_{0}<q_{1}<\cdots<q_{n}=1$$ by:
$$
q_{0}=0, q_{1}=p_{1}, q_{2}=p_{1}+p_{2}, \ldots q_{n}=p_{1}+p_{2}+\cdots+p_{n}=1
$$

To simulate discrete random variable $$X$$, call RNG, then $$x_1$$ if $$0 \leq RNG < q_1$$, $$x_2$$ if $$q_1 \leq RNG < q_2$$, etc. So the transformation function $$f$$ is:

$$
f(x)=\left\{\begin{array}{ll}{x_{1},} & {0 \leq x<q_{1}} \\ {x_{2},} & {q_{1} \leq x<q_{2}} \\ {\dots} & {} \\ {x_{n},} & {q_{n-1} \leq x \leq 1}\end{array}\right.
$$

#### Method of Inverse Functions

For any continuous random variable $$X$$ with distribution function $$F_X$$, the random variable $$Y=F_{X}(X)$$ is uniformly distributed on [0, 1]. If we invert the distribution function $$F_X$$ and apply it to $$Y$$, you can recover $$X$$. So, if you want to simulate a random variable with invertible distribution function $$F$$, simulate uniform random variable on [0, 1] and apply function $$f=F^{-1}$$  as the transformation function. This method fails if you cannot write the inverse of the distribution function in closed form.

Exponential Distribution: For a Exponentially distributed random variable $$X$$ with parameter $$\lambda$$, the density $$f_{X}$$ of $$X$$ is given by:
$$
f_{X}(x)=\lambda \exp (-\lambda x), x>0, \text { and so } F_{X}(x)=1-\exp (-\lambda x), x>0
$$

and so $$F_{X}^{-1}(y)=-\frac{1}{\lambda} \log (1-y)$$. Since 1-RNG has same U[0, 1] distribution as RND, can conclude that $$f(x)=-\frac{1}{\lambda} \log (x)$$ works as transformation function in this case.

Cauchy Distribution:
The cauchy distribution has a density function:
$$
f_{X}(x)=\frac{1}{\pi} \frac{1}{\left(1+x^{2}\right)}
$$

The distribution function $$F_X$$ and its inverse are explicit:

$$
F_{X}(x)=\frac{1}{\pi} \int_{-\infty}^{x} \frac{1}{\left(1+x^{2}\right)} d x=\frac{1}{\pi}\left(\frac{\pi}{2}+\arctan (x)\right), \text { and so } F_{X}^{-1}(y)=\tan \left(\pi\left(y-\frac{1}{2}\right)\right)
$$

So $$\tan (\pi(\operatorname{rand}-0.5))$$ will simulate a Cauchy random variable for you. 

#### Box-Muller method
For normal random variable, there is no inverse function. But you can use a trick with two random numbers. If $$\gamma_{1}$$ and $$\gamma_{2}$$ are independent U[0, 1]-distributed random variables, then random variables
$$
X_{1}=\sqrt{-2 \log \left(\gamma_{1}\right)} \cos \left(2 \pi \gamma_{2}\right), X_{2}=\sqrt{-2 \log \left(\gamma_{1}\right)} \sin \left(2 \pi \gamma_{2}\right)
$$

are independent and standard normal on N(0, 1).

So to simulate a random variable with mean $$\mu=0$$ and $$\sigma^{2}=1$$, get two random numbers (rand1 and rand2). The numbers 
$$X_{1}=\sqrt{-2 \log (\mathrm{rand} 1)} \cos (2 \pi \mathrm{rand} 2), X_{2}=\sqrt{-2 \log (\mathrm{rand} 1)} \sin (2 \pi \mathrm{rand} 2)$$
 will be two independent normals. It's necessary to call rand() twice, but you also get two normal numbers. Normally in practice, many implementations produce two random numbers on every second call, return one of them, and store the 2nd for the next function call.

The transformation function is thus:
$$f_{1}(x, y)=\sqrt{-2 \log (x)} \cos (2 \pi y), f_{2}(x, y)=\sqrt{-2 \log (x)} \sin (2\pi y)$$

#### Method of the Central Limit

Simulate (something like n=12) independent random variables: $$X=\gamma_{1}+\gamma_{2}+\cdots+\gamma_{12}-6$$

This will approximate a unit normal, though it won't be exact ($$\mathbb{P}[X>6]=0, \text { and } \mathbb{P}[Z>6] \neq 0$$ for true normal $$Z$$)

Mathematically speaking, for a sequence of independent random variables $$X_{1}, X_{2},\ldots$$  with the same square integrable distribution. If you set $$\mu=\mathbb{E}\left[X_{1}\right]\left(=\mathbb{E}\left[X_{2}\right]=\ldots\right)$$ and $$\operatorname{Var}\left[X_{1}\right]\left(=\operatorname{Var}\left[X_{2}\right]=\ldots\right)$$. The sequence of normalized random variables $$\frac{\left(X_{1}+X_{2}+\cdots+X_{n}\right)-n \mu}{\sigma \sqrt{n}}$$ converges to a normal random variable.


### Monte Carlo Integration

Law of Large Numbers: If $$X_{1}, X_{2}, \dots$$ is a sequence of random variables with the same distribution, and there is a function $$g: \mathbb{R} \rightarrow \mathbb{R}$$ such that $$\mu=\mathbb{E}\left[g\left(X_{1}\right)\right]\left(=\mathbb{E}\left[g\left(X_{2}\right)\right]=\ldots\right)$$

then:
$$
\frac{g\left(X_{1}\right)+g\left(X_{2}\right)+\cdots+g\left(X_{n}\right)}{n} \rightarrow \mu=\int_{-\infty}^{\infty} g(x) f_{X_{1}}(x) d x, \text { as } n \rightarrow \infty
$$

The key idea of monte carlo integration is:

If the quantity y you are interested in can be written as $$y=\int_{-\infty}^{\infty} g(x) f_{X}(x) d x$$ for some random variable X with density $$f_{X}$$ and some function g, and that $$x_{1}, x_{2}, \dots$$ are random numbers distributed according to distribution with density $$f_{X}$$, then the average $$\frac{1}{n}\left(g\left(x_{1}\right)+g\left(x_{2}\right)+\cdots+g\left(x_{n}\right)\right)$$ will approximate y. 

The accuracy of the approximation behaves like $$1 / \sqrt{n}$$, so you have to quadruple the number of simulations if you want to double the precision of the approximation. 

Examples:

1. Numerical integration.
   
If g is a function on [0, 1]. To approximate the integral $$\int_{0}^{1} g(x) d x$$, you can take a sequence of n $$(\mathrm{U}[0,1])$$ random numbers $$x_{1}, x_{2}, \dots$$, to make the approximation:
$$\int_{0}^{1} g(x) d x \approx \frac{g\left(x_{1}\right)+g\left(x_{2}\right)+\cdots+g\left(x_{n}\right)}{n}$$.
Here, the density of $$X \sim U[0,1]$$ is given by:
$$f_{X}(x)=\left\{\begin{array}{ll}
{1,} & {0 \leq x \leq 1} \\
{0,} & {\text { otherwise }}
\end{array}\right.$$

2. Estimating Probabilities:

If Y is a random variable with density function $$f_{Y}$$. If we want the probability of $$\mathbb{P}[Y \in[a, b]]$$ for some $$a<b$$, we can simulate $$n$$ draaws $$y_{1}, y_{2}, \dots, y_{n}$$ from the distribution $$F_{Y}$$, tand the required approximatin is:
$$\mathbb{P}[Y \in[a, b]] \approx \frac{\text { number of } y_{n}^{\prime} \text { s falling in the interval }[a, b]}{n}$$

The great thing about Monte-Carlo is that even if the density of the random variable cannot be obtained, but you can simuilate darws from it, you can still perform calculate aobve and get approximation. Everything works in same way for probabilities involving random vectors in any number of dimensions. 


3. Approximation of pi

Can calculate that $$\pi \approx 3.141592$$ by using Monte Carlo method. All you have to exploit that $$\pi$$ is the area of the unit disk. Therfore $$\pi / 4$$ is equal to the portion of the area of the unit disk lying on the positive quadrant. 

Can write:
$$\frac{\pi}{4}=\int_{0}^{1} \int_{0}^{1} g(x, y) d x d y$$

Where: 
$$
g(x, y)=\left\{\begin{array}{ll}
{1,} & {x^{2}+y^{2} \leq 1} \\
{0,} & {\text { otherwise }}
\end{array}\right.
$$

Can simulate $$n$$ pirs $$\left(x_{i}, y_{i}\right), i=1 \ldots n$$ of uniformally distributed normal numbers and count how many fall into upper quater of unit circle. See how many satisfy $$x_{i}^{2}+y_{i}^{2} \leq 1$$ and divide by n. Multiply result by 4 and you should be close to pi.  


$$
\left\{X_{n}\right\}_{n \in \mathbb{N}_{0}}
$$

# Simple random walks

A sequence $$\left\{X_{n}\right\}_{n \in \mathbb{N}_{0}}$$ of random variables is called a simple random walk (with parameter $$p \in(0,1))$$ if
1. $$X_{0}=0$$
2. $$X_{n+1}-X_{n}$$ is independent of $$\left(X_{0}, X_{1}, \ldots, X_{n}\right)$$ for all $$n \in \mathbb{N},$$ and
3. the random variable $$X_{n+1}-X_{n}$$ has the following distribution (where $$q=1-p$$)
$$
\left(\begin{array}{cc}
{-1} & {1} \\
{q} & {p}
\end{array}\right)
$$
If $$p=\frac{1}{2}$$ the random walk is called symmetric.

This is called a simple because the size of each step is fixed (equal to 1), and only the direction is random. Other more general random walks are possible.

If $$\left\{X_{n}\right\}_{n \in \mathbb{N}_{0}}$$ is a simple random walk with param $$p$$, the distribution of X_{n} is discrete with support $$\{-n,-n+2, \ldots, n-2, n\}$$ and probablities:
$$p_{l}=\mathbb{P}\left[X_{n}=l\right]=\left(\begin{array}{c}{n} \\ {\frac{l+n}{2}}\end{array}\right) p^{(n+l) / 2} q^{(n-l) / 2}, l=-n,-n+2, \ldots, n-2, n$$

$$X_{n}$$ is composed of $$n$$ independent steps $$\xi_{k}=X_{k+1}-X_{k}, k=1, \ldots, n,$$ each of which goes either up or down. In order to reach level $$l$$ in those $$n$$ steps, the number $$u$$ of up-steps and the number $$d$$ of down steps must satisfy $$u-d$$ (and $$u+d=n$$ ). Therefore, $$u=\frac{n+l}{2}$$ and $$d=\frac{n-l}{2}$$

The random variable here $$\frac{n+X_{n}}{2}$$ has the binomial $$b(n, p)$$ distribution.

You can view the random walk as a random trajectory in some space of trajetories, and compute the rquired probability by counting number of trajectories in the subset/event you are interested in, then adding them gether, weighted by probabilities. The space C of trajtectories is $$C=\left\{\left(x_{0}, x_{1}, \ldots, x_{n}\right): x_{0}=0, x_{k+1}-x_{k}=\pm 1, k \leq n-1\right\}$$. The first n steps of the RW is a probablity distribution on the state space C.

