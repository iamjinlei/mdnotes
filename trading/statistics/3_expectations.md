<!---
nav:
    - Home=/
    - Statistics=/trading/statistics/note.md
left_pane: toc
--->

# 3 Expectations

## Mean

The mean is just the **average** value.
It tells you where the center of your data is.

For n numbers: x₁, x₂, ..., xₙ, the mean μ is:

    μ = (1/n) * Σxᵢ

The **expected value** of a random variable is the arithmetic mean of that variable, i.e. E(X) = µ.

- Discrete variable: the expected value of a discrete random variable, X, is found by multiplying each X value by its probability and then summing over all values of the random variable.

        E(X) = Σxᵢp(xᵢ) = µₓ

- Continuous variable: for a continuous variable X ranging over all the real numbers, the expectation is defined by integration.

        E(X) = ∫x𝑓(x)𝑑x = µₓ

## Variance

The variance tells you how **spread out** the data is — how far from the mean the values tend to be.

- Big variance: values are spread out.
- Small variance: values are clustered close to the mean.

The **variance** of a random variable X is defined as the expected squared deviation of the values of this random variable about their mean.

    V(X) = E((X - μ)²) = E(X²) - μ² = σ²

In the discrete case, this is equivalent to:

    V(X) =  Σ(xᵢ - μ)²p(xᵢ) = σ²

## Sample Mean and Variance

Sample is a subset of the whole population.
Sample mean is:

    x̄ = (1/n) * Σxᵢ    where xᵢ is a subset (size of n) of all possible x's

Sample variance:

    s² = (1/(n-1)) * Σ(xᵢ - x̄)²
       = (1/(n-1)) * E(Σ(xᵢ² - 2xᵢx̄ + x̄²))
       = (1/(n-1)) * E(Σxᵢ² - Σ2xᵢx̄ + Σx̄²)
       = (1/(n-1)) * E(Σxᵢ² - 2nx̄² + nx̄²)
       = (1/(n-1)) * (Σxᵢ² - nx̄²)    where xᵢ is a subset (size of n) of all possible x's


## <mark hl>Notation Clarifications</mark>
- Big X represents a random variable.
- Big Xᵢ represents a random variable whose process is "choose a random sample x₁, x₂, ..., xₙ of size n" from X.
    - Small xᵢ represents a single value from population that is collected in a sample x.
    - Small x̄ represents the mean of a particular sample, which can contain multiple values from the population.
