---
layout: post
title: Extinction from a rationalist perspective, by C.R. Gallistel (Part I)
subtitle: An information-theoretic approach to extinction and contingency
tags: [extinction,information theory]
comments: true
---

The standard way to explain how the animals learn a new response is by appealing to an assotiation between events. In the pavlovian case, an animal associates two events arranged to occur with some frecuency together and with some delay between them. 

Gallistel starts with a important question in the associative theories of learning: What gets associated with what? I think this is an important question because, regardless how obvious is to say that what gets associated _cannot be_ the events per se (there is not a magic and cosmic glue between them after they have ocurred with some frequency) this seems to be not stressed enough, and one can forget the important question that is the cornerstone of the supposed mechanism: if something gets associated with something else, what is that, at what level, and what is the nature of that association? 

Of course, there are responses to this: the representations of the events gets associated. But again: what are those representations? How the events become represented by means of being experienced, and how those representations works in, say, the absense of the events? 

# Information-theoretic measure of contingency

Gallistel look problematic the reliance of operant theorizing on contingency without a proper and general measure of contingency. Some operant theorists (e.g., Baum, 1973) defines the contingency as the correlation between the output of a system and it's feedback. But, as Gallistel argue, correlation is a measure of linear dependence. Indeed, the Pearson correlation coefficient $\rho$ is just the cosine of the angle $\theta$ between two vectors $x,y$.

Thus, Gallistel continues, a more general measure of contingency, not constrained to linear dependence, is badly needed. And such a measure is the mutal information between two random variables, defined as $I(X;Y)$

$$ I(X;Y) = H(X) - H(X \mid Y) $$

On which $H(\cdot)$ is the _entropy_ of the random variable $X$, that can be computed as:

$$H(X) = \sum^{p(X)>0}p(X)\log(\frac{1}{p(X)})$$

# References

Baum, W. M. (1973). THE CORRELATION‐BASED LAW OF EFFECT. _Journal of the Experimental Analysis of Behavior_, 20(1), 137-153.
