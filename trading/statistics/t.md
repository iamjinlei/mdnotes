
# Distributions - Study Notes

## 1. Normal Distribution

What is it: The normal distribution is the famous bell curve. It describes data that clusters around a mean with symmetric spread.

Shape: Bell-shaped, symmetric.

Parameters:
- Mean (mu): controls the center
- Standard deviation (sigma): controls the spread

Formula:
```
f(x) = (1 / (sigma * sqrt(2 * pi))) * exp( - (x - mu)^2 / (2 * sigma^2) )
```

Examples:
- Heights of people
- Daily returns of large-cap stocks (often modeled as normal for simplicity)

---

## 2. Binomial Distribution

What is it: The binomial distribution models the number of successes in a fixed number of independent yes/no (Bernoulli) trials.

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

---

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

