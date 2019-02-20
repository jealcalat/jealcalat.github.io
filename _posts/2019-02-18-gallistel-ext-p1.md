---
layout: post
title: Extinction from a rationalist perspective, by C.R. Gallistel (Part I)
subtitle: An information-theoretic approach to extinction and contingency
tags: [extinction,information theory]
comments: true
---
# Associative theory of learning

The standard way to explain how the animals learn a new response is by appealing to an assotiation between events. In the pavlovian case, an animal associates two events arranged to occur with some frecuency together and with some delay between them. 

Gallistel starts with a important question in the associative theories of learning: What gets associated with what? I think this is an important question because, regardless how obvious is to say that what gets associated _cannot be_ the events per se (there is not a magic and cosmic glue between them after they have ocurred with some frequency) this seems to be not stressed enough, and one can forget the important question that is the cornerstone of the supposed mechanism: if something gets associated with something else, what is that, at what level, and what is the nature of that association? 

Of course, there is an answer for this: is the representations of the events what gets associated (see Gallistel 2007). But again: what are those representations? How the events become represented by means of being experienced, and how those representations works in, say, the absense of the events? 

# Information-theoretic measure of contingency

Gallistel look problematic the reliance of operant theorizing on contingency without a proper and general measure of contingency. Some operant theorists (e.g., Baum, 1973) defines the contingency as the correlation between the output of a system and it's feedback. But, as Gallistel argue, correlation is a measure of linear dependence. Indeed, the Pearson correlation coefficient $\rho$ is just the cosine of the angle $\theta$ between two vectors $\mathbf{x},\mathbf{y}$.

Thus, Gallistel continues, a more general measure of contingency, not constrained to linear dependence, is badly needed. And such a measure is the mutal information between two random variables, defined as $I(X;Y)$

$$ I(X;Y) = H(X) + H(Y) - H(X,Y) $$

In words, the equation for mutual information says that the mutual information between $X$ and $Y$ is the sum of their individual entropy (or information) minus the entropy of their joint distribution. $H(\cdot)$ is the _entropy_ of a random variable $X$ (with $x_i$ realizations of it) or it's joint distribution, that can be computed as:

$$H(X) = \sum_{i}p(x_i)\log\Bigg(\frac{1}{p(x_i)}\Bigg)$$

With $p(x_i)$$^[1]$ as the relative frequency of the $i$-th $x$, and $\log$ is the logarithm base 2 (so information is measured in bits). For example, if $X$ is the result of a coin toss (a Bernoulli trial), then the total information we can have is, with equal probability of the coin comming up heads and tails,

$$H(X) = p(Heads)\log\Bigg(\frac{1}{p(Heads)}\Bigg) + p(Tails)\log\Bigg(\frac{1}{p(Tails)}\Bigg)$$
$$H(X) = \frac{1}{2}\log(2) + \frac{1}{2}\log(2) = \log(2)=1 $$

(this post is still in process...)

# Footnotes

[1] This notation is shorthand for $p(X = x_i)$, the probability that the random variable $X$ takes value $x_i$

# References

Baum, W. M. (1973). THE CORRELATION‐BASED LAW OF EFFECT. _Journal of the Experimental Analysis of Behavior_, 20(1), 137-153.

Gallistel, C. R. (2007). Flawed foundations of associationism? Comment on Machado and Silva (2007). _The American psychologist_. 62(7), 682–685.
