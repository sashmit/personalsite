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

For extended $$\mathbb{N}_0$$-valued, if you are given a pmf of the $$\mathbb{N}$$-valued or $$\mathbb{N}_0$$-valued cases and you sum them up, see if it is equal to 1. If so, then $$X$$ never takes $$+\infty$$, or else probablity of $$+\infty$$ is positive.

If random variable has support $$S=\{0,1\}$$, it is called indicators (can be thought as of as signal lights). If $$X=1$$, then event of interest has happened  and if $$X=0$$, then event of interest has not happened. 

For example, if $$Y$$ is outcome of coin toss, and if you want to know if Heads (H) occured, can write $$X=\mathbf{1}_{\{Y=H\}}$$

If you have two die, $$Y_1$$ and $$Y_2$$, with $$S=\{1, 2, 3, 4, 5, 6\}$$, and you want to know if probalbity that their sum is at least 9, define new random variable $$Z = Y_1 + Y_2 $$. Another random variable defined as indicator $$X=\mathbf{1}_{\{Z \geq 9\}}$$. i.e, $$
X=\left\{\begin{array}{ll}
{1,} & {Z \geq 9} \\
{0,} & {Z<9}
\end{array}\right
$$

Lets us compute whether event of interest (X) has happened by computing $$\mathbb{P}[X=1]$$