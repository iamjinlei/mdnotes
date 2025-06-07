<!---
nav:
    - Home=/
    - Statistics=/trading/statistics/note.md
left_pane: toc
--->

# 4 Probability Distributions

## Random Variables

- **Random variable** is a well-defined rule for assigning a numerical value to every possible outcome of an experiment.
- Typically, capital letters such as X, Y, and Z are used to denote random variables.
Lowercase letters such as x, y, z and a, b, c are used to denote particular values that the random variable can take on.
    - The expression p(X = x) symbolizes the probability that the random variable X takes on the particular value x.
Often written simply as p(x).
    - Likewise, p(X ≤ x) is the probability that the random variable X is less than or equal to the specific value x.
- If a random variable X can assume only a particular finite or countably infinite set of values, it is said to be a **discrete random variable**.
- **Discrete random variables** tend to be things you count, while **continuous random variables** tend to be things you measure.
- Probability distribution is a specification (in the form of a graph, a table or a function) of the probability associated with each value of a random variable.
    - Probability explains single events or a combinantino of events in an experiment.
    - Probability distribution explains all events in an experiment.

### Discrete Random Variables
- **Probability Mass Function (PMF)** describes the probability that a **discrete random variable** takes on a specific value.
It is specifically defined for discrete random variables.
    - same as p(X = x)
    - 0 ≤ p(X = x) ≤ 1
    - Σ p(X = x) = 1
- **Cumulative Distribution Function (CDF)** describes probability that a random variable X takes on a value less than or equal to some particular value a is often written as:
<img style="width:32%;display:block;margin:auto;" loading="lazy" src="imgs/4_cdf_discrete.png" alt="cdf_discrete">

### Continuous Random Variables
- In general, for continuous random variables, the occurrence of any exact value of X may be regarded as having 0 probability.
For this reason, one discuss the probability that X takes on some value a, the so-called **probability density** of X at a.
Denoted by **Probability Density Function (PDF)**.
    - 𝑓(a) = probability density of X at a
- The **Cumulative Distribution Function (CDF)** is written as:
<img style="width:55%;display:block;margin:auto;" loading="lazy" src="imgs/4_cdf_continuous.png" alt="cdf_continuous">
- The probability a continous random variable takes on any value between a and b:
    - p(a ≤ X ≤ b) = ∫𝑓(x)𝑑x for a ≤ x ≤ b
    - p(a ≤ X ≤ b) = 𝐹(b) - 𝐹(a)


## The Binomial Distribution

### Bernoulli Trial

Many experiments share the common element that their outcomes can be classified into one of two events, one can be labeled as "success" and the other as failure.
A **Bernoulli trial** is each repetition of an experiment involving only 2 outcomes:
- p = probability of success
- q = probability of failure = 1 - p
- p + q = 1

We are often interested in the result of **independent**, **repeated** Bernoulli trials, i.e. the number of successes in repeated trials.
- Independent: the result of one trial does not affect the result of another trial.
- Repeated: conditions are the same for each trial, i.e. p and q remain constant across trials.
    - This is also referred to as a <mark hl>stationary process</mark>.
    - If p and q can change from trial to trial, the process is <mark hl>nonstationary</mark>.
The term **identically distributed** is also often used.

### Binomial Distribution

A binomial distribution gives us the probabilities associated with independent, repeated Bernoulli trials.

<mark hl>A **binomial distribution** describes the probabilities of those of</mark>
- <mark hl>receiving a certain number of successes, **r**,</mark>
- <mark hl>in **N** independent trials, each having only 2 possible outcomes,</mark>
- <mark hl>with the same probability of success, **p**.</mark>

The probability of getting r successes in N independent trials with each having p success probability:

```
p(X = r; N, p) = number of ways event can occur * p(one occurrence)
               =  ɴCᵣ * pʳ * (1 - p)⁽ᴺ⁻ʳ⁾

ɴCᵣ reads as N choose r.
```

More formally, in sampling a **stationary** Bernoulli process, with the probability of success equal to p, the probability of observing exactly r successes in N independent trials is:

<img style="width:70%;display:block;margin:auto;" loading="lazy" src="imgs/4_binomial_dist_pdf.png" alt="binomial_dist_pdf">

Another way of defining binomial distribution:

- Random variable Xᵢ = 1 if the ith Bernoulli trial is successful, 0 otherwise.
- Random variable X = ∑Xᵢ is the number of successes, where the Xᵢ are independent and identically distributed (**iid**).
- p(X = r; N, p) is a binomial distribution with parameters N and p.

### Mean and Variance

```
Mean:
E(Xᵢ) = Σxᵢp(xᵢ) = 0 * (1 - p) + 1 * p = p
E(X) = E(X₁ + X₂ ... + Xɴ) = E(X₁) + E(X₂) + ...+ E(Xɴ) = Np

Variance:
xᵢ = xᵢ²
V(xᵢ) = E(xᵢ²) - E(xᵢ)² = p - p² = p(1 - p)
V(X) = V(X₁) + V(X₂) ... + V(Xɴ) = np(1 - p)
```

### Shape

- For small p and small N, the binomial distribution is what we call skewed right.
That is, the bulk of the probability falls in the smaller numbers, and the distribution tails off to the right.

