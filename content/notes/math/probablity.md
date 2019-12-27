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

Usually don't know with certainty what value a random variable $$X$$ will take, we know how to compute probablity that its value will be within some subset of $$\mathbb{R}$$

For example, we can compute, $$\mathbb{P}[X \geq 7], \mathbb{P}[X \in[2,3.1]] $$ or $$\mathbb{P}[X \in\{1,2,3\}]$$

Such a collection is called a _distribution_ of $$X$$. Note: don't confuse random variable with its _distribution_, especially when multiple random variables appear at same time.

When two random variables $$X$$ and $$Y$$ have same distribution, they are referred to as *equally distributed*. The common notation is $$X \stackrel{(d)}{=} Y$$. This implies $$ \mathbb{P}[X \in A]=\mathbb{P}[Y \in A] $$.

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

- Set [0, 1] of all real numbers between 0 and 1 are *not countable*; proved by Georg Cantor using the diagonal argument.


# Discrete random variables  

Discrete - if random variable takes at most countably many values.

$$X$$ is said to be discrete if there exists finite or countable set $$S \subset \mathbb{R}$$ such that $$\mathbb{P}[X \in S]=1$$ (e.g, if we know with certainty that only values $$X$$ can take are those in $$S$$). 

The smallest set $$S$$ with this property is called *support* of $$X$$. Often written $$_{X}$$