- Big X̄ represents a random variable of means of those random samples Xᵢ.
    - It is an [estimator](1_definitions.md#key-concepts) of the population mean.
    - X̄ = (X₁ + X₂ + ... + Xₙ) / n
- Small s² represents a variance of a sample.
- Big S² represents the estimator, and small s² is a particular value of it.
- E(X) and V(X) meant for the whole population
    - Sample mean and sample variance only concern values from a sample.
    - E(X) and V(X) are for the whole population.
They do NOT use for sample.
        - E(Xᵢ) = E(X)
        - V(Xᵢ) = V(X)

Then we further have mean and variance for the mean estimator X̄:

    E(X̄) = E((X₁ + X₂ + ... + Xₙ) / n)
         = (E(X₁) + E(X₂) + ... + E(Xₙ)) / n
         = μ

    V(X̄) = V((X₁ + X₂ + ... + Xₙ) / n)
         = V(X₁ + X₂ + ... + Xₙ) / n²
         = (V(X₁) + V(X₂) + ... + V(Xₙ)) / n²     [Xᵢ are independent, check rule#15 below]
         = σ² / n

Proof for [why does sample variance have n - 1 in the denominator](3_expectations.md#why-does-sample-variance-have-n-1-in-the-denominator) is in the appendiex.

## Standard Deviation

The standard deviation is just the **square root of variance**.
It is in the **same units** as the original data, easier to interpret.

    StdDev(X) = sqrt(Variance) = σₓ

## Covariance

Covariance measures how **two variables move together**.

- If they both increase together, covariance is positive.
- If one increases while the other decreases, covariance is negative.
- If they are unrelated, covariance is close to zero.

For two variables X and Y:

    Cov(X, Y) = E((xᵢ - E(X)) * (yᵢ - E(Y)))

Intuition:

- If both X and Y are above or below their means at the same time, positive contribution.
- If one is above and the other is below, negative contribution.


## Correlation

Correlation is a **scaled version of covariance**, it removes the units and normalizes between -1 and +1.

- +1: perfect positive linear relationship
- -1: perfect negative linear relationship
- 0: no linear relationship

    Corr(X, Y) = Cov(X, Y) / (StdDev(X) * StdDev(Y))

## Autocorrelation

Autocorrelation (also called serial correlation) measures how a time series is correlated with a lagged version of itself.
In simple terms, does today's value depend on past values? If yes, autocorrelation exists.

- If autocorrelation exists, we can potentially predict future values based on past.
- If not, the series is more like random noise.

For time series Xₜ, lag k:

    Autocorrelation at lag k = Corr(Xₜ, Xₜ₋ₖ)

Interpretation

| Autocorrelation Value | Meaning |
|---|---|
| Close to +1 | Strong positive correlation, values repeat trend |
| Close to -1 | Strong negative correlation, values alternate up/down |
| Close to 0 | No correlation, no predictable pattern |


Autocorrelation Plot (ACF Plot)

- Shows autocorrelation at different lags.
- Helps identify patterns:
    - Trending series: slow decay of autocorrelation.
    - Mean-reverting series: negative autocorrelation at certain lags.
    - Random walk: no significant autocorrelation.

## Expectation Rules

Assume following, *a* and *b* are any given constants.
*X* and *Y* are random variables.

| # | Rule | Note |
|---|---|---|
| 1  | E(X) = Σxᵢp(xᵢ) = µₓ | discrete variable |
| 2  | E(g(X)) = Σg(xᵢ)p(xᵢ) = µ₉₍ₓ₎ | discrete variable, g(X) is some function of X |
| 3  | E(a) = a | the expectation of a constant is the constant |
| 4  | E(aX) = a * E(X) | multipling every value by 2, the expectation doubles |
| 5  | E(a ± X) = a ± E(X) | adding 7 to every case, the expectation will increase by 7 |
| 6  | E(a ± bX) = a ± bE(X) | |
| 7  | E((a ± X) * b) = (a ± E(X)) * b | |
| 8  | E(X + Y) = E(X) + E(Y) | |
| 9  | If X and Y are independent: E(XY) = E(X)E(Y) | |
| 10 | V(X) = E((X - μ)²) = E(X²) - E(X)² = E(X²) - μ² = σₓ² | |
| 11 | V(a) = 0 | a constant does not vary |
| 12 | V(a ± X) = V(X) | adding a constant to a variable does not change its variance |
| 13 | V(a ± bX) = b² * V(X) | |
| 14 | V(X ± Y) = V(X) + V(Y) ± 2COV(X,Y) | |
| 15 | If X and Y are independent, V(X ± Y) = V(X) + V(Y) | |
| 16 | Cov(X,Y) = E((X - E(X)) * (Y - E(Y)) = E(XY) - E(X)E(Y) | |
| 17 | If X and Y are independent, Cov(X,Y) = 0 | Cov(X,Y) = 0 does not necessarily mean X and Y are independent |

### Exercises

#### Exercise 1

    Prove V(X) = E((X - μ)²) = E(X²) - μ²

    Solution:
    V(X) = E((X - μ)²)
         = E(X² - 2Xμ + μ²)           [expand]
         = E(X²) - E(2Xμ) + E(μ²)     [rule#7]
         = E(X²) - 2μE(X) + μ²        [rule#7]
         = E(X²) - 2μ² + μ²
         = E(X²) - μ²

#### Exercise 2

    Prove V(aX) = a² * V(X)

    Solution:
    Let Y = aX
    V(Y) = E(Y²) - E(Y)²              [rule#10]
         = E(a²X²) - E(aX)²
         = a²E(X²) - a²E(X)²          [rule#4]
         = a²(E(X²) - E(X)²)
         = a²V(X)

#### Exercise 3

    Let Z = (X - µₓ)/σₓ, find E(Z) and V(Z)

    Solution:
    E(Z) = E((X - µₓ) / σₓ)
         = (E(X) - µₓ) / σₓ           [rule#7,rule#3]
         = 0
    V(Z) = V((X - µₓ) / σₓ)           [rule#13]
         = V(X) / σₓ²                 [rule#12]
         = 1

#### Exercise 4

    Finding the mean and variance for the number of heads obtained in 3 coin tosses.

    Solution:
    Let Xᵢ = 1 if the ith coin toss comes up heads, 0 otherwise.
    So Xᵢ² = Xᵢ (0² = 0, 1² = 1).

    E(X₁) = E(X₂) = E(X₃) = 0.5
    E(X₁ + X₂ + X₃) = E(X₁) + E(X₂) + E(X₃) = 1.5                [rule#8]
    V(X₁) = V(X₂) = V(X₃) = E(X²) - E(X)² = 0.5 - 0.25 = 0.25    [rule#10]
    V(X₁ + X₂ + X₃) = V(X₁) + V(X₂) + V(X₃) = 0.75               [rule#15]

## Summary

| Concept | Meaning |
|---|---|
| Mean | Average — where the data centers |
| Variance | How spread out the data is |
| Std Dev | Square root of variance — easier to interpret as "typical deviation" |
| Covariance | Measures how two variables move together (units depend on X and Y) |
| Correlation | Scaled covariance, unit-free, ranges [-1, +1], easy to interpret |
| Autocorrelation | How current value relates to past values. Detect trends, mean reversion, model building |

Why important in time series / trading?

- Mean return: is your asset trending up or down?
- Variance / Std Dev: how risky / volatile is this asset?
- Many trading signals depend on moving averages (mean) and volatility (variance)!
- In portfolio construction: want to select assets with low or negative correlation for diversification.
- In pairs trading: look for highly correlated or cointegrated pairs.
- In risk models: correlation matrix used to model portfolio risk.
- Trend following: positive autocorrelation (momentum).
- Mean reversion: negative autocorrelation.
- ARIMA models: built on autocorrelation patterns.
- Strategy testing: check if signals are statistically significant or just noise.

## Appendix

### Why Does Sample Variance Have n - 1 in the Denominator?

The reason we use n-1 rather than n is so that the sample variance will be an [unbiased estimator](1_definitions.md#key-concepts) of the population variance σ².
That is:

    The sample variance is the formula for a particular sample:
        s² = (1/(n-1)) * (Σxᵢ² - nx̄²)
    Now we define an estimator S² for s² by replacing variables by estimators:
        S² = (1/(n-1)) * (ΣXᵢ² - nX̄²)
    Xᵢ is an unbiased estimator for population X, thus xᵢ.
    X̄  is an unbiased estimator for mean of population X, thus x̄.

    Now need to prove S² is an unbiased estimator of the population variance σ², i.e. E(S²) = σ²

    Proof:
    (1) From population variance definition σ² = E(X²) - μ², we have E(X²) = σ² + μ²
    (2) E(Xᵢ²) = E(X²) = σ² + μ²
    (3) E(X̄²) = V(X̄) + E(X̄)²
              = σ² / n + μ²            [check Notation Clarifications section]

    then:
    E(S²) = E((1/(n-1)) * (ΣXᵢ² - nX̄²))
          = (1/(n-1)) * E(ΣXᵢ² - nX̄²)
          = (1/(n-1)) * (ΣE(Xᵢ²) - nE(X̄²))
          = (1/(n-1)) * (n(σ² + μ²) - n(σ² / n + μ²))
          = σ²
