---
title: "Poisson Distribution"
categories:
  - blogging
toc: false
tags: [Basic Probability]
---  


Before we talk about the Poisson distribution, let's think of a probability of how many people are coming to a 24/7 convenience store in an hour. To make things simple, we assume that the probability does not change over time. That is, the probability at 1 pm and 3 am is the same. We can write out the probability using a binomial distribution:
$$
P(X=k) = \binom{N}{k}p^k(1-p)^{n-k} \tag{1}. 
$$
The expected value of a binomial distribution is:
$$
E[X] = np = \lambda,
$$
so we can write $(1)$ with its mean $\lambda$:
$$
P(X=k) = \binom{N}{k}\left(\frac{\lambda}{n}\right)^k\left(1-\frac{\lambda}{n}\right)^{n-k}. \tag{2}
$$
First, let us count people entering the store at each minute. Then $n$ will be $60$. But how can we be sure that two or more people coming inside the store in a minute? I think one minute is too long to make sure that there is only one person who comes inside the store. Let's count whether a person enters at every second. Now $n$ is going to be $3600$. Unfortunately, it could be a reasonable interval, but we cannot still be sure about the previously mentioned problem.  

A Poisson distribution comes out of this problem. In this particular distribution, $n$ is going to be $\infty$. That is, we are going to count whether a person enters a store in an interval of $\lim_{n\to\infty} \frac{1}{n}$. Now let's derive the Poisson distribution from $(2)$.
$$
\begin{aligned}
  P(X=k) &= \lim_{n\to\infty} \binom{N}{k} \left(\frac{\lambda}{n} \right)^k \left(1-\frac{\lambda}{n}\right)^{n-k} \\
  &=\lim_{n\to\infty}\frac{n!}{(n-k)!k!} \left(\frac{\lambda}{n} \right)^k \left(1-\frac{\lambda}{n}\right)^{n}\left(1-\frac{\lambda}{n}\right)^{-k} \\
  &=\lim_{n\to\infty} \underbrace{\frac{n(n-1)\cdots(n-k+1)}{n^k}}_{\to 1}\underbrace{\frac{\lambda^k}{k!}}_{\text{const.}} \underbrace{\left(1-\frac{\lambda}{n}\right)^n}_{\to e^{-\lambda}} \underbrace{\left(1-\frac{\lambda}{n}\right)^{-k}}_{\to 1} \\
  &= \frac{\lambda^k}{k!} e^{-\lambda}.
\end{aligned}
$$

If we know that 10 people visit the store in an hour, we can get a probability that 20 people visit the store in an hour by setting $\lambda=10$ and $k=20$:
$$
P(X=20;\lambda=10) = \frac{10^{20}}{20!}e^{-20} = 0.00186608 \approx 0.19 \%.
$$