<img style="width:45%;display:block;margin:auto;" loading="lazy" src="imgs/4_binomial_dist_shape_sp_sn.png" alt="binomial_dist_shape_small_p_small_n">

- For large p and small N, the binomial distribution is what we call skewed left.
That is, the bulk of the probability falls in the larger numbers and the distribution tails off to the left.

<img style="width:45%;display:block;margin:auto;" loading="lazy" src="imgs/4_binomial_dist_shape_lp_sn.png" alt="binomial_dist_shape_large_p_small_n">

- For p = 0.5 and large and small N, the binomial distribution is what we call symmetric.
That is, the distribution is without skewness.

<img style="width:45%;display:block;margin:auto;" loading="lazy" src="imgs/4_binomial_dist_shape_p50.png" alt="binomial_dist_shape_large_p50">

- When p ≠ 0.5, when N becomes large, the binomial distribution approaches symmetry.

<img style="width:45%;display:block;margin:auto;" loading="lazy" src="imgs/4_binomial_dist_shape_ln.png" alt="binomial_dist_shape_large_n">


### Examples

```
In a family of 11 children, what is the probability that there will be more boys than girls?
Solve this problem WITHOUT using the complements rule.

Solution:
p(boy) = 0.5
N = 11
p(more boys than girls) = p(6, N, p(boy)) + p(7, N, p(boy)) ... + p(11, N, p(boy))
                        = 0.2256 + 0.1611 + 0.0806 + 0.0269 + 0.0054 + 0.0005
                        = 0.5
```


## Normal Distribution

Characteristics of the normal distribution:

- Symmetric, bell shaped.
It describes data that clusters around a mean with symmetric spread.
- Continuous for all values of X between -∞ and ∞ so that each conceivable interval of real numbers has a probability other than zero.
- -∞ ≤ X ≤ ∞
- Two parameters, µ and σ. Note that the normal distribution is actually a family of
distributions, since µ and σ determine the shape of the distribution.
    - Mean (μ): controls the center
    - Standard deviation (σ): controls the spread

<img style="width:50%;display:block;margin:auto;" loading="lazy" src="imgs/4_normal_dist_pdf.png" alt="normal_dist_pdf">


- The notation N(µ, σ²) means normally distributed with mean µ and variance σ².
If we say X ∼ N(µ, σ²), we mean that X is distributed N(µ, σ²).
- About 2/3 of cases fall within 1 standard deviation of the mean, that is:
    ```
P(µ - σ ≤ X ≤ µ + σ) = 0.6826
    ```

- About 95% of cases fall within 2 standard deviations of the mean, that is
    ```
P(µ - 2σ ≤ X ≤ µ + 2σ) = 0.9544
    ```

<img style="width:60%;display:block;margin:auto;" loading="lazy" src="imgs/4_normal_dist_curve.png" alt="normal_dist_curve">

- Many things actually are normally distributed, or very close to it.
For example, height and intelligence are approximately normally distributed; measurement errors also often have a normal distribution.
- The normal distribution is easy to work with mathematically.
In many practical cases, the methods developed using normal theory work quite well even when the distribution is not normal.
- There is a very strong connection between the size of a sample N and the extent to which a sampling distribution approaches the normal form.
Many sampling distributions based on large N can be approximated by the normal distribution even though the population distribution itself is definitely not normal.


Examples:

- Heights of people
- Daily returns of large-cap stocks (often modeled as normal for simplicity)

Usage in time series:

- Assumption for returns: many models (ARIMA, Kalman filter, etc.) assume residuals/errors are normally distributed.
Even though crypto returns are not perfectly normal, log returns of large assets often approximate normal over short periods.
- Confidence intervals: if residuals are normal, we can compute forecast intervals: mean ± 1.96 x σ for 95% CI.
- Risk models: value-at-Risk (VaR) often assumes normal returns (or uses a fat-tailed correction).


### Binomial Distribution

The binomial distribution models the number of successes in a fixed number of independent yes/no (Bernoulli) trials.

Parameters:
- n: number of trials
- p: probability of success in each trial

Formula:
```
P(k successes in n trials) = C(n, k) * p^k * (1-p)^(n-k)
```

Examples:
- Number of times a coin lands heads in 10 flips
- Number of profitable trades in a batch of 100 trades













## 3. Poisson Distribution

What is it: The Poisson distribution models the number of times an event happens in a fixed interval of time or space when events occur independently at a constant average rate.

Parameter:
- lambda (λ): average rate of events per interval

Formula:
```
P(k events) = (λ^k * e^-λ) / k!
```

Examples:
- Number of trades per second on an exchange
- Number of server requests per minute

---

## 4. Uniform Distribution

What is it: The uniform distribution models a situation where all outcomes are equally likely.

Types:
- Discrete uniform: a finite number of equally likely outcomes
- Continuous uniform: all values in an interval [a, b] are equally likely

Formula (continuous):
```
f(x) = 1 / (b - a) for a <= x <= b
```

Examples:
- Random number generator between 0 and 1
- Picking a random time of day

---

## Summary

| Distribution | Typical Use Case |
|--------------|------------------|
| Normal       | Modeling natural phenomena, returns (approximate) |
| Binomial     | Number of successes in fixed trials |
| Poisson      | Number of events in a fixed interval |
| Uniform      | Equally likely outcomes |

---

