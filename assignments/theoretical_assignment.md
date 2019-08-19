<h1 align='middle'>Deep|Bayes 2019</h1>
<h2 align='middle'>Theoretical Assignment</h2>
<p align='right'>Shubham Gupta<\p>
<p align='right'><a href="mailto:shubhamgblr@gmail.com">shubhamgblr@gmail.com</a></p>

## Q1
The random variable ξ has Poisson distribution with the parameter λ. If ξ = k we perform k Bernoulli trials with the probability of success p. Let us define the random variable η as the number of successful outcomes of Bernoulli trials. Prove that η has Poisson distribution with the parameter pλ.

**Answer**

We know,

$$\xi = Poisson(\lambda)$$

A poisson distribution for k events in an interval is given by:
$$P(\text{k events in an interval}) = \frac{e^{-\lambda}\lambda^k}{k!}$$

For a bernoulli trail, the conditional probability distribution  of obtaining `x` successes in `k` trails and success probability `p` is given by:

$$P(\eta=k|\xi=x) = \binom{k}{x}p^x(1-p)^{k-x}$$

We need to find the marginal probability of $P(\eta = x)$. We know the formula for marginal probability is given by:

$$P(\eta= x) = \sum_{k \geq x}P(\eta=x|\xi = k)P(\xi=k)$$

Substituting the values, we get:
$$P(\eta= x) = \sum_{k \geq x}\binom{k}{x}p^x(1-p)^{k-x}\frac{e^{-\lambda}\lambda^k}{k!}$$
$$= \sum_{k \geq x}\frac{k!}{x!(k-x)!}\binom{k}{x}p^x(1-p)^{k-x}\frac{e^{-\lambda}\lambda^k}{k!}$$

Removing the constants out and cancelling the common factor $k!$ , we get:
$$P(\eta= x) = \frac{p^xe^{-\lambda}}{x!}\sum_{k \geq x}\frac{(1-p)^{k-x}\lambda^k}{(k-x)!}$$

Let us substitute $$z = k-x$$. We get

$$P(\eta= x) = \frac{p^xe^{-\lambda}}{x!}\sum_{z \geq 0}\frac{(1-p)^z\lambda^{z+x}}{z!}$$
$$=\frac{(p\lambda)^xe^{-\lambda}}{x!}\sum_{z \geq 0}\frac{((1-p)\lambda)^z}{z!}$$
$$=\frac{(p\lambda)^xe^{-\lambda}}{x!} e^{\lambda(1-p)}$$
$$=\frac{(p\lambda)^xe^{-p \lambda}}{x!}$$
$$=Poisson(p \lambda)$$

Hence, $$\eta$$ has a Poisson distribution with parameter $$p \lambda$$.

---

## Q2
A strict reviewer needs t1 minutes to check assigned application to DeepBayes
summer school, where t1 has normal distribution with parameters µ1 = 30, σ1 = 10. While a kind reviewer needs t2 minutes to check an application, where t2 has normal distribution with parameters µ2 = 20, σ2 = 5. For each application the reviewer is randomly selected with 0.5 probability. Given that the time of review t = 10, calculate the conditional probability that the application was checked by a kind reviewer. 

**Answer**

We are given the following:

$$t1 = N(30, 10)$$
$$t2 = N(20,5)$$
$$P(t1) = P(t2) = 0.5$$

Using Bayes theorm, we get:

$$P(r=kind|t=10) = \frac{P(t=10|r=kind) P(r=kind)}{P(t=10)}$$

We can subsitute the denominator with the actual value i.e

$$P(r=kind|t=10) = \frac{P(t=10|r=kind) P(r=kind)}{P(r=kind|t=10) P(r=kind) + P(r=strict|t=10) P(r=strict)}$$

Now, for normal distributions, we know the probability mass function at any given point $x$ is given by:

$$P(x|\mu, \sigma^2)= \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$

Substituting the above formula, we get:

$$P(r=kind|t=10) = \frac{\frac{1}{\sqrt{2\pi\sigma^2_{kind}}}e^{-\frac{\big(t-\mu_{kind}\big)^2}{2\sigma^2_{kind}}} * 0.5}{0.5*\bigg(\frac{1}{\sqrt{2\pi\sigma^2_{kind}}}e^{-\frac{\big(t-\mu_{kind}\big)^2}{2\sigma^2_{kind}}}+\frac{1}{\sqrt{2\pi\sigma^2_{strict}}}e^{-\frac{\big(t-\mu_{strict}\big)^2}{2\sigma^2_{strict}}}\bigg)}$$


Now, $$e^{-\frac{\big(t-\mu_{kind}\big)^2}{2\sigma^2_{kind}}}$$ =  $$e^{-\frac{\big(t-\mu_{strict}\big)^2}{2\sigma^2_{strict}}}$$ = $$2$$,  when we substitute the values. Furthermore, we can cancel our the common values of 0.5 and $$\frac{1}{\sqrt{2\pi}}$$. Therefore, we get:

$$= \frac{\frac{1}{5}}{\frac{1}{5} + \frac{1}{10}}$$
$$~= \frac{2}{3}$$

Hence, the probability of the reviewer being kind at $$t=10$$ is $$\frac{2}{3}$$.

---
